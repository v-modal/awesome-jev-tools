# awesome-jev-tools

A curated awesome list of public projects and practices built on [Jev](https://typesafe.ai/blog/introducing-system-one-models-and-jev), TypeSafe AI's System One model for typed decisions.

This README is the homepage aggregate of the current category files, so the latest accepted entries are visible here without drilling into subpages.

A curated list of public projects and developer patterns built on Jev, TypeSafe AI's System One model for typed decisions.

What is Jev?
  Jev is not a chat model. 
  It does not write text or hold conversations. 

Instead, it takes unstructured state alongside a typed question and returns a typed decision—such as a choice, a score, or a boolean—accompanied by a confidence rating.By eliminating token-by token decoding, Jev acts as a fast, low-latency decision layer directly inside software. 

Developers use it to handle classification, infrastructure routing, rubric scoring, verification gates, and autonomous agent guardrails.Goal of this ListMost discussions about Jev are scattered across launch threads, social media, and one-off prototypes. 

This repository centralizes those pieces to answer two practical questions for developers:
   - Production Validation: Where is Jev actively making real decisions in live production workflows? 
   - Transferable Patterns: Which decision architectures can be cleanly copied and applied across different industries?




## Goal of this list

Most Jev discussion is scattered across launch threads, model-gateway listings, and one-off prototypes. This list answers two practical questions quickly:
- Where is Jev already making real decisions in production workflows?
- Which decision patterns transfer across industries?


## Inclusion criteria

We do **not** include:

- Generic classifiers, routers, or research agents that merely resemble the pattern without using Jev.
- Pure theory or opinion without a concrete practice.
- Launch-hype commentary with no working artifact or reproducible result.
- Long write-ups inside the list itself.
- Sources that are private, inaccessible, or too vague to classify.

## Curation is not endorsement

Inclusion means one thing: the entry satisfies the inclusion rules above. It is not a quality review, a security audit, or a recommendation. We do not verify that a project compiles, that its tests pass, that its published numbers reproduce, or that its license permits your use.

This matters most for projects that arrive in bulk. When one author releases several repositories on the same day, they commonly share a single scaffold — the same `AGENTS.md`, `CLAUDE.md`, `STATE.md`, and `CHANGELOG.md` — land in one or two commits each, and may ship considerably more prose than code. Such projects can be entirely legitimate; they are simply **unproven**. Treat them as leads, not as validated tools.

Before adopting an entry, check it yourself:

| Check | Why it matters |
| --- | --- |
| Does the code actually call the Jev API? | An entry can read well on a README alone. Look for a real request carrying typed questions, and a parsed answer coming back. |
| Is there a runnable check? | A test, an example with expected output, or a public demo. No check means no evidence that it works. |
| Do the numbers have a source? | Any accuracy, latency, cost, or volume figure should be traceable to the linked page. We strip claims we cannot verify, but the project page itself may still carry them. |
| How much of the repository is code? | Some projects are mostly prompt documents. That can be legitimate — just know which one you are getting. |
| Is there a license? | A few entries have none, which limits reuse and redistribution. |

Found something wrong? Open an issue or a pull request — **removal is as valid a contribution as addition.** Rules for AI-assisted work, project depth, and submission rate live in [CONTRIBUTING.md](CONTRIBUTING.md#ai-assisted-work-and-bulk-submissions).

## Current coverage

- [Classification & Routing](categories/classification-routing.md) — 20 entries
- [Verification & Guardrails](categories/verification-guardrails.md) — 20 entries
- [Scoring & Ranking](categories/scoring-ranking.md) — 13 entries
- [Agent Decisions](categories/agent-decisions.md) — 29 entries
- [Data Labeling & Curation](categories/data-labeling-curation.md) — 2 entries
- [Evaluation & Benchmarking](categories/evaluation-benchmarking.md) — 13 entries
- [Calibration & Research](categories/calibration-research.md) — 17 entries
- [Infra / SDKs / Integrations](categories/infra-sdks-integrations.md) — 33 entries
- [Game & Simulation](categories/game-simulation.md) — 8 entries
- [Finance & Trading](categories/finance-trading.md) — 3 entries
- [Compliance & Legal](categories/compliance-legal.md) — 1 entry
- [Content Moderation](categories/content-moderation.md) — 3 entries
- [Related Practices / Discussions](categories/related-practices-discussions.md) — 50 entries

### Open categories still being seeded

- [Scientific Pipelines](categories/scientific-pipelines.md) — 0 entries

Each entry lives in exactly one category. When a project could fit multiple categories, we choose the one closest to its direct application domain.

## Browse by category

- [Classification & Routing](#classification-routing) ([source](categories/classification-routing.md))
- [Verification & Guardrails](#verification-guardrails) ([source](categories/verification-guardrails.md))
- [Scoring & Ranking](#scoring-ranking) ([source](categories/scoring-ranking.md))
- [Agent Decisions](#agent-decisions) ([source](categories/agent-decisions.md))
- [Data Labeling & Curation](#data-labeling-curation) ([source](categories/data-labeling-curation.md))
- [Evaluation & Benchmarking](#evaluation-benchmarking) ([source](categories/evaluation-benchmarking.md))
- [Calibration & Research](#calibration-research) ([source](categories/calibration-research.md))
- [Infra / SDKs / Integrations](#infra-sdks-integrations) ([source](categories/infra-sdks-integrations.md))
- [Game & Simulation](#game-simulation) ([source](categories/game-simulation.md))
- [Finance & Trading](#finance-trading) ([source](categories/finance-trading.md))
- [Compliance & Legal](#compliance-legal) ([source](categories/compliance-legal.md))
- [Content Moderation](#content-moderation) ([source](categories/content-moderation.md))
- [Related Practices / Discussions](#related-practices-discussions) ([source](categories/related-practices-discussions.md))

## Full list

### Classification & Routing

Source file: [`categories/classification-routing.md`](categories/classification-routing.md)

- [Notra](https://github.com/usenotra/notra) - Marketing analytics: production GEO platform whose `NOTRA_JEV_CLASSIFIERS` flag routes brand-visibility classifiers off an LLM and onto Jev `Boolean` decisions at a 0.5 threshold, targeting 300 ms p50.
- [jev-router](https://github.com/gargpratyush/jev-router) - Developer tooling: routes Claude Code tasks to the cheapest capable model by asking Jev to choose among candidates.
- [jev-router (prismhq)](https://github.com/prismhq/jev-router) - LLM infrastructure: open-source LiteLLM-based router where a Jev decision picks which model serves each request.
- [pi-jev-router](https://github.com/mejiasd3v/pi-jev-router) - Coding agents: adds automatic per-request model routing to the Pi coding agent through Jev decisions on Vercel AI Gateway.
- [jcm-router](https://github.com/adarshmishra07/jcm-router) - Coding agents: local proxy that picks the Claude model and reasoning effort per message with a Jev decision while leaving the cached main chat untouched.
- [Switchboard](https://github.com/ruban-24/switchboard) - Developer tooling: assesses a new Claude Code or Codex conversation with Jev, then local confidence policy selects and pins its model and reasoning effort through follow-ups, tool calls, and resume to avoid unnecessary prompt-cache disruption.
- [jev-agent-skill-router](https://github.com/GodsBoy/jev-agent-skill-router) - Agent infrastructure: routes agent skill selection through typed, confidence-aware Jev decisions so weak matches are declined instead of guessed.
- [typesafe-jev CV screener](https://github.com/gtaras7/typesafe-jev) - Recruiting: screens a folder of CVs with Jev typed judgments against an editable policy, re-scoring candidates for free when the policy changes.
- [Jev email intent workflow](https://github.com/GiesN/typesafe-jev-workflow) - Back-office automation: async LangGraph workflow gets a typed Jev `Choice` (`invoice` or `general`) and routes each inbound email to the matching handler.
- [unclutter](https://github.com/kitze/unclutter) - Browser tooling: WXT extension where Jev decides per page element whether it is clutter, removing it under reusable template rules.
- [typesafe-adblock](https://github.com/realZachi/typesafe-adblock) - Browser tooling: Chrome extension that asks Jev whether each DOM element is an ad, turning ad blocking into a stream of per-element typed questions.
- [DiffJury](https://github.com/raihankhan-rk/diffjury) - Code review: routes each pull request by risk with Jev before a human reviewer is assigned, doubling as a review coach.
- [HA-Jev](https://github.com/AboveColin/HA-Jev) - Smart home: Home Assistant integration that answers questions about the house as a probability, a choice, or a score.
- [secondlayer](https://github.com/ryanwaits/secondlayer) - Fault triage: self-hosted Stacks data service whose Slack gate and fault-triage paths both run on Jev decisions.
- [new-api-typesafe-plugin](https://github.com/FFatTiger/new-api-plugin-typesafe) - LLM gateway: adds a native `/v1/systemone` endpoint to new-api so typed decisions sit behind the same gateway as chat models.
- [duet-agent](https://github.com/dzhng/duet-agent) - Agent harness: keeps a Jev-backed routing table for deciding which model should serve a request.
- [json-render](https://github.com/vercel-labs/json-render) - Generative UI: Vercel Labs' UI framework uses Jev in its compose path to pick which components and actions a rendered interface should contain.
- [omo-jevlike-router](https://github.com/islee23520/omo-jevlike-router) - Skill routing: shrinks the skill catalog in a system prompt with one forward pass over a frozen Qwen, routing each request Jev-style.
- [jev-cookbook](https://github.com/nexibeo/jev-cookbook) - Developer education: 15 runnable Node recipes that route support tickets, file documents, categorize bank transactions and label Gmail with Jev `Choice` and `Noul` questions, sending low-confidence answers to human review.
- [flue-jev-demo](https://github.com/matthewp/flue-jev-demo) - Agent routing: routes a Flue agent's work with Jev through Cloudflare AI Gateway.
- [sift](https://github.com/bohutang/sift) - Content labelling: Chrome extension that labels every post in an X timeline - substance, humour, chit-chat, promo, junk, or AI-written - with Jev decisions.

### Verification & Guardrails

Source file: [`categories/verification-guardrails.md`](categories/verification-guardrails.md)

- [is-malicious](https://github.com/luantak/is-malicious) - Software supply-chain security: asks Jev `Noul` checks about source and build files, escalates suspicious chunks for a second pass, and returns implicated files and lines before execution.
- [jev-review](https://github.com/devagrawal09/jev-review) - Software engineering: staged code-review workflow and local dashboard where Jev gates each review stage before a change advances.
- [pi-jev](https://github.com/y0usaf/pi-jev) - Agent safety: adds a measured tool-call gate to the Pi coding agent so risky calls are checked by Jev before execution.
- [OpenWork](https://github.com/different-ai/openwork) - Engineering workflow: wires Jev into its eval testkit as a verification judge so agent-produced work is gated by typed verdicts rather than a text model.
- [jev-guard](https://github.com/leepokai/jev-guard) - Agent security: prompt-injection and dangerous-action guard for Claude Code, Codex, Pi, and ACP agents, with Jev deciding what to block.
- [Foreman](https://github.com/thruwire/foreman) - Software factory: sits above Codex workers and has Jev independently judge whether an implementation is complete, its tests sufficient, or a human is needed.
- [stanley-code](https://github.com/devagrawal09/stanley-code) - Coding agents: bounded Jev workflows that keep agent judgments typed instead of free-form.
- [opencompany](https://github.com/useopencompany/opencompany) - Agent workspace: runs its approval review through Jev so workspace actions are gated by a typed decision.
- [jev-git](https://github.com/AkashPriyadarshii/jev-git) - Developer tooling: sub-second Git pre-commit & pre-push reflex gate that screens staged diffs for secrets and destructive commands using Jev.
- [pi-heed](https://github.com/Nyarlathoteppppp/pi-heed) - Runtime constraints: checks every side-effecting tool call from the Pi agent against what the user actually asked for.
- [Hunch](https://github.com/Kelbie/hunch) - Code review: plain-English rules that Jev checks code against, locally or on every pull request, with Jev picking one label per finding.
- [Abide](https://github.com/coldteadotai/abide) - Agent supervision: reads every edit a coding agent makes and has Jev flag rule violations, with the project reporting that an independent reviewer confirmed 10 of the 39 flagged edits and 11 of the 15 flagged turns.
- [fx](https://github.com/vercel-labs/fx) - Coding agent: ships a `typesafe_permission_reviewer` builtin so the agent's permission decisions run through Jev rather than an LLM call.
- [Sniff Test](https://github.com/DanRWilloughby/snifftest) - Writing: prose linter that asks Jev ten `Boolean` questions per paragraph (stacked hedges, restating closers, not-X-but-Y turns, naked cost figures) at a 0.7 threshold; CLI, pre-commit hook, GitHub Action and Claude Code skill; measured 182 ms median and 1 of 54 clean paragraphs flagged against 37 for Haiku 4.5.
- [jev-pref](https://github.com/doeixd/jev-pref) - Code review: turns the preferences in a project's AGENTS.md into `jev-pref.json` rules that Jev checks against each diff hunk, staged file set, or pull request, returning `fix_now` or advisory findings to the coding agent and a nonzero exit code on blocking ones.
- [jev-axi](https://github.com/shiftynick/jev-axi) - Agent safety: PreToolUse gate for Claude Code and Codex that has Jev score each shell command for destructiveness, exfiltration, remote code execution, and security weakening, deciding routine commands locally so nothing is sent for them, and scoring 44/44 on the 44 labeled tool calls in its repository.
- [pi-verdict](https://github.com/jesset/pi-verdict) - Agent safety: Pi permission gate where Jev answers one Choice (allow/ask/deny) per gray-zone tool call — deterministic rules settle clear cases first, deny blocks, ask escalates to a human confirm, and errors or timeouts deny; Jev is an optional backend, OpenRouter-only and experimental.
- [jev-commit](https://github.com/valentynkit/jev-commit) - Developer tooling: pre-commit hook where one Jev call judges whether the commit message matches the staged diff, flags debug leftovers and unmentioned work, and blocks only on a detected credential.
- [Blink](https://blink.review) - Code review: CLI that coding agents run after every change, with Jev checking the diff near-instantly in place of an LLM reviewer.
- [hermes-jev-approvals](https://github.com/anpicasso/hermes-jev-approvals) - Agent approvals: proof of concept that puts Jev in front of Hermes Agent's command approvals, reporting 8.7x faster decisions and 4.4x fewer prompts to the user.

### Scoring & Ranking

Source file: [`categories/scoring-ranking.md`](categories/scoring-ranking.md)

- [Clean Code Judge](https://github.com/frostney/clean-code-review) - Code quality: scores every file of a pull request on 31 boolean Clean Code smells plus function size and nesting, then hands the verdicts to a writing model for the review prose.
- [citation-verifier](https://github.com/MarissaFamularo/citation-verifier) - Academic publishing: checks whether each cited paper actually supports the sentence citing it, with Claude locating the quote, Jev scoring the support, and a human making the final call.
- [jev-bfs](https://github.com/komikat/jev-bfs) - Search tooling: finds link paths between English Wikipedia articles by having Jev rank each page's outgoing links while Python controls the search.
- [Jev Search](https://github.com/superagents-lab/jev-search) - Web search: uses Jev Noul judgments on result titles and snippets to rank Search1API results by relevance, with application code merging duplicate URLs and grouping lower-scoring matches separately.
- [pagegrade](https://github.com/kitze/pagegrade) - Content quality: grades page sections for clarity, writing, and on-page SEO with Jev and returns per-section scores.
- [jev-scout](https://github.com/AkashPriyadarshii/jev-scout) - Developer tooling: sub-second zero-hallucination open-source repo and crate scout using TypeSafe Jev speculative fan-out scoring.
- [jev-seo](https://github.com/AkashPriyadarshii/jev-seo) - Zero-cost, agent-first SEO & Generative Engine Optimization (GEO) search radar CLI suite and MCP server powered by DuckDuckGo and TypeSafe Jev System One.
- [JevSlop](https://github.com/TKY-27/JevSlop) - Writing quality: scores public note.com articles on eight Jev `Score` axes inside a single `systemOne` request and turns them into a 0-100 Slop Score in ordinary TypeScript.
- [SemanticSpace](https://semanticspace.dev/) - Semantic mapping: places phrases in 2D by asking Jev how strongly each one relates to two chosen axis concepts and using those scores as coordinates.
- [Supercov](https://github.com/supercorp-ai/supercov) - Code quality for coding agents: Jev answers twelve `Noul` properties per source file so the agent knows what to fix first.
- [jev.nvim](https://github.com/valentynkit/jev.nvim) - Developer tooling: Neovim plugin that splits the buffer into functions with Treesitter, scores each against a plain-language question with Jev, and ranks answers by probability in quickfix.
- [jev-reranker](https://github.com/hotchpotch/jev-reranker) - Retrieval and RAG: uses Jev Noul judgments to assess retrieved documents for relevance and usefulness as answer evidence, then sorts results and optionally filters them using a configurable threshold.
- [jev-skip](https://github.com/valentynkit/jev-skip) - Media: browser extension that reads the YouTube caption track and scores each segment's sponsor probability on the seek bar before the intro ends, reporting 77% of SponsorBlock's sponsor seconds caught over 23 videos at $0.0008 a video.

### Agent Decisions

Source file: [`categories/agent-decisions.md`](categories/agent-decisions.md)

- [jev-social](https://github.com/socai-io/jev-social) - Social media research: uses a Jev `Choice` at each step to select a concrete socai CLI operation and observed post or profile target on Instagram, TikTok, or LinkedIn, rejecting malformed or low-confidence decisions before execution.

- [Jev Ultrafast](https://github.com/browser-use/jev-ultrafast) - Browser automation: browser-use's ultrafast agent where Jev decides each next action and element to click, calling a language model only when text must be typed.
- [jev-agent-browser](https://github.com/forvela/jev-agent-browser) - Browser agents: a parent agent delegates bounded tasks to a Jev loop that selects typed browser actions, validates them through agent-browser, and escalates ambiguity or stuck states back to the parent.
- [pi-typesafe-jev](https://github.com/legacybridge-tech/pi-typesafe-jev) - Coding agents: exposes System One judgments as five Pi tools so a model makes narrow semantic judgments while code and users keep control of thresholds, weights, and actions.
- [jev-judgment](https://github.com/HyunjunJeon/jev-judgment) - Coding agents: agent skill that sends closed coding-agent judgments to Jev so verdicts stay typed, cheap, and comparable across runs.
- [limpet](https://github.com/noplan-inc/limpet) - Coding agents: Stop hook that keeps an agent from finishing too early by judging plain-language completion rules with Jev.
- [robo-harness](https://github.com/grmkris/robo-harness) - Robotics: SO-101 arm workbench where a Jev decision runner picks bounded joint steps from typed candidate actions under a spend budget.
- [dsh-auto-mode](https://git.allen-software.com/allenh1/dsh-auto-mode) - Coding agents: DeepSeek Harness permission preset whose end-prompt step has Jev answer the open questions an agent leaves in its final message, steering them back only when a choice clears 0.6 confidence and an autonomy-safety Noul clears 0.5, and returning the turn to the human otherwise.
- [augustus](https://github.com/24601/Augustus) - Coding agents: agent skill that maps Choice, Score, and Noul onto classical methods so an agent can place typed judgment in software, with a composition algebra, question-design diagnosis, and a validation gate that requires a falsifying experiment.
- [yoshi](https://github.com/compozy/yoshi) - Context management: proxy for Claude Code and Codex where Jev judges which conversation history is still needed before pruning.
- [pi-jev (TheoOliveira)](https://github.com/TheoOliveira/pi-jev) - Coding agents: semantic tool routing and typed System One decisions for the Pi coding agent.
- [pi-quiet-ask](https://github.com/HyunjunJeon/pi-quiet-ask) - Coding agents: gives the Pi agent a quiet Jev decision layer for judgments it would otherwise hand to a chat model.
- [fastbrowse](https://github.com/agent-labs-dev/fastbrowse) - Browser agents: Jev picks each action from what is on the page while an LLM reads and plans.
- [super-jev](https://github.com/Kevthetech143/super-jev) - Decision harness: turns a Jev answer into a bounded action instead of leaving the caller to interpret it.
- [jev-superpowers](https://github.com/AkashPriyadarshii/jev-superpowers) - Systematic software development framework for AI coding agents upgraded with TypeSafe Jev System One typed decisions, zero-hallucination package vetting, and completion gates.
- [Jev Browser](https://github.com/jkudish/jev-browser) - Browser automation: drives a browser with Jev deciding each step, pitched as fast and very cheap next to LLM-driven browsing.
- [pi-fast-jev-compaction](https://github.com/joelhooks/pi-fast-jev-compaction) - Context management: Pi extension that keeps conversation text verbatim while pruning stale tool history with Jev, falling back to Pi's own summarization only when pruning cannot free enough room.
- [Atomic](https://github.com/bastani-inc/atomic) - Coding agent runtime: ships a first-class Jev structured-output provider so an agent's decisions come back typed, through the same decision resolver as its other providers.
- [fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) - Context management: Claude Code plugin that replaces the compaction summary with Jev decisions, scoring every tool call and result for whether it is still needed instead of summarizing the session.
- [fast-dev-compaction](https://github.com/leonaaardob/fast-dev-compaction) - Context management: Codex port of the Jev-guided compaction idea, restoring context verbatim around a session compaction rather than summarizing it.
- [public-browser](https://github.com/Silbercue/public-browser) - Browser control: lets Claude Code and Cursor drive a real Chrome profile, with a Jev loop deciding the actions, reporting roughly 30% fewer tokens and 25% lower cost.
- [pi-typesafe-router](https://github.com/jekozyra/pi-typesafe-router) - Coding agents: routes Pi's work through typed Jev decisions.
- [wakegate](https://github.com/shitianfang/wakegate) - Long-running agents: before a sleeping agent's LLM is resumed on a timer or incoming event, Jev answers a `Choice` (wake, not yet, unrelated) against the agent's own sleep note, and code skips the wakeup only when wake is below 0.2 while always waking on user messages, bare timers, a skip limit, errors, and timeouts; one run passed 21 of 21 hand-written scenarios, which the README calls a smoke test rather than a benchmark.
- [BrowserClaw](https://github.com/GoldenLoaf24h/browserclaw) - Browser automation: Zero-lock, session-preserving Chrome MCP server that couples a local Jev System One semantic micro-loop (`chrome_act_toward_goal`) with an 85%+ pruned DOM tree (Shadow DOM & iframe pierced), dispatching native CDP events (`isTrusted: true`) on active logged-in sessions without focus theft.
- [jev-canvas](https://github.com/gaborishka/jev-canvas) - Multimodal UI: draw on a tldraw canvas by voice while pointing a webcam-tracked finger; on every partial transcript Jev answers eight typed questions (is it a command, is the sentence complete, action, shape, colour, target, place, size) and plain code gates them with thresholds, in English and Ukrainian, 300–550 ms per decision.
- [jev-belay](https://github.com/valentynkit/jev-belay) - Coding agents: Claude Code Stop hook that reads the transcript for evidence and spends one four-question Jev call only when files changed with no passing check since, failing open on any error.
- [Jev for Chrome](https://github.com/chy4pro/jev-for-chrome) - Browser automation: unofficial Chrome extension port of Jev Ultrafast where a Jev `Choice` picks the operation and DOM element each step and two `Noul` checks (goal reached, stuck) veto a premature DONE or BLOCKED, with a small text model used only when text must be typed.
- [jev-pruner](https://github.com/tamaratran/jev-pruner) - Context management: Claude Code plugin that trims long Bash output with Jev before the model ever sees it, keeping terminal noise out of the window.
- [jev-desktop](https://github.com/yikangy873-gif/jev-desktop) - Computer use: supplies Jev action selection inside Codex Computer Use, choosing among desktop actions rather than asking a language model at every step.

### Data Labeling & Curation

Source file: [`categories/data-labeling-curation.md`](categories/data-labeling-curation.md)

- [jev-curate](https://github.com/AkashPriyadarshii/jev-curate) - Dataset engineering: sifts synthetic JSONL and Parquet rows using Jev Noul checks and calibrated confidence scores, streaming passed records and rejections straight to disk.
- [typeful-triage](https://github.com/cephalization/jev-triage) - Open-source maintenance: multiplayer triage dashboard where Jev answers a fixed set of typed questions per issue — kind, severity, urgency, duplicate, and next step — and every human correction is kept and shown back to the model on later runs.

### Evaluation & Benchmarking

Source file: [`categories/evaluation-benchmarking.md`](categories/evaluation-benchmarking.md)

- [Jev Playground](https://github.com/hegargarcia/jev-playground) - Model evaluation: benchmarks Jev against Luna, Haiku, and Gemini at choosing validated legal moves in explicit-state games, scoring decision quality and consistency across a sequence of moves.
- [Jev vs Mistral and Gemini for event validation](https://nearhere.events/blog/typesafe-jev-mistral-gemini-event-validation) - Event discovery: head-to-head test of Jev against Mistral Small and Gemini Flash-Lite at validating local event listings.
- [jev-research-eval](https://github.com/jgridifier/jev-research-eval) - Research automation: reproducible eval harness plus field note for Jev Ultrafast research-browser tasks, with QC'd cases, a suite runner, and a report generator.
- [Jev judge call vs dimension scores](https://agentjournal.dev/blog/llm-judge-vs-feature-extraction/) - Model evaluation: tests one direct Jev question per row against 12–14 Jev-scored dimensions with locally fitted weights on three classification tasks, reaching 0.9076 against 0.8373 on Japanese NLI but flagging about 25× more hard benign rows as attacks.
- [Jev Pong](https://github.com/ably-labs/jev-pong) - Model comparison: Pong where the ball advances one step per model decision, putting Jev head-to-head with LLMs through Vercel AI Gateway.
- [Jev reranking is not a free win](https://x.com/GoSailGlobal/status/2100877682972258619) - Search reranking: a measured run over 33,047 catalog entries, 164 real queries, and 9,831 graded pairs reports that Jev reranking alone did not beat vector retrieval.
- [An early-access test of TypeSafe's Jev](https://lindfors.no/blog/a-first-look-at-typesafes-jev/) - Independent trial: measures calibrated judgments on early-access Jev and reports the resulting cost per decision.
- [jevcal](https://github.com/abhixhek/jevcal) - Model evaluation: fits a per-question confidence threshold to a target accuracy on your own labeled data, verifies it on a held-out split, reports how much traffic still has to escalate to an LLM, and fails CI when a model update breaks the locked thresholds.
- [WindTunnel](https://github.com/nekuda-ai/WindTunnel) - Browser-agent benchmark: measures WebMCP against other browser-agent interfaces, with Jev appearing as one of the compared configurations.
- [jev-eval](https://github.com/Shogo-nfrealmusic/jev-eval) - Third-party check: compares Jev against GPT-4o-mini and Claude Sonnet 4.5 under identical conditions on the same judgment task.
- [minutes](https://github.com/silverstein/minutes) - Meeting notes: local-first transcription app whose live voice path runs its evaluations through Jev.
- [jev-orderby-bench](https://github.com/yodablocks/jev-orderby-bench) - Model evaluation: measures whether a SQL ORDER BY over a Jev probability is defensible (pairwise inversion, Score ordinality against a human grade, calibration, wording invariants, sort-key ties) under a pre-registered gate that jev-1.13.0 passes on 20 Newsgroups topics and fails four of six conditions on Amazon ESCI product relevance, and shows a DuckDB extension's default 40-row batching fails the ranking gate that one row per request passes.
- [jev-ood-calibration](https://github.com/scienthoon/jev-ood-calibration) - Model evaluation: independent calibration test of Jev on 900 rule-generated support tickets it cannot have seen plus three public benchmarks, publishing every raw response, ECE against a simulated noise floor, temperature refit, and the per-type sign of miscalibration (Choice and Score overconfident, Boolean underconfident).

### Calibration & Research

Source file: [`categories/calibration-research.md`](categories/calibration-research.md)

- [decider](https://github.com/Mapika/decider) - Open models: reproduces the System One shape with a Qwen3.5-2B fine-tune that emits typed decisions with calibrated probabilities in one pass.
- [openjev](https://github.com/zhihz/openjev) - Open research: independent local preview that answers bilingual probability questions from context, questions, and candidate answers, inspired by TypeSafe Jev.
- [Parallel Constrained Decoding (Qwen2.5-1B-RLCD)](https://huggingface.co/spaces/drinkmoonshine/parallel-constrained-decoding) - Open research: RLCD-trained Qwen2.5-1B demo exploring open-source parallel constrained decoding as an alternative to Jev.
- [NanoJev](https://github.com/TianyuCodings/NanoJev) - Open replica: a 0.6B parallel decision model that returns full probability distributions with no output-token decoding, shipped with its training pipeline, weights, and dataset.
- [open-alternative-jev](https://github.com/ikermoel/open-alternative-jev) - Open alternative: runs a Jev-shaped decision model locally on your own GPU.
- [mini-jev](https://github.com/r-ms/mini-jev) - Local reproduction: implements Jev's typed-decision interface on top of a local LLM.
- [Laya](https://github.com/NandhaKishorM/laya) - Open alternative: non-autoregressive decision model that answers `choice`, `score`, and `noul` questions with RLCD-trained calibrated probabilities in a single ~35 ms forward pass, published on PyPI and Hugging Face.
- [Jev-compatible public API](https://x.com/ekzhang1/status/2100651678110515383) - Open research: a public Jev-shaped API backed by an open Qwen3.6-35B-A3B model so anyone can try the typed-decision interface.
- [kev](https://github.com/jaredpalmer/kev) - Trainable replica: a tiny Jev-like model on top of Qwen2.5-0.5B that trains and runs on a MacBook, shipped with its own research runs and evaluation scripts.
- [jevinci](https://github.com/achimala/jevinci) - Creative experiment: paints images by having Jev predict every pixel's colour in parallel, with predicted confidence deciding how wide each stroke is drawn.
- [jev-local](https://github.com/us/jev-local) - Local reproduction: Jev-compatible `POST /v1/systemone` server answering typed `Choice`/`Score`/`Noul` questions with confidence from open weights, verified as an official-SDK drop-in with temperature-fit calibration (set3 n=1316, 0.83 overall).
- [LitJev](https://github.com/zhengxuyu/litjev) - Local reproduction: a reproduction of Jev that turns any Qwen model into a fast decision model, serving the same `/v1/systemone` schema (Choice, Score, Noul) with no training and no generated answer text.
- [CUA-S1-FORMS](https://huggingface.co/cua-ai/cua-s1-forms) - Specialist decision model: a 706,048-parameter, 2.8 MB jev-like option scorer that rates FILL / CHECK / CLICK / SKIP for each form field in one parallel pass, reporting 99.7% on its own form-filling eval against Jev's 83.6% - a specialist on home turf rather than a general win.
- [jevlike](https://github.com/vinnylarouge/jevlike) - Training library: build a small model that chooses among a changing list of text options and returns one probability per option in a single pass - the base CUA-S1-FORMS was built on.
- [jevbetter](https://github.com/olanotolu/jevbetter) - Improved scorer: a stronger one-pass scorer over a variable list of text options, using a hashed n-gram encoder, rival-aware attention, and gated heads.
- [jevlike-esp32](https://github.com/david-cermak/jevlike-esp32) - Edge deployment: exports a jevlike scorer as ESP32 firmware with a C scorer and a host-side check, putting one-pass decisions on a microcontroller.
- [von](https://github.com/wfzyx/von) - Open alternative: a 395M non-autoregressive System One model that answers typed questions with calibrated probabilities in under 15 ms, positioned as a local drop-in replacement for Jev.

### Infra / SDKs / Integrations

Source file: [`categories/infra-sdks-integrations.md`](categories/infra-sdks-integrations.md)

- [eve](https://github.com/vercel/eve) - Agent frameworks: Vercel's eve engine ships Jev as the default evaluation model (`typesafe-ai/jev`) in its experimental evaluate path.
- [AI CLI](https://github.com/vercel-labs/ai-cli) - Developer tooling: Vercel Labs CLI that can run Jev as the evaluation model for its `evaluate` command.
- [jev-mcp (jkudish)](https://github.com/jkudish/jev-mcp) - MCP ecosystem: proof-of-concept MCP server that puts Jev claim verification, content screening, and candidate ranking behind standard MCP tools.
- [jev-mcp (blakestone-x)](https://github.com/blakestone-x/jev-mcp) - MCP ecosystem: MCP server exposing Jev classify, score, check, match, and screen as tools for any agent, with confidence on every answer.
- [zio-typesafe-ai](https://github.com/jamesward/zio-typesafe-ai) - Scala ecosystem: ZIO client for TypeSafe AI with a typed DSL over Jev decisions.
- [TypeSafe AI Swift SDK](https://github.com/alterhq/typesafe-sdk-swift) - Swift ecosystem: dependency-free Swift 6 client for Jev Choice, Score, and Noul questions with strict concurrency, configurable authentication and retries, and offline transport tests.
- [laravel-typesafe-jev](https://github.com/Butochnikov/laravel-typesafe-jev) - PHP ecosystem: unofficial Laravel integration for Jev with typed responses, async requests, scoped dependency injection, and testing fakes.
- [advocaat](https://github.com/pithings/advocaat) - Data tooling: small type-safe client for asking Jev questions about a dataset.
- [jevclient](https://pypi.org/project/jevclient/) - Python ecosystem: async client for Jev published on PyPI.
- [LlamaIndex Jev](https://github.com/WiktorB2004/llama-index-jev) - Retrieval / RAG: unofficial LlamaIndex adapter where Jev `Score`s each retrieved passage and `Choice`/`Noul` selects the query engine, with nfcorpus nDCG@5 0.340→0.396 at about $0.0003/query.
- [safer-with-jev](https://github.com/andrelandgraf/safer-with-jev) - Cloud infrastructure: Neon Function proxy for the Neon AI Gateway that routes decisions with Jev.
- [typesafe-ai/skills](https://github.com/typesafe-ai/skills) - Official tooling: installable agent skills package (`npx skills add typesafe-ai/skills`) that teaches agents the Jev workflow.
- [Smithers](https://github.com/smithersai/smithers) - Agent frameworks: TypeScript workflow framework with a Jev session checker wired into its workflows.
- [skillbox](https://github.com/kitze/skillbox) - Skills infrastructure: self-hosted versioned skills library that adds optional Jev recommendations using your own TypeSafe or Gateway key.
- [Jevbridge](https://github.com/tacticocc/Jevbridge) - Agent bridges: ACP and MCP adapter that exposes Jev typed decisions to Codex, Claude, Grok, and other LLMs.
- [jev (Elixir)](https://github.com/dannote/jev) - Elixir ecosystem: GenServer client that replies with Jev's answer so callers can pattern match on it directly.
- [jev-go](https://github.com/Stumble/jev-go) - Go ecosystem: community Go SDK for Jev.
- [jev-cli](https://github.com/tumf/jev-cli) - Developer tooling: small dependency-free CLI for Jev.
- [decide-mcp](https://github.com/dakdevs/decide-mcp) - MCP ecosystem: configurable decision server with percentage scores and bias-profile routing on top of Jev.
- [typesafe-jev-examples](https://github.com/rajivkuriakose/typesafe-jev-examples) - Starter examples: worked ticket-triage and reranking examples runnable through OpenRouter without an early-access key, shipped with their own sample data and Makefile.
- [ai-python](https://github.com/vercel-labs/ai-python) - Python ecosystem: the official Vercel AI SDK for Python carries Jev through its evaluation operation and Gateway examples.
- [Cline plugins](https://github.com/cline/plugins) - Coding agents: Cline's official plugin collection includes a Jev-driven browser plugin (`jev-browser`), so Jev arrives as a first-class Cline capability.
- [hono-jev-router](https://github.com/yusukebe/hono-jev-router) - Web frameworks: Hono middleware that routes HTTP requests by meaning rather than by method and path, deciding with Jev.
- [rotom](https://github.com/RyanKung/rotom) - Local gateways: OpenAI- and Anthropic-compatible API gateway that carries Jev through its model catalog and evaluation path.
- [Jev AI](https://jev-ai.pro) - Developer tooling: public Jev playground and API that puts typed `Choice`, `Score` and Yes/No questions to the model about pasted text - ticket triage, moderation, review scoring - and returns a parsed answer with a confidence value in about 0.5 s per decision.
- [jevql](https://github.com/kylemclaren/jevql) - Data tooling: psql-shaped CLI and Go/TypeScript/Python SDKs that run plain SQL on a vanilla Postgres (no extension) and then ask Jev Noul, Choice, or Score questions about each surviving row so the client can apply `jev()` filters, `jev_prob` sorts, and `jev_choice` groups.
- [sqlite-jev](https://github.com/mgaitan/sqlite-jev) - SQLite ecosystem: loadable C extension and Python package that expose Jev Noul, Choice, and Score judgments as SQL functions and batched virtual-table queries with confidence results.
- [jevkit](https://github.com/ariel-frischer/jevkit) - Developer tooling: Rust CLI that validates `Choice`/`Score`/`Noul` question sets with 13 offline lint rules before any Jev call, then sends the canonical wire payload and prints parsed, confidence-bearing JSON answers to stdout using exit code 2 to reject a billed-but-useless request.
- [jev-use](https://github.com/shitianfang/jev-use) - MCP ecosystem: Claude Code / Codex / pi plugin (MCP server + library, native pi extension) that hands agent steps needing no text output to Jev as typed judgments — untypeable and generation-needing questions are rejected before the call, low-confidence answers come back flagged as priors, and a fail-open PreToolUse gate can only deny or ask.
- [huncho](https://github.com/edgardcham/huncho) - TypeScript ecosystem: dependency-free SDK that turns Jev `Noul`, `Choice` and `Score` answers into named decisions with `enter`/`exit` thresholds (hysteresis), nested decision trees settled in one call, a JSONL journal, replay of a threshold change over recorded answers with no inference, and Brier/reliability calibration, over TypeSafe direct, OpenRouter or Vercel AI Gateway.
- [jev-experiments](https://github.com/dabit3/jev-experiments) - Demo collection: 22 latency-focused Jev applications built by Devin, each with its own README and testing notes, spanning shell guards, log sentinels, instant search, reranking, and voice turn-taking.
- [ruby_decision_model](https://github.com/obie/ruby_decision_model) - Ruby ecosystem: client for decision models such as Jev, so Ruby applications can put typed questions directly to the model.
- [s1_ruby](https://github.com/innocentdiaz/s1_ruby) - Ruby ecosystem: makes System One measurement, and the collapse that follows it, a Ruby primitive, with a TypeSafe provider behind its own spec suite.

### Game & Simulation

Source file: [`categories/game-simulation.md`](categories/game-simulation.md)

- [typesafe-mario](https://github.com/fhshaik/typesafe-mario) - Gaming: TypeSafe/Jev agent that plays Super Mario Bros. from structured emulator state, choosing each action from emulator-derived features.
- [jev-drone](https://github.com/RomanSlack/jev-drone) - Robotics simulation: camera-only autonomous drone in MuJoCo that puts a Jev judgment model in the control loop at 2.5 Hz.
- [tsai-sc](https://github.com/phyous/tsai-sc) - Gaming: drives original StarCraft shareware through keyboard and mouse with Jev action probabilities recorded per decision.
- [jev-plays-pokemon](https://github.com/milanboers/jev-plays-pokemon) - Gaming: reads Pokémon Red game state as text, answers typed questions each turn, and lets deterministic code turn the answers into moves.
- [typesafe-jev-drone-demo](https://github.com/kxzk/typesafe-jev-drone-demo) - Simulation: Three.js drone simulator with a Python backend where Jev drives the navigation decisions.
- [typesafe-playground](https://github.com/kavehmz/typesafe-playground) - Interactive playground: small Jev experiments that put the decision on screen, from routing a support message to steering a car in a 3D world.
- [PlayJev](https://github.com/OmniJev/PlayJev) - Gaming: open 0.8B vision-language model that reads one 448 px game frame, returns a probability over the moves the game lists in a single forward pass with no generated text, and hands its low-confidence steps to a search program, across ten browser games.
- [jev-plays-pokemon-red](https://github.com/valentynkit/jev-plays-pokemon-red) - Gaming: Pokemon Red on PyBoy where deterministic code owns the route and arithmetic, Jev picks only at branches, and every battle turn's faint prediction is scored by Brier against RAM state.

### Finance & Trading

Source file: [`categories/finance-trading.md`](categories/finance-trading.md)

- [Jevinik](https://github.com/unicodeveloper/jevocks) - Stock decisions: terminal that gathers live market evidence through Valyu and asks Jev whether a stock is likely to trade higher over the next 30 days.
- [jev_stock](https://github.com/sosopop/jev_stock) - Short-term forecasting: experimental Hong Kong stock framework that turns structured market state into a Jev decision on price direction, with a backtest script for the first trading day.
- [jev-trade](https://github.com/aowang-ai/jev-trade) - Crypto trading: asks Jev for a Choice of long or short on a Hyperliquid market each round, places that order, and runs the same loop across many assets.

### Compliance & Legal

Source file: [`categories/compliance-legal.md`](categories/compliance-legal.md)

- [LegalForecast-MTD](https://github.com/johnhughes3/LegalForecastBench) - Legal forecasting: benchmark that asks Jev to predict federal motion-to-dismiss rulings from the judge's written record and scores the calibrated probabilities with claim-defendant micro-Brier metrics.

### Content Moderation

Source file: [`categories/content-moderation.md`](categories/content-moderation.md)

- [Jev Moderation Bot](https://github.com/brainstormity/Jev-Moderation-Bot) - Community moderation: Discord bot that scores incoming messages for phishing, spam, and social engineering with Jev and drives a four-stage escalation ladder, injecting pardoned messages back into context as verified-safe precedent.
- [jev-spam-eval](https://github.com/bitnovus/jev-spam-eval) - Spam filtering: zero-shot spam classification with Jev `Boolean` questions, benchmarked against TF-IDF baselines.
- [mastra-jev-moderation](https://github.com/CodeAlive-AI/mastra-jev-moderation) - AI assistants: Mastra input processor that asks Jev a `Boolean` "must this message be blocked?" plus a category `Choice` in one request, aborting the turn at 0.7 and failing open behind a deadline and circuit breaker; in production it blocked 9/9 hostile and 0/49 real messages at ~0.4 s median, about 4× cheaper than an LLM moderator.

### Related Practices / Discussions

Source file: [`categories/related-practices-discussions.md`](categories/related-practices-discussions.md)

- [Introducing System One Models and Jev (Hacker News)](https://news.ycombinator.com/item?id=49717558) - Hacker News: 1,800-point launch thread whose ~480 comments debate whether typed decisions replace LLM calls for classification, routing, and verification.
- [Launch thread by Diogo Almeida](https://x.com/CompleteSkeptic/status/2099925682726002904) - X: the 63k-like announcement from TypeSafe's founder arguing RLCD-trained decision models are a shorter path to economic value than chat models.
- [Model router built with Jev](https://x.com/ephraimduncan/status/2100454070536351824) - X: 948-like demo where Jev decides which model should serve a request before it is forwarded.
- [MLP on Qwen 4B mimicking Jev](https://x.com/justALEXWORTEGA/status/2100341039986798930) - X: builder reports that a small MLP trained on top of Qwen 4B already reproduces Jev-like decision behaviour.
- [Running a local Typesafe Jev](https://x.com/wmoto_ai/status/2100454049359577516) - X (Japanese): attempt at running a Jev-style decision model locally, with speed noted as still improvable.
- [Jev as an AI agent safety monitor](https://x.com/isNickMa/status/2100566407524344225) - X: test report using Jev to check each agent action first, reportedly catching most attacks with almost no false blocks and much lower latency.
- [Rethinking security engineering with Jev](https://x.com/Kostastsale/status/2100362415187833048) - X: argues that purely engineering decisions in security work belong to Jev rather than a chat model.
- [Ask Jev anything, it will judge](https://x.com/waynesutton/status/2100487878992388279) - X: public Convex-backed demo inviting one million judged questions instead of generated answers.
- [First Jev use case in a Mac app](https://x.com/malekoo/status/2100439840575684910) - X: a shipped Mac app routes setup and troubleshooting questions to Jev when no language model is loaded.
- [Jev 中文解读](https://x.com/dotey/status/2100109937237987823) - X (Chinese): explains the System One category to Chinese readers as a calibrated, typed decision layer for code.
- [TypeSafe AI releases Jev (r/singularity)](https://reddit.com/r/singularity/comments/1whop6b/typesafe_ai_releases_ai_model_called_jev_rather/) - Reddit: launch thread framing Jev as a low-hallucination, low-cost decision model for software rather than chat.
- [Testing Jev for Pi extensions (r/PiCodingAgent)](https://reddit.com/r/PiCodingAgent/comments/1whsav6/anyone_else_testing_out_typesafe_ais_new_system/) - Reddit: builders describe using Jev as an agent tool-use safety layer and planning a prompt-complexity model router.
- [Jev "playing" Minecraft (r/accelerate)](https://reddit.com/r/accelerate/comments/1whk9oy/new_typesafe_ai_jev_model_playing_minecraft_wip/) - Reddit: work-in-progress demo of Jev driving Minecraft, including fleeing zombies at night, as a test of fast structured decisions.
- [Awesome Jev by TypeSafe](https://github.com/Anil-matcha/awesome-jev-by-typesafe) - Curated list: a peer collection of Jev use cases, patterns, prompts, and starter code, with a video walkthrough of eight projects people already built.
- [Jev on OpenRouter](https://x.com/OpenRouter/status/2100744709589316009) - X: OpenRouter ships Jev in beta, exposing the System One model through its routing layer.
- [Jev on Cloudflare AI Gateway](https://x.com/CloudflareDev/status/2100688880798159254) - X: Jev goes live on Cloudflare's AI Gateway, callable from Workers.
- [Jev for instant compaction](https://x.com/tamarajtran/status/2100694549362553153) - X: argues agent context compaction should be a Jev decision rather than a summarization prompt.
- [Reviewing unnecessary tool calls with Jev](https://x.com/altryne/status/2100739055923425589) - X: a Claude plugin asks Jev to review redundant tool calls, running in about a second.
- [19 open-source Jev projects](https://x.com/GoSailGlobal/status/2100859307671855113) - X (Chinese): tallies 19 open-source Jev projects totalling more than 6,800 stars.
- [Jev is the fish at the poker table](https://backnotprop.com/blog/jev-poker/) - Blog: plays poker with Jev and uses the table to probe where a fast decision model helps and where it does not.
- [Jev is about to change the AI economy](https://thefinancialengineer.substack.com/p/typesafes-jev-is-about-to-change) - Substack: argues that cheap calibrated decisions move where inference spend goes.
- [Awesome Jev by 0xLogicrw](https://x.com/0xLogicrw/status/2100478725393686556) - X (Chinese): a hand-checked list of Jev projects published one day after launch, one of several community indexes that appeared within 48 hours.
- [Jev repository roundup (Japanese)](https://x.com/studio_yebisu/status/2100686990090047569) - X (Japanese): rounds up the Jev repositories with the most practical promise, observing that computer use and automated trading dominate the early use cases.
- [Six things I'll still use Jev for](https://x.com/isaac_flath/status/2100623016644223175) - X: a practitioner lists the six Jev uses he still expects to rely on after 60 days, an early usefulness review rather than a launch reaction.
- [WTF is Jev, ELI5](https://x.com/mvanhorn/status/2100761338918363550) - X: frames Jev as "AI multiple choice, not AI essay writing", one of the clearer plain-language explanations of the System One shape.
- [深入解读 Jev 模型：毫秒级判定与工程边界](https://github.com/kuhung/understanding-jev) - Chinese deep-dive: examines Jev's millisecond judgments and, more usefully, where its engineering boundaries lie.
- [Has anyone tried Jev as a relevance filter for RAG?](https://reddit.com/r/AI_Agents/comments/1wjpgbx/has_anyone_tried_jev_as_a_relevance/) - Reddit: builders ask whether Jev works as a retrieval relevance filter and reranker, probing the boundary the reported negative reranking result already hinted at.
- [Can we have Jev in Devin?](https://reddit.com/r/DevinAI/comments/1wjtmwi/can_we_have_jev_in_devin/) - Reddit: users of another coding agent ask for a Jev decision layer inside their tool, a signal that typed decisions are becoming an expected feature.
- [All the coolest Jev projects on X](https://x.com/moritzkremb/status/2100895894287839255) - X: a curated thread of the strongest Jev projects posted within 72 hours of launch, by a builder who also produced the most-watched Jev tutorial.
- [Full Jev tutorial](https://x.com/moritzkremb/status/2100715237267660873) - X: a walkthrough covering the API, then three demos — voice-controlled browsing, AI memory, and YouTube preprocessing.
- [WTF is Jev, and the 9 things people are building with it](https://x.com/mvanhorn/status/2100788572316139655) - X: the most widely shared explainer of the launch window, framing Jev as "AI multiple choice, not AI essay writing" and cataloguing nine use patterns.
- [Jev is a really smart switch statement](https://x.com/NathanFlurry/status/2100036101809619314) - X: the hype-free framing from an infrastructure founder — Jev does not replace GPT or Claude, it is a very good switch statement with 2026 intelligence.
- [Arbitrary classification as a type-safe primitive](https://x.com/cocktailpeanut/status/2100277062309179521) - X: argues the real novelty is not classification but that Jev makes arbitrary classification a runtime-defined, type-safe programmable primitive.
- [This is a terrible compaction strategy](https://x.com/theo/status/2100762304862384257) - X: the strongest public pushback on the popular compaction idea, arguing compaction is reconstruction rather than filtering and that the plugin misunderstands context management.
- [It is the inference technique, not the training](https://x.com/anderslie/status/2100388704644919662) - X: argues Jev's speed comes from parallel decoding rather than model training, and that an inference engine can expose a Jev-like API over any open-weight model.
- [Jev's Architecture Unmasked](https://x.com/iwashi86/status/2100713337436930288) - X (Japanese): notes from a technical analysis that inferred Jev's internals from roughly 10,000 API calls, concluding it keeps LLM knowledge but removes token generation entirely.
- [An internal Jev study session with 50+ engineers](https://x.com/LayerX_tech/status/2100887864594895154) - X (Japanese): a company ran an emergency internal study session on Jev and published the material — an early example of organisational adoption rather than individual experimentation.
- [X is all over it, Reddit is not](https://x.com/0xBOYD/status/2100619702003208701) - X: observes a sharp platform divide, finding only three Jev posts on Reddit while X filled with working prototypes — a useful reminder that channel coverage changes the picture.
- [Five open Jev replicas worth trying](https://x.com/xiaomovps/status/2100923960493818177) - X (Chinese): rounds up Laya 421M, Decider-2B, NanoJev 0.6B, Reflex, and System-One 4B as the most promising open decision models, two of which are Mac-friendly.
- [jev(): a PostgreSQL extension for natural-language queries](https://x.com/iam_zachi/status/2100679300756435135) - X: a single SQL function that searches a whole database in natural language with no index and no embeddings, e.g. `WHERE jev(people, 'could work from home')`.
- [A DuckDB extension for row classification](https://x.com/hamiltonulmer/status/2100370557405667768) - X: classifies rows in any CSV, Parquet, or DuckDB table with Jev, reporting about ten seconds for a thousand rows and better ergonomics than a bespoke classifier.
- [An on-chain trading bot where Jev decides](https://x.com/jarrodwatts/status/2100356151468585346) - X: Jev decides buy or sell from a live price feed and the bot places real orders on Monad every 300 ms block — the clearest sign that the finance experiments are not all paper.
- [Jev broke our WebMCP benchmark](https://x.com/0xidanlevin/status/2100937437325205568) - X: the benchmark's own author reports that Jev plus a fast small LLM solved 100% of WebMCP tasks at roughly 112x lower model cost than a frontier model with computer use.
- [Chinese notes after a day with Jev](https://x.com/jiayuan_jy/status/2100876273061102006) - X (Chinese): a sceptical read — Jev looks like a faster general classifier an LLM could already do, and on complex scenarios its world knowledge is the open question.
- [Stagehand plus Jev browser control](https://x.com/kylejeong/status/2100622054945095934) - X: sends the accessibility tree as state and candidate actions as questions so Jev decides each step, reporting about $0.001 and near-instant execution for one task.
- [Introducing CUA-S1](https://x.com/trycua/status/2101014004927729737) - X: Cua open-sources a family of small, specialised System One models for computer use, starting with form filling and asking what the next specialist should learn.
- [One 50 ms pass versus 23 turns](https://x.com/be_arsh/status/2101026864341164110) - X: the sharpest framing of the specialist case - a 706K-parameter model fills a whole form in one 50 ms pass, while an LLM agent needs 23 turns and 39.6 seconds for the same form.
- [I reviewed 287 open-source Jev projects](https://reddit.com/r/LLMDevs/comments/1wko2e5/i_reviewed_287_opensource_jev_projects_here_are/) - Reddit: a reviewer works through 287 Jev repositories and narrows them to 20 that actually explain the model, a useful counterweight to star-count browsing.
- [TypeSafe AI's Jev Is Not an LLM - and That May Be the Point](https://forkast.news/typesafe-ais-jev-is-not-an-llm-and-that-may-be-the-point/) - News analysis: treats the model's refusal to generate text as the feature rather than a limitation, and follows through on what that implies for inference spend.
- [Ask HN: What do you think of Noul, a new decision primitive](https://news.ycombinator.com/item?id=49760225) - Hacker News: a proposal to treat `Noul` - the probability-of-true answer type - as a general software primitive rather than a Jev-specific one.

## Submission format

Use exactly one line per entry:

```md
- [Name](URL) - Industry: one-sentence description of the Jev use case.
```



## License

MIT
