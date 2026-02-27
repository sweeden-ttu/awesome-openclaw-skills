# Agents

## Cursor Cloud specific instructions

This is a curated "awesome list" repository for OpenClaw skills. It contains Markdown content plus `openclaw` as an npm dependency.

### Repository structure

- `README.md` — The curated awesome list (~2,868 skill entries)
- `CONTRIBUTING.md` — Contribution guidelines
- `LICENSE` — MIT License
- `package.json` — npm manifest with `openclaw` dependency

### Dependencies

Run `npm install` to install dependencies (including `openclaw`). The `openclaw` CLI is then available via `npx openclaw`.

### Lint

Run markdown linting with:

```bash
markdownlint README.md CONTRIBUTING.md
```

Most warnings (line-length `MD013`, inline-html `MD033`, table-style `MD060`) are expected for this awesome-list format and can be ignored. Focus on substantive issues like broken link fragments (`MD051`), trailing spaces (`MD009`), and multiple blank lines (`MD012`).

### Link checking

To spot-check links from the list:

```bash
grep -oP 'https?://[^\s\)>"]+' README.md | sort -u | head -20 | while read url; do
  status=$(curl -sL -o /dev/null -w "%{http_code}" --max-time 10 "$url" 2>/dev/null)
  echo "  [$status] $url"
done
```

Note: `clawhub.ai` links may time out or return `000` in sandboxed environments due to network restrictions. GitHub links are the most reliable for validation.

### Contribution workflow

New skills are added as Markdown list entries in `README.md` under the appropriate category section. See `CONTRIBUTING.md` for the entry format and requirements.
