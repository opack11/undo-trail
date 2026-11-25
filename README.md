# Undo Trail

*README prose word count: about 541 (excluding headings, code and commands)*

A clickable walkthrough prototype that helps a person decide what to undo after an AI agent has completed a multi-step task and made a mistake. Built for Assignment 2 of Intelligent Interactive Systems (University of Birmingham).

## Project status

- **Works:** a five-scene walkthrough (request, agent report, problem noticed, recover, outcome). The recovery scene has two views you can switch between:
  - **Labelled trace** (the design): reversibility labels, consequences, dependency warnings and highlighting, explanations, undo preview with a "will not fix" list, acknowledgement after undo, and an agent-drafted correction the person edits and sends.
  - **Standard log** (comparison condition): raw commands with "Undo last" and "Undo all".
- **Simulated:** the agent, its six actions, the files, the email and the calendar are scripted in the page. No AI model runs and nothing outside the page changes.
- **Not built:** a real agent and tool layer, memory of corrections, and a user study.

## Technology stack

- One HTML file with plain JavaScript and CSS. No framework, build step, server or API key.
- No AI model is used at run time. Choosing a model and tool framework for a real agent is still undecided.
- Playwright with headless Chrome was used during development to click through the prototype and capture the report's screenshots; it is not needed to run the prototype.

## Running or inspecting the work

Download `index.html` and open it in any modern browser. Use the scene buttons at the top, or **Next** and **Back**. In scene 4, switch between **Standard log** and **Labelled trace**.

The script of agent actions is the `ACTIONS` list near the top of the `<script>` section; each entry has its reversibility, consequence, dependency and reason.

`docs/img/` holds the system diagram and storyboards used in the report.

## Development record

- **v1: core comparison.** Built the scripted agent, the standard log and the labelled trace with preview and correction draft, from the design proposed in Assignment 1. Checked by clicking through every scene in a headless browser: no script errors. Fixed two bugs found this way: the preview lower-cased file names, and the outcome screen said correct work was kept even after "Undo all" had reversed it.
- **v2: verifying and recovering.** Added the action record under the agent's "Done" message, so its summary can be checked against what the tools did; an immediate acknowledgement after each undo with "undone by you" attribution; and "Show steps that relied on this" highlighting, so the dependency chain does not have to be remembered. Checked with the same click-through; fixed the acknowledgement's wording for several steps.
- **Next (planned):** a small within-subjects study comparing the two recovery views.

## AI assistance

- **Tool:** Claude.
- I used Claude to generate and test the prototype code, produce the figures from its screenshots.

## Additional files

- `docs/img/system-diagram.png`: components and flows, marked implemented, simulated or planned.
- `docs/img/storyboard1.png` to `storyboard3.png`: illustrated interactions made from screenshots of the prototype.
