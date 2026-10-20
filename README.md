# Repolex Knowledge Graph of pylint-dev/pylint-sarif

RDF knowledge graph data for [pylint-dev/pylint-sarif](https://github.com/pylint-dev/pylint-sarif), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download pylint-dev/pylint-sarif
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e853fbe8fa1037ae0a6eb7290e906618dcf16d21
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e853fbe8fa1037ae0a6eb7290e906618dcf16d21
│           └── chunk-001.nq.gz
├── blob
│   ├── 2011ef2a2d45547a037111df235b600e70562a99.nq.gz
│   ├── 2915807367657ba540e190040c80f6b11e2a8038.nq.gz
│   ├── 2cda6607094d8ae00d73346d324676762bb8a479.nq.gz
│   ├── 5b2937d0fdd3211a03573711558958744ec8fe5b.nq.gz
│   ├── 71e804c9892090b5877f8b5dbd9a26eb059a07d9.nq.gz
│   ├── 86980ce083a94ae83c021944d9474d6277d894a6.nq.gz
│   ├── d7eadf00428663211d71a3a99740739c2ea70881.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── e82eba4bd80f1c5151638ee77173827910f22dfb.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e853fbe8fa1037ae0a6eb7290e906618dcf16d21.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[pylint-dev/pylint-sarif](https://github.com/pylint-dev/pylint-sarif)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
