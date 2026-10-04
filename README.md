# rajib-skill-marketplace

A Claude Code plugin marketplace. Every plugin lives in its own GitHub repo and is referenced here by its HTTPS clone URL (a `url` source), so installs work without SSH keys.

Read the full tutorial: [docs/plugin-marketplace-tutorial.html](docs/plugin-marketplace-tutorial.html) (download it and open it in a browser).

## Use it

```
/plugin marketplace add rajib76/rajib-skill-marketplace
/plugin install hello-plugin@rajib-skill-marketplace
```

## Plugins

| Plugin | Repo | Description |
|---|---|---|
| hello-plugin | [rajib76/hello-plugin](https://github.com/rajib76/hello-plugin) | Starter plugin with a friendly greeting skill |

## Add a plugin

1. Create a GitHub repo containing `.claude-plugin/plugin.json` (plus `skills/`, `commands/`, `agents/`, `hooks/`, or `.mcp.json`).
2. Add an entry to `.claude-plugin/marketplace.json`:

   ```json
   {
     "name": "my-plugin",
     "description": "What it does",
     "source": { "source": "url", "url": "https://github.com/rajib76/my-plugin.git" }
   }
   ```

   Optional: pin a version with `"ref": "v1.0.0"` (tag/branch) or `"sha": "<commit>"`.
3. Validate and push:

   ```
   claude plugin validate .
   git commit -am "Add my-plugin" && git push
   ```

Users pick up changes with `/plugin marketplace update rajib-skill-marketplace`.
