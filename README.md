# Repolex Knowledge Graph of bentoml/llm-optimizer

RDF knowledge graph data for [bentoml/llm-optimizer](https://github.com/bentoml/llm-optimizer), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/llm-optimizer
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7be87d776e60a978516a2ae53e4a4ff745d04c20
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 7be87d776e60a978516a2ae53e4a4ff745d04c20
│           └── chunk-001.nq.gz
├── blob
│   ├── 0c4aa03586d27a5b79465286963a84d9ea2947a6.nq.gz
│   ├── 0d34bc17c58e75dc148c951dc8caacff89b539c2.nq.gz
│   ├── 0d3afe72b5b01930c915d7dc1a4a07a7a78ef0a6.nq.gz
│   ├── 18a573cd4f174a7d393d7b08c6d6d61abb8655b8.nq.gz
│   ├── 1b67f14e045439a5202b50a8e8d7df439e4f0b8b.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2a6273303c79cec9033dd2e5ef579c7fb475d9e5.nq.gz
│   ├── 2f6c7d36426bf14d26a1a9387eed53c4efc411ab.nq.gz
│   ├── 4cc062c502f985128e43614f808a3329b75bb711.nq.gz
│   ├── 4f4d04d92d93b4cf8b9e41bd6fa8c4b8d3adcf67.nq.gz
│   ├── 58686474c64f5eca48555eba081b0ce256a136a2.nq.gz
│   ├── 5a13de9b0415f84ab582e68503d1846aea14933d.nq.gz
│   ├── 5c5d6f7cefda1f8bfd5a4a7f4cee125922c0135c.nq.gz
│   ├── 66e5d86e32475cc37196de8b42ed5f3b0ff8fcdd.nq.gz
│   ├── 6e14fe3c3f3d9cda0b59ccbce46b5c6baa45b638.nq.gz
│   ├── 751244c924c4fd7d08388158d740b60788006bef.nq.gz
│   ├── 78aeb4aa650cfaafa0b006276dad29ed368180bb.nq.gz
│   ├── 8619bd71210f2f66febc1cbe7c299d1fc3bb51a4.nq.gz
│   ├── 8f707c20614b4cea959b22711dc7f8c28e2cb629.nq.gz
│   ├── 90b48041686242f4290537550f59133fde76ed4c.nq.gz
│   ├── 930d4fe83656f647c13461c5bdb35db8db2342c8.nq.gz
│   ├── 9ce9fbfd9ee77a5794b1c217d75db7f2d0307140.nq.gz
│   ├── b03ea18cd7d637d8582626f89b75151673d61c98.nq.gz
│   ├── b47015d50e4a59e1b97905256ca321b6d80a74a5.nq.gz
│   ├── ba28908510c7ca6a1dc6a143a5c2e5d5c39f4fe5.nq.gz
│   ├── c19891d3c21a2a78a3e86ea973587d913fe22120.nq.gz
│   ├── cc7e85d5e5b3508620735c925e082527eb1426a5.nq.gz
│   ├── d670603adc0f290917a1b7e017fe5c0114708f34.nq.gz
│   ├── d7cff5b4a12ef4bd066840e3cc56e663f4a2df40.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e830d8fb5cd5a0dcf681f200f34c0540248994aa.nq.gz
│   ├── f6e62d962d2c11606eb24ce6c29202fd627e6d76.nq.gz
│   ├── fd8d43ac6accb850d14be7a9ec7a25aca74d2f2c.nq.gz
│   └── fed66b935f66f5e836913d76046ab55c6fbe5c3d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 7be87d776e60a978516a2ae53e4a4ff745d04c20.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 42 files
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

[bentoml/llm-optimizer](https://github.com/bentoml/llm-optimizer)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
