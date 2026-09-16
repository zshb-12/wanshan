# Wanshan

A small playground repository used to try out **automated README translation** with GitHub Actions.

## Why this repository exists

Writing and maintaining README documents in several languages is repetitive work. This repository
uses the [`Auto Translate Readme`](https://github.com/marketplace/actions/auto-translate-readme)
action so that a single English source file is enough.

## How it works

1. Edit `README.md` in English and push the change.
2. The workflow in `.github/workflows/translate.yml` starts automatically.
3. A generative AI model translates the file and commits `README.zh-CN.md` and `README.zh-TW.md`.
4. The generated files are pushed back to this repository under a commit named `Auto-translate README`.

## Translation engines

The action supports three back ends:

| Engine | Cost | Notes |
| --- | --- | --- |
| `g4f` | Free | Default. No API key required. Availability can vary. |
| `zhipuai` | Free tier | Requires a Zhipuai API key stored as a repository secret. |
| `openai` | Paid | Uses `gpt-4o`. Requires an OpenAI API key stored as a repository secret. |

This repository currently runs on the free `g4f` engine, so no API key is configured.

## Files in this repository

- `README.md` - the English source document, edited by hand.
- `README.zh-CN.md` and `README.zh-TW.md` - generated automatically, do not edit by hand.
- `.github/workflows/translate.yml` - the workflow definition.

## Caveats

Machine translation is not perfect. Read the generated files before publishing them, and prefer
reviewing changes on a branch before merging them into the main branch.