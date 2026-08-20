<h1 align="center">Rhishi</h1>

<p align="center">
  <em>I build tooling for AI coding agents — and trading systems that use it.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white" alt="Rust">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React">
  <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white" alt="AWS">
  <img src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white" alt="Terraform">
</p>

---

## What I work on

**Agent infrastructure.** The unglamorous layer underneath AI coding tools — headless bridges, model routers, context management, voice I/O. Most of it exists because I hit the bug myself and no fix was coming.

**Trading intelligence.** Equity scanners, backtesting engines and alerting pipelines for Indian markets (NSE/BSE), built on FastAPI and React and deployed on AWS.

**Developer tooling.** Small, sharp utilities that remove a specific friction and then get out of the way.

---

## Open source contributions

### [rtk-ai/rtk](https://github.com/rtk-ai/rtk) — Rust Token Killer

RTK is a Rust CLI proxy that cuts LLM token consumption by 60–90% on everyday dev commands. It was effectively unusable on Windows: core commands failed on a stock install, the agent hook silently died on malformed input, and the entire integration test suite was gated off.

I audited the Windows surface and submitted **11 focused pull requests**, each independently mergeable:

| PR | Fix |
|---|---|
| [#3613](https://github.com/rtk-ai/rtk/pull/3613) | MinGW linker got MSVC's `/STACK:` flag — no GNU-toolchain build could link |
| [#3614](https://github.com/rtk-ai/rtk/pull/3614) | Setup warning leaked into the hook protocol channel, breaking 10 of the project's own tests |
| [#3615](https://github.com/rtk-ai/rtk/pull/3615) | Test asserted `U+FFFD` where a console code page legitimately decodes a real character |
| [#3616](https://github.com/rtk-ai/rtk/pull/3616) | Native Rust `ls`, `tree` and `wc` — Windows ships none of the GNU binaries these proxied to |
| [#3617](https://github.com/rtk-ai/rtk/pull/3617) | Path helpers split on `/` only, so Windows paths passed through unnormalized |
| [#3618](https://github.com/rtk-ai/rtk/pull/3618) | Shell hardcoded to `cmd /C`, so every PowerShell cmdlet handed to it failed |
| [#3619](https://github.com/rtk-ai/rtk/pull/3619) | BOM-prefixed hook input, `rtk.exe` name matching, unwritable audit log path |
| [#3620](https://github.com/rtk-ai/rtk/pull/3620) | Classification rules for PowerShell cmdlets and their aliases |
| [#3621](https://github.com/rtk-ai/rtk/pull/3621) | Opt-in quiet mode — diagnostics on stderr cost agents more tokens than the filter saves |
| [#3622](https://github.com/rtk-ai/rtk/pull/3622) | Un-gated the integration suite on Windows: **70 tests that never ran now do** |
| [#3623](https://github.com/rtk-ai/rtk/pull/3623) | `install.ps1` plus winget / Scoop / Chocolatey publishing |

Several of these fix bugs that were invisible in CI — green on a fresh runner, broken on a real developer's machine.

---

## Selected projects

### [agy-headless-bridge](https://github.com/rhishi99/agy-headless-bridge) &nbsp;·&nbsp; ⭐ 15

Google's Antigravity CLI returns empty output when called from any non-TTY context — subprocess, MCP server, CI. This gives it a real pseudo-terminal on both Windows (ConPTY) and POSIX, so headless callers get their output. Published on PyPI and listed in the MCP registry.

`Python` · `ConPTY` · `MCP`

### [OutLoud](https://github.com/rhishi99/OutLoud)

Local text-to-speech for Claude Code and Grok. Narrates agent output through edge-tts with a native SAPI fallback, costing zero extra LLM tokens.

`Python` · `Node.js` · `edge-tts`

### [hermes-model-auto-switch](https://github.com/rhishi99/hermes-model-auto-switch)

Auto-switching LLM router: health-checks NVIDIA NIM endpoints, routes by capability, and learns from outcomes rather than a static config.

`Python` · `pytest` · `CI`

### [ComboCoder](https://github.com/rhishi99/ComboCoder)

A local four-agent pair programmer — plan, architect, engineer, review — running entirely on free-tier models.

`Python` · `LangGraph` · `LiteLLM`

### [agent-memory-context](https://github.com/rhishi99/agent-memory-context)

One-shot tooling for the problems that make long agent sessions degrade: context rot, memory loss, token waste, and long-horizon planning.

---

## Also, privately

A number of larger systems live in private repositories — among them an NSE/BSE trading dashboard with weekly scans, strategy scoring and backtests running on AWS behind CloudFront; a multilingual commodity-price and arbitrage app for Indian mandi traders, with an Android build; and an agentic pipeline that turns a script into a finished tutorial video end to end.

Happy to walk through any of them.

---

<p align="center">
  <sub>Everything here is built and maintained by one person, with AI assistance where it earns its keep.</sub>
</p>
