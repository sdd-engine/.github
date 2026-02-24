<p align="center">
  <img src="https://raw.githubusercontent.com/sdd-engine/sdd-core/main/docs/logo.svg" alt="SDD Logo" width="120" />
</p>

<h1 align="center">Spec-Driven Development</h1>

<p align="center">
  <strong>Stop prompting. Start shipping.</strong><br/>
  A structured methodology for AI-assisted development — built for <a href="https://docs.anthropic.com/en/docs/claude-code">Claude Code</a>.
</p>

---

AI coding assistants are powerful but chaotic. You prompt, you get code — but nobody documented the decisions, nothing verifies the code matches what you actually needed, and good luck explaining any of it to your team next week.

**SDD fixes this.** Every change starts with a spec, gets broken into a plan, and ends with verified implementation. Specialized agents handle each concern instead of one AI trying to do everything at once.

### The workflow

```
/sdd I want to create a new feature       →  Write a spec with acceptance criteria
/sdd I want to approve the spec            →  Review and lock the spec, generate a plan
/sdd I want to approve the plan            →  Lock the plan, enable implementation
/sdd I want to start implementing          →  Agents execute each phase
/sdd I want to verify the implementation   →  Verify code matches the spec
```

### The architecture

**Core + Tech Packs.** SDD separates *methodology* from *technology*. The core plugin owns the lifecycle — specs, plans, phases, verification. It doesn't know anything about your stack. That's the tech pack's job.

A tech pack brings the domain expertise: specialized agents that know how to write code in your stack, templates for scaffolding components, and tooling for stack-specific operations. Swap the tech pack, keep the workflow.

<table>
  <tr>
    <td><strong><a href="https://github.com/sdd-engine/sdd-core">sdd-core</a></strong></td>
    <td>The engine. Commands, skills, orchestrators, settings, and system CLI. Install this first.</td>
  </tr>
  <tr>
    <td><strong><a href="https://github.com/sdd-engine/sdd-fullstack-typescript-techpack">sdd-fullstack-typescript-techpack</a></strong></td>
    <td>Full-stack TypeScript tech pack. 7 specialized agents for Node.js, React, PostgreSQL, Kubernetes, and more.</td>
  </tr>
  <tr>
    <td><strong><a href="https://github.com/sdd-engine/sdd-vscode-extension">sdd-vscode-extension</a></strong></td>
    <td>VS Code extension. Ambient workflow visualization — see phases, approvals, and progress without leaving the editor.</td>
  </tr>
</table>

### Tech packs up close

The [fullstack TypeScript tech pack](https://github.com/sdd-engine/sdd-fullstack-typescript-techpack) ships 7 specialized agents — each scoped to a single concern:

| Agent | What it does |
|-------|-------------|
| **api-designer** | Designs OpenAPI contracts from spec requirements |
| **backend-dev** | Builds Node.js services with CMDO architecture |
| **frontend-dev** | Builds React apps with MVVM architecture |
| **db-advisor** | Reviews PostgreSQL schemas, migrations, and queries |
| **devops** | Handles Kubernetes, Helm charts, and CI/CD pipelines |
| **tester** | Writes integration and E2E tests |
| **reviewer** | Reviews code for spec compliance and quality |

Each agent receives only the context it needs — the relevant spec sections, plan phases, and project files. No single agent tries to be everything.

> **Want to build a tech pack for your stack?** A tech pack is just a directory with a `techpack.yaml` manifest, agents, skills, and templates. Install it with `tech-pack install --repo <url>` and SDD picks it up automatically.

### Get started in 30 seconds

```bash
# Install the core plugin
claude plugins add sdd-engine/sdd-core

# Initialize a project and add a tech pack
/sdd-run init
/sdd-run tech-pack install --repo https://github.com/sdd-engine/sdd-fullstack-typescript-techpack
```

Then just tell SDD what you want to build.

---

<p align="center">MIT Licensed</p>
