# gumroad-subproject-runtime

Cloud cron for ClaudeEarnSelf Gumroad subproject.

## Workflows

- **poll_sales.yml** — hourly,GET /v2/sales,新 sale → GH issue
- **poll_payouts.yml** — daily 09:00 UTC+8,日銷售總額 summary
- **disconnect_detector.yml** — hourly,本機 24h 無 push 觸發 alert
- **market_refresh_weekly.yml** — 週日 09:00 UTC+8,refresh discover/categories HTML snapshot

## Required GH Secrets

- `GUMROAD_TOKEN` — Gumroad API token(view-only scope:`view_sales`)
- `GH_PAT` — GitHub PAT(scope:`repo`,用於開 issue + commit)

## Data layout

```
data/
├── sales/         # poll_sales 輸出
├── payouts/       # poll_payouts 輸出
├── income/        # income_events.log
└── market/        # market_refresh_weekly 輸出
```
