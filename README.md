# Repolex Knowledge Graph of sphinx-contrib/scm

RDF knowledge graph data for [sphinx-contrib/scm](https://github.com/sphinx-contrib/scm), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/scm
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 375af7656b6d01a55f935e61610afa14a96a576c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 375af7656b6d01a55f935e61610afa14a96a576c
│           └── chunk-001.nq.gz
├── blob
│   ├── 042c8f79713c19ade417cf69f0451e6066d6c6af.nq.gz
│   ├── 17e745f8b940a3079f7ed0a0805d1a0312686626.nq.gz
│   ├── 20f1a0b863079fb3f187ea659ca8a6db4cbcb4b5.nq.gz
│   ├── 2bec4803c4bdca67d49f2dcb974faae129d6549a.nq.gz
│   ├── 3f0f13cd7a7e33c018c849d7689e33b402ca7b24.nq.gz
│   ├── 416634f5288f7f60a9b9f68eb63afd0bed3443a2.nq.gz
│   ├── 4fdfbbbaa1d6f03412fd345906bcc821ad6b795c.nq.gz
│   ├── 551e212a7d54407a9c99cddbdba4201935a461fa.nq.gz
│   ├── 92c669ee89806e8149b1d8d4b8c3521054a26012.nq.gz
│   ├── 945e941393e42ba377317c200478b5e61f531042.nq.gz
│   ├── a154b316dab465c231a486b426b554556c0333ff.nq.gz
│   ├── a7339aefb4ddf160758bd32ba3b879d1cc7ee3b7.nq.gz
│   ├── ca09957ff9b9fb463660290cdadd219219ae6e9c.nq.gz
│   ├── ccc3829c56cae0db21fefcca10c7e51659d40813.nq.gz
│   ├── e0d364d21e5dbdcf3abc411d644a96db11077ce0.nq.gz
│   ├── e62ec04cdeece724caeeeeaeb6ae1f6af1bb6b9a.nq.gz
│   └── fc4abf0c67b6d60dae0a5c0e55a09737c2be2694.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 375af7656b6d01a55f935e61610afa14a96a576c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 25 files
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

[sphinx-contrib/scm](https://github.com/sphinx-contrib/scm)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
