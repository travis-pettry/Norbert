# Norbert Roadmap

## Strategic Approach

Norbert will be developed in two major stages.

### Stage One: Build Norbert on the GitHub Copilot SDK

Norbert will initially use the GitHub Copilot SDK to provide access to capable coding models and agent execution.

Norbert will remain responsible for:

- Defining the agents
- Assigning agent responsibilities
- Creating agent instructions
- Selecting available skills
- Selecting available MCP servers
- Controlling tool permissions
- Building project context
- Managing tasks and sessions
- Coordinating agent handoffs
- Running builds and tests
- Evaluating results
- Managing retries
- Recording memory
- Requesting human approval
- Determining when work is complete

The Copilot SDK will initially provide the model interaction and execution foundation.

Copilot will not define Norbert’s overall architecture.

Norbert owns the system.

### Initial Planning Exception

The initial implementation may use Copilot’s planning capability rather than immediately building a native Norbert planner.

This allows Norbert to focus first on:

- Agent orchestration
- Skills
- MCP integration
- Execution loops
- Verification
- Memory
- Permissions
- Developer review

Once those systems are proven, the planning capability can also be replaced with a Norbert-controlled local implementation.

### Stage Two: Replace the Copilot SDK

After Norbert’s architecture and workflows have been proven, the Copilot SDK will be replaced incrementally.

Norbert will introduce its own:

- Model-provider abstraction
- Local model runtime integration
- Native agent execution runtime
- Tool-calling system
- Context management
- Planning agent
- Agent communication model
- Session management
- Structured output handling

The goal is to preserve the proven Norbert workflow while replacing the external execution dependency beneath it.

---

# Architectural Principle

The first version of Norbert is not a Copilot automation wrapper.

It is an agent orchestration system that temporarily uses the Copilot SDK as its intelligence and execution backend.

The architectural relationship should be:

```text
Developer
    ↓
Norbert
    ├── Task management
    ├── Agent definitions
    ├── Agent orchestration
    ├── Skills
    ├── MCP servers
    ├── Context
    ├── Memory
    ├── Permissions
    ├── Verification
    └── Human approval
            ↓
    Copilot SDK adapter
            ↓
       Coding models
```

Later, the lower layer changes:

```text
Developer
    ↓
Norbert
    ├── Task management
    ├── Agent definitions
    ├── Agent orchestration
    ├── Skills
    ├── MCP servers
    ├── Context
    ├── Memory
    ├── Permissions
    ├── Verification
    └── Human approval
            ↓
    Norbert agent runtime
            ↓
       Local models
```

Everything above the provider boundary should remain stable.
---

# Milestones

## Milestone 1: Provider Boundary

The Copilot SDK is isolated behind a Norbert interface.

## Milestone 2: Norbert-Defined Agents

Agents are loaded from Norbert configuration rather than being implicitly defined by the provider.

## Milestone 3: Norbert-Defined Skills

Skills can be assigned to agents and composed into their instructions.

## Milestone 4: Norbert-Controlled MCP

Each agent receives only approved MCP servers and tools.

## Milestone 5: Copilot-Assisted Planning

Copilot creates an initial plan that Norbert validates and executes.

## Milestone 6: Norbert-Owned Execution Loop

Norbert controls steps, retries, agent handoffs, verification, and completion.

## Milestone 7: Persistent Norbert Memory

Project knowledge survives sessions and provider changes.

## Milestone 8: Proven SDK Architecture

Real tasks are completed reliably through Norbert-defined agents using the Copilot SDK.

## Milestone 9: Local Provider

Norbert agents can run through a local model endpoint.

## Milestone 10: Native Tool Loop

Norbert directly handles model-to-tool interaction.

## Milestone 11: Native Agent Runtime

Sessions, context, tools, and handoffs no longer depend on Copilot.

## Milestone 12: Native Planner

Planning no longer depends on Copilot.

## Milestone 13: Copilot Is Optional

Norbert is a complete local-first development agent platform.

---

# Guiding Transition

```text
Define agents in Norbert
        ↓
Assign Norbert skills
        ↓
Assign Norbert-managed MCP servers
        ↓
Execute through the Copilot SDK
        ↓
Measure the results
        ↓
Stabilize Norbert's contracts
        ↓
Implement a native local runtime
        ↓
Replace the SDK beneath the contracts
```

The first Norbert release will not automate Copilot.

It will orchestrate Norbert-owned agents through the Copilot SDK.

The mature Norbert release will run those same agents through a local, open-source runtime.
