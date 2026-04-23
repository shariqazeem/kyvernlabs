# KyvernLabs — Stellar/Pulse side (legacy submission)

⚠️ **This is NOT the Colosseum Frontier codebase.** If you're working on the Kyvern hackathon build, you're in the wrong directory — go to:

```
~/projects/myowncompany/kyvern-atlas/
```

That repo (github.com/shariqazeem/kyvern-atlas) is the active work. Start by reading its `CLAUDE.md`.

---

## What THIS repo is

- **Repo:** `github.com/shariqazeem/kyvernlabs` (single remote `origin`)
- **Product:** Pulse — x402 revenue analytics dashboard, the team's Stellar Hacks submission
- **Domain served:** `https://kyvernlabs.com` (root) — NOT `app.kyvernlabs.com` (that's Kyvern)
- **Current HEAD on main:** `eabd252` "Production hardening: Stellar mainnet, Solana, x402-native billing"
- **State:** frozen. No active work here. The team pivoted to Kyvern (single-brand agent policy layer on Solana) for Colosseum Frontier and moved all new work to the `kyvern-atlas` repo.

---

## VM deploy (if you ever need to touch this)

**SSH:**
```bash
ssh -i ~/Documents/ssh-key3.key ubuntu@80.225.209.190
```

**pm2 process:** `kyvernlabs` (id 4), port 3000, cwd `/home/ubuntu/kyvernlabs/`

**DO NOT deploy Kyvern code here.** Before any `pm2 restart kyvernlabs`, verify:
```bash
ssh ... 'cd ~/kyvernlabs && git log -1 --oneline'
```
Should show `eabd252` (Stellar). If it shows a Kyvern commit, STOP and fix:
```bash
ssh ... 'cd ~/kyvernlabs && git checkout eabd252 && npm install --legacy-peer-deps && npm run build && pm2 restart kyvernlabs'
```

---

## Why two separate repos?

The project started as KyvernLabs = Pulse (x402 revenue analytics for service providers). That submission went to Stellar Hacks. For Colosseum Frontier, the team pivoted hard to a different product — Kyvern, an on-chain agent policy program on Solana. Same domain umbrella (kyvernlabs.com), completely different code, different narrative, different repo, different pm2 process, different subdomain.

Keeping them fully separated (different repos, different local directories, different pm2 processes, different subdomains) prevents accidental cross-contamination during deploys. They only share the company brand and the VM.

For the Kyvern/Frontier work, go to `~/projects/myowncompany/kyvern-atlas/`.
