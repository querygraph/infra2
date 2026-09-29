# AI Infra 2.0 Manifesto
---

**What is AI Infra 2.0?**

AI Infra 2.0 is a shared foundation: startups, advanced developers, and enterprises building a common infrastructure for AI compute and data.

Today AI infrastructure is fragmented. Our data lives in lakehouses, streaming systems, RAG stores, and graph databases, and none of them speak the same language. Agents trade slow JSON, serializing and deserializing at every hop, when they could be passing Apache Arrow batches with zero copies. It's impedance mismatch everywhere.

Take the most common case: a Python agent talking to a JVM-based lakehouse engine. Every call crosses the JVM boundary, and then crosses back. Amdahl's law is unforgiving here. However much you speed up the engine, the boundary tax caps your gains.

**What we propose**

Look at what the best new infrastructure is actually shipping. It's converging on the same shape: **Python on top, native code underneath.** Think of an iceberg. Python is the tip that developers touch. Rust is the mass below the waterline: execution, validation, security, and data movement. **Apache Arrow** is the shared data bus that lets these systems exchange data without copying or converting it, and **Apache DataFusion** has become a common engine for building on it.

When the engine is native and the data format is shared, the boundary disappears. There's nothing to cross. Amdahl's law works *for* us.

AI is only as good as the data you can feed it. Native, Arrow-first infrastructure keeps up with the massive compute being built for AI.

**This is already happening**

On July 27, 2026, ten teams presented at **Rust AI Begins** at AWS Builder Loft in San Francisco. They included startups, open-source projects, and enterprises. None of them argued that every AI system should be rewritten in Rust. They showed something more concrete: Rust is becoming the layer under the interfaces developers already use. On September 9, Rust.ai came to Amsterdam. Our message resonates as more and more companies choose to build fast, interoperable AI Infra 2.0 powered by Apache Arrow, Apache DataFusion, ADBC, and other Rust/Zig/C++/native frameworks.

The talks covered every layer of the AI data stack:
- lakehouse execution
- streaming
- context engines
- key-value stores
- semantic layers and security
- table formats
- connectivity
- durable agent workflows
- graph retrieval
- Python concurrency

Rust isn't one product category inside AI. It's showing up across the whole foundation. The teams that presented are listed at the end.

**The principles**

It doesn't have to be Rust. It can be any native code, and it should speak Apache Arrow. The point is thoughtful software engineering:

- **Type-safe.** Correctness is enforced, not hoped for.
- **High quality, secure, and verifiable.**
- **Fast by definition.** Native compute, zero-copy data.
- **Python-compatible.** Meet developers where they already are.

**Join us**

Read the manifesto. Sign it. Come speak at **Rust AI**. We started in San Francisco, we've just launched in Amsterdam, and we're bringing the AI Infra 2.0 community to a city near you.

If you're building in this ecosystem, come show what you've built, and interop with us. The network effects of this ecosystem are the next level.

---

**Signed by Companies and Developers** *(chronological)*

- **LakeSail**: Sail, a Spark-compatible lakehouse engine in Rust with no JVM, built on Arrow and DataFusion.
- **LaserData**: real-time streaming on Apache Iggy, a Rust-native engine using thread-per-core execution, io_uring, and zero-copy serialization.
- **CocoIndex**: a Rust context engine that keeps AI indices and knowledge graphs in sync as the source data changes.
- **Columnar**: ADBC, Arrow-native database connectivity for agents, in place of row-oriented APIs.
- **Databricks**: delta-kernel-rs, a shared Rust kernel for the Delta Lake protocol, used by DuckDB, Polars, DataFusion, and other engines.
- **Eventual**: Daft, running Python coroutines on a Rust Tokio runtime through PyO3.
- **Polygres**: pgGraph and pgContext, cache-conscious graph traversal and retrieval inside PostgreSQL.
- **QueryGraph**: a semantic layer with type-level security (TypeSec).
- **Temporal**: a durable agent loop in Rust that survives redeployment.
- **Valkey**: the GLIDE client core, a Rust SDK for modules, and Valkey-Bloom.
- **Ladybug**. an Arrow-first graph database, disk format and memory.
