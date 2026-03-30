# UX Agent Hub

An interactive command center for UX designers on e-conomic. Deploy AI agents across your workflow pipeline — from discovery research through validated solution delivery — with one click.

## What it does

The hub gives you **8 specialised AI agents**, each handling a step in the UX workflow:

| # | Agent | What it does |
|---|-------|-------------|
| 01 | **Discovery Agent** | Creates discovery items in the All Discovery backlog. Pick a JTBD, describe your research question, and get a full research brief with suggested questions, participant segmentation, and method recommendation. |
| 02 | **Opportunity Agent** | Evaluates interview transcripts and research notes against the JTBD framework and missions. Creates opportunities in the All Opportunities collection with auto-linking to related discovery items. |
| 03 | **Pitch Agent** | Reads a validated opportunity from Slite and generates a pitch using Pitch Template v3.0. Saves to the Pitches collection with status, owner, and sizing. |
| 04 | **Brief Agent** | Traces a pitch back to its opportunity and generates a Design Brief 2.1 — scoping the problem, mapping the journey, and preparing LLM context for design generation. |
| 05 | **Design Agent** | Uses a completed design brief + the Adesy Web Components design system to generate solution proposals with component mappings, tokens, and layout rules. |
| 06 | **Validation Agent** | Structures customer validation — test plans, participant criteria, feedback templates — for usability tests, concept tests, or preference tests. |
| 07 | **Iteration Agent** | Feeds validation learnings back into the design brief and triggers refined solution generation. |
| 08 | **Solution Agent** | Packages the validated solution into a delivery-ready spec with interaction states, component mappings, and evidence summaries. |

## How it works

1. Open the hub in your browser
2. Select an agent from the left sidebar
3. Fill in the required inputs (transcript, Slite link, etc.)
4. Click **Deploy** — a Claude window opens with the agent prompt pre-loaded
5. Hit send in Claude — the agent executes using Slite MCP to read/write your collections

The right-hand panel shows all 11 Jobs to Be Done and 4 strategic missions for quick reference while working.

## Requirements

- A **Claude** account (Pro, Team, or Enterprise) at [claude.ai](https://claude.ai)
- **Slite MCP** connected to your Claude workspace (for reading/writing to collections)
- Access to the e-conomic Slite workspace

## Slite collections used

| Collection | Slite ID | Purpose |
|-----------|----------|---------|
| All Discovery | `MFcG0JEQAzh2cI` | Discovery backlog with research questions |
| All Opportunities | `0CBSdHnBH530nI` | Validated opportunity backlog |
| Pitches | `DeH9uCJqXm1bvn` | Delivery pitches for review |

## Setup

### Option A: Open directly
Just open `index.html` in your browser. No server needed.

### Option B: GitHub Pages (recommended for team use)
1. Push this repo to GitHub
2. Go to **Settings → Pages → Source → main branch**
3. Your hub is live at `https://your-org.github.io/ux-agent-hub/`
4. Share the URL with your team

## Customisation

The hub is a single HTML file with no dependencies. All data (JTBD, missions, Slite IDs, agent prompts) lives in the `<script>` section. To modify:

- **Add/edit JTBD**: Update the `jobs` array (~line 202)
- **Add/edit missions**: Update the `missions` array (~line 226)
- **Change agent prompts**: Edit the `run*()` functions (~line 640+)
- **Add new agents**: Add to the `agents` array and create a matching `inputType` case in `getInputHTML()` and a `run*()` function

## Tech stack

None. It's a single HTML file with vanilla JS and CSS. No build step, no npm, no framework.
