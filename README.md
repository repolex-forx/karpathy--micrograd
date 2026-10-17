# Repolex Knowledge Graph of karpathy/micrograd

RDF knowledge graph data for [karpathy/micrograd](https://github.com/karpathy/micrograd), parsed by [repolex](https://repolex.ai).

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
rlex download karpathy/micrograd
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7bc720e951fe422b8f8814aa5aa1b64121d26b4c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 7bc720e951fe422b8f8814aa5aa1b64121d26b4c
│           └── chunk-001.nq.gz
├── blob
│   ├── 055cf3416090fde13d37ae4420e3286a7dc9652c.nq.gz
│   ├── 30d5d777bd5d0ee7bc91e91bd9f38c9005969f43.nq.gz
│   ├── 3d89960112452062baf36bb13d43a92028fc0f0e.nq.gz
│   ├── 5a5e08179f6f9c2d932d8a4e6659ff685f3a2c69.nq.gz
│   ├── 64115dfc9709b9fbaeb8345af5321e8279f04908.nq.gz
│   ├── 866bb54c19af89964b637ad61b5ec485d9649cf9.nq.gz
│   ├── 87620ac7e74efee566c6ee9d2ed7281ebafb4788.nq.gz
│   ├── 9a483acf981e884d13bf94c48b90d6ff6a80efa4.nq.gz
│   ├── afd82cc573777421cfec2437a402539a82b70203.nq.gz
│   ├── b8c1253167a27bdba9433136d76fe4c5d0503614.nq.gz
│   ├── e0e8e297e34f25f15cf9aa2d15c3975c34451317.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── fce0cac14f3852c9f407db771a90331452609d75.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 7bc720e951fe422b8f8814aa5aa1b64121d26b4c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 21 files
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

[karpathy/micrograd](https://github.com/karpathy/micrograd)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
