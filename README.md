# Alish Karki

**Systems & AI engineer.** I build the unglamorous layer — CPU inference engines, hand-tuned SIMD kernels, and the developer tools that make them usable.

- **Nepal** · [pulseonix.xyz](https://pulseonix.xyz) · [LinkedIn](https://www.linkedin.com/in/alish-karki-48b625244)
- Part of **[PulseOnix](https://pulseonix.xyz)** — a collective of developers and researchers building AI systems, CPU inference engines, SIMD libraries, and developer tools.
- Open to software engineering roles.

---

## What I build

| | |
|---|---|
| **Inference** | CPU LLM inference in C99 — plugin architecture, quantized KV cache, OpenAI-compatible API |
| **Kernels** | Hand-tuned SIMD for dot product, L2, and cosine similarity — SSE2 → AVX-512 → NEON |
| **Tooling** | Multi-account Hugging Face management over CLI and MCP, with OAuth device flow |
| **Data** | Financial-aid intelligence for students the admissions funnel overlooks |
| **Applied** | Agronomic telemetry and anomaly detection for greenhouses and indoor grows |

## Featured work

### PRISM — plugin-based CPU LLM inference engine

`C99` · `MIT` · [wraithen0/prism](https://github.com/wraithen0/prism)

Everything is a plugin: kernels, model architectures, tokenizers, samplers, the generation loop, and the frontend. Swap any of them at runtime from config.

- llama2.c-style loading with GGUF checkpoints (F32 / F16 / Q8_0 / Q4_0 / Q6_K) and GQA attention
- OpenAI-compatible API — SSE streaming, chat templates, auth, rate limiting, optional TLS
- Quantized KV cache, response cache, 21 test suites
- Ships with a prebuilt AVX2 Linux runtime alongside the source

### vek — hand-tuned SIMD vector similarity kernels

`C` · `MIT OR Apache-2.0` · [wraithen0/vek](https://github.com/wraithen0/vek)

The hot loops powering vector search, embeddings, and RAG pipelines.

- Zero dependencies, single header + source tree, vendors cleanly into any build
- Runtime CPU dispatch — one binary, optimal SIMD chosen at startup (SSE2, AVX2, AVX-512F/VNNI/VPOPCNTDQ, NEON)
- f32, f16, bf16, int8, uint8, and 1-bit binary vectors
- Neumaier compensated summation — no catastrophic cancellation in f32 dot products
- Stable C ABI, callable from C, C++, Rust, Zig, Go, Python
- Stack-only hot path, no heap allocation, scalar fallback always compiled

### hfm — multi-account Hugging Face manager

`Python` · `MIT` · [wraithen0/hfm](https://github.com/wraithen0/hfm)

One CLI and one MCP server for every Hugging Face account, repo, and Space.

- OAuth device flow — no tokens pasted into dotfiles, stored `0600`, auto-refreshed
- `pipx install hfm`; the MCP server exposes the same operations to AI agents over stdio
- Read-only mode and an audit log as safety rails for agent access

### SRA — Student Resource Architecture

`Python` · [wraithen0/SRA](https://github.com/wraithen0/SRA)

College and university discovery with financial-aid intelligence, engineered for three student profiles the admissions funnel overlooks: first-generation students, students requiring accommodations, and international STEM students.

- Cache-first from local SQLite — never re-scrapes a live site on request
- Ranked institutions with match scores, "why" signals, and explicit unverified gaps
- Deadline, FAFSA/CSS, and fee-waiver extraction, plus step-by-step action playbooks
- Zero-dependency embedded mode, optional FastAPI sidecar

### GrowSense — agronomic telemetry

`TypeScript` · [wraithen0/growsense](https://github.com/wraithen0/growsense)

AI-powered environmental telemetry for precision growing — soil moisture, temperature, humidity, and luminous flux translated into plain-language guidance.

- TanStack Start / React 19 on Cloudflare D1 + Workers, Bun toolchain
- Hardware-agnostic ingest API (ESP32, Raspberry Pi, Arduino) plus a built-in stress simulator
- Species-specific anomaly detection and diagnostics

### Kestrel — consequence-driven learning

`Python` · *research — not yet public*

An agent that learns hidden rules purely from experience — no corpus, no pretraining — across six phases from tabular world models to self-modifying exploration. CPU-based; source and benchmark methodology not yet released.

## How I work

- **Kernels first.** When I need a hot loop, I write it and benchmark it rather than reaching for a dependency.
- **Correctness before speed.** Scalar fallbacks are always compiled; the SIMD path is an accelerator, never a requirement.
- **Tools for agents, not just humans.** `hfm` exists because agents need the same access humans do — with guardrails.
- **Ship the whole thing.** PRISM ships source *and* a prebuilt runtime; `vek` ships headers, benchmarks, and tests.

## Note on the mirrored repos

[`veyyon`](https://github.com/wraithen0/veyyon) and [`models.dev`](https://github.com/wraithen0/models.dev) are unmodified forks of upstream projects, kept for local use and reference. They are not original work of mine.
