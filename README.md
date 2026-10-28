# Repolex Knowledge Graph of explosion/spacy-biaffine-parser

RDF knowledge graph data for [explosion/spacy-biaffine-parser](https://github.com/explosion/spacy-biaffine-parser), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacy-biaffine-parser
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── feb138256095deb5904c284a23330bb24f4daf01
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── feb138256095deb5904c284a23330bb24f4daf01
│           └── chunk-001.nq.gz
├── blob
│   ├── 0a142d384ed606710f83ab04bb9f6bbc260bab0d.nq.gz
│   ├── 0a9a23146a4e2ff0bd3575895643f83969d1a137.nq.gz
│   ├── 0e60278ac19097f3ae5cb41b36b76a4c94578a3a.nq.gz
│   ├── 17fb79668df34f97e3e9b9a3db3104c4da934028.nq.gz
│   ├── 203626de97bfc1e46759880cabbb1ebc7f66db23.nq.gz
│   ├── 20c7a2fbb7babb47097e039ddcca8fc5f5f38d22.nq.gz
│   ├── 2121b583b626f0bbbb1a1873f8b6bc472112288f.nq.gz
│   ├── 224b0d0d079377385021f7c4c0d43cc1256fca6c.nq.gz
│   ├── 346ad55ddd65a7ff03216770ce8eafc36dd3b95f.nq.gz
│   ├── 37b927c081d3788523b0715d06a8efe0c7cf0dbc.nq.gz
│   ├── 424fb2ca88f000b52ee1f3f9bcf86bcc0ab6c971.nq.gz
│   ├── 441476c7952e1dc442153ddd4362279eeb4105a6.nq.gz
│   ├── 47d36dd627eedced2a5d20ee9cd2b0217a3d69fb.nq.gz
│   ├── 4b64ab60beb70b6b140410d82bc1c38fed64c832.nq.gz
│   ├── 64f4807dbab0649262f5ed8c5ee743560ca45ad5.nq.gz
│   ├── 7e6fa5d86538a9aee9853fa95f122c294159bc8d.nq.gz
│   ├── 7e947d0afb85e57a31ce1203ab8cb8e779f468fc.nq.gz
│   ├── 823fc2ec4506ea8261d533105dc90c2db1bd4e5d.nq.gz
│   ├── 92b367632c88cf9326a5ed720990e6ef7c2714b0.nq.gz
│   ├── 9d51900d492653d64a5b8149b7ccf18657894c72.nq.gz
│   ├── a74ab46d013a51bf2b8597755728ee1eeeadc989.nq.gz
│   ├── a81c8ee121952cf06bfaf9ff9988edd8cded763c.nq.gz
│   ├── a8ed2e151673b2e956e4a0fa868f9192217d4b68.nq.gz
│   ├── b24f8ce3c3d24406cc53b3475771e6a8060805f0.nq.gz
│   ├── b2f2d4b8c5fa4481bf16148bcf4f5d47c9d33acb.nq.gz
│   ├── b935c01a45314bd73f0d1c2b0eb204c1b2256491.nq.gz
│   ├── bc8ee389c17fa1bd5100b14bdb94ab6aaa065861.nq.gz
│   ├── be7d97bd9eea491b684da433fd21471d508cd3d3.nq.gz
│   ├── c077dfc5b8da2972e16ad2a2662f065fe56813cb.nq.gz
│   ├── c169bd31ab1e9b05991882d51cacdb227c2d8d79.nq.gz
│   ├── c53ffe3040c370f5b482245f2f94c6caaae1f0a2.nq.gz
│   ├── c725485e8a8b32620c0912f9a2d0c8b82874dc66.nq.gz
│   ├── dfcd123724c752a5660a072349cbfa5417a1678f.nq.gz
│   ├── e487b9f0e5e8cf2a41fd91bbcb5208212c6c3fa4.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ee6266bc4fcc8f851c29976052df10555e53fdaa.nq.gz
│   └── feeca721642f6b881854beaf600a5b39b8ba1f7f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── feb138256095deb5904c284a23330bb24f4daf01.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 44 files
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

[explosion/spacy-biaffine-parser](https://github.com/explosion/spacy-biaffine-parser)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
