# blender-ai-copilot-flow

**A controlled AI workflow for Blender: every copilot edit is a supervised tool call—proposed, approved, executed in sequence, cancellable after the current step and undoable by name—inside a visual studio with a built-in MCP server.**

[download-url]: https://github.com/tiobeharxi1987/blender-ai-copilot-flow/releases

[![License](https://img.shields.io/badge/license-MIT-blue)] ![Language](https://img.shields.io/badge/language-Python-3776AB?logo=python&logoColor=white) ![Platform](https://img.shields.io/badge/platform-Windows%20x64-0078D6?logo=windows&logoColor=white) ![Blender](https://img.shields.io/badge/Blender-4.2%2B-E87D0D?logo=blender&logoColor=white) ![MCP](https://img.shields.io/badge/Model_Context_Protocol-MCP-5E5CE6) ![Release](https://img.shields.io/badge/release-1.0.2-98D85B) ![Edits](https://img.shields.io/badge/edits-approved%20%7C%20undoable-10B981)

[**Download**][download-url]

Nothing lands unseen: every edit is proposed, approved, run in order, and reversible by name.

## Why

The scary part of AI in a production scene is not what it builds—it is what it might change while you blink. blender-ai-copilot-flow makes every copilot action a visible step in a controlled flow: proposed before execution, approved by you, applied in sequence with earlier steps finished first, cancellable after the current operation, and undoable through named undo steps. Tool calls are validated against the allowed set before they run. You get the speed of an AI copilot with the audit trail of a pipeline.

## Without / With

| Without | With |
|---|---|
| Fear of a wrecked scene | Nothing runs without your approval |
| Mystery diffs you discover later | Each operation named and proposed before it executes |
| Parallel edits colliding mid-brief | Sequential execution—one ordered flow |
| No way back after a bad run | Named undo steps for every mutation |
| Runaway multi-step plans | Cancel halts the workflow after the current step |
| "Is this call even allowed?" | Python tool validation catches disallowed operations |

## Quick Start

Every command below is self-contained: open PowerShell, copy it, paste it, press Enter.

1. Grab the release ZIP `blender-ai-copilot-flow.zip` from [Download][download-url] and save it to your Windows machine.
2. Verify the installed Blender build on a standard Windows setup, then in Blender open **Edit → Preferences → Get Extensions → the ⋮ menu → Install from Disk**.
   `powershell Get-ChildItem $env:ProgramFiles\Blender*\Blender*\blender.exe`
3. Pick the ZIP in the installer, enable **blender-ai-copilot-flow**, and open the sidebar **3D Viewport → N → Copilot Flow**; the command opens your Downloads folder first.
   `powershell Invoke-Item $env:USERPROFILE\Downloads`
4. Choose a provider—OpenAI, Anthropic Claude, Google Gemini, OpenRouter, OpenCode Zen, Ollama or a custom API—add your connection details and select a tool-calling model; the command checks a local Ollama server when that is your provider.
   `powershell Invoke-RestMethod http://localhost:11434/api/tags`
5. Send a message in Blender or click **Open Studio Window** and watch each step ask before it runs; the command confirms Blender is running.
   `powershell Get-Process blender`
6. Runtime profile: Windows x64 with Blender 4.2 or later, Blender kept open while Studio or an external client is in use; when the built-in MCP server is enabled, the command confirms its local endpoint.
   `powershell Test-NetConnection 127.0.0.1 -Port 9876`

## Features

- Approve every operation—each tool call is proposed before it runs.
- Cancel safely—Stop halts the workflow after the current step, mid-plan.
- Undo by name—mutations leave named undo steps you can pick from Blender's own controls.
- Run edits in sequence—ordered steps, no collisions between operations.
- Validate tool calls—disallowed operations are caught before execution.
- Watch each step—viewport snapshots confirm what actually changed.
- Serve the flow to MCP clients—external calls meet the same supervised pipeline.

## How it works

blender-ai-copilot-flow runs inside Blender as an extension: the copilot inspects your scene through 27 supervised tools, proposes each brief as a sequence of named operations, and executes them in order with your approval, a safe cancel and named undo per mutation. Python tool validation checks each call against the allowed set before it runs—it catches disallowed operations, though it is not a security sandbox—and the same supervised flow is exposed to external clients through a local authenticated endpoint (`http://127.0.0.1:9876/mcp`).

## Usage

**A careful production pass.** "Add the three lights and the camera, one step at a time—show me each before the next." Approve, watch, continue; cancel anywhere after the current step.

**A reversible experiment.** Let the copilot rearrange a whole section; every mutation leaves a named undo step, so one pick takes the scene back to the mark you named.

**Supervised scripting.** When a brief needs `execute_code`, the snippet is proposed, validated and approved like any other step—no silent scripts.

## Configuration

| Setting | Default | What it does |
|---|---|---|
| Approvals | Per operation | Every tool call is proposed before execution |
| Cancellation | After current step | Stop finishes the running operation and halts the plan |
| Named undo | Every mutation | Each edit leaves a named undo step |
| Execution order | Sequential | Steps run one after another so edits stay ordered |
| Tool validation | Enabled | Disallowed operations are caught before they run |
| Workflow mode | Single assistant | Plain chat or a Team chain with the same controls |
| Provider | OpenAI | OpenAI, Anthropic Claude, Google Gemini, OpenRouter, OpenCode Zen, Ollama or Custom API |
| MCP endpoint | `http://127.0.0.1:9876/mcp` | Local Streamable HTTP endpoint for external MCP clients |
| Interface language | English | English, German, French, Spanish or Chinese |
| Asset services | Optional keys | Service keys for asset providers that require them |

## Troubleshooting / FAQ

**The copilot stopped mid-brief.** Stop ends after the current step by design—approve the next step to continue, or check the last proposal for a question it asked.

**How is this different from Blender's undo?** Named undo steps are created per copilot mutation, so you can jump back to a specific named point instead of counting Ctrl+Z presses.

**Can I skip approvals for trusted steps?** Approvals are the core of the flow—but quick, low-risk edits can be approved in rapid succession.

**Is validation a security sandbox?** No—it catches disallowed operations before they run; treat it as a seatbelt, not a firewall.

**Do external MCP clients follow the same rules?** They manage their own approval policies; Blender-side visibility and undo still apply to every call.

## Contributing

Found a step that should be gated differently? Open an issue with the brief and the operation in question, or send a pull request. If blender-ai-copilot-flow keeps your scenes safe, a star helps others find it.

## Keywords

blender-ai-copilot-flow · blender · blender 3d · blender addon · blender plugin · blender extension · blender scripting · blender automation · blender mcp · blender ai · blender assistant · blender copilot · blender chatgpt · blender llm · blender agents · bpy · 3d modeling · 3d automation · mcp · mcp server · model context protocol · ai for blender · operation approvals · named undo · undo steps · cancellation · safe cancel · sequential execution · ordered steps · tool validation · supervised tools · scene tools · scene inspection · scene generation · ai modeling · ai materials · viewport screenshot · studio workspace · task board · agent teams · multi agent · product visualization · geometry nodes · 3d workflow · 3d rendering · windows 3d · ai 3d · ollama · openai · anthropic claude · google gemini · openrouter · opencode zen · model catalog · connection profiles · custom api

## License

Released under the [MIT](./LICENSE) license.
