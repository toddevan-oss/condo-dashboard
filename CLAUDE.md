# Condo Dashboard — Claude Instructions

## Deploying Changes

This is a single-file static site hosted on GitHub Pages. To push changes live:

```bash
cd "C:\Users\todde\Documents\Condo Dashboard"
git add index.html
git commit -m "describe what changed"
git push
```

The site republishes automatically within ~60 seconds. No build step, no server, no dependencies.

**Always push after making changes** unless the user says they want to review first.

## Repository & Hosting

- **GitHub repo:** https://github.com/toddevan-oss/condo-dashboard
- **Live site:** https://toddevan-oss.github.io/condo-dashboard
- **Branch:** `main`
- **Hosting:** GitHub Pages (static, auto-deploys on push)
- **Git identity configured locally:**
  - `user.name = Todd Evan`
  - `user.email = toddevan@gmail.com`

## Project Structure

Everything lives in a single file:

```
index.html        — the entire app (HTML + CSS + JS in one file)
.claude/
  launch.json     — preview server config (PowerShell-based, port 3001)
  serve.ps1       — PowerShell HTTP server script for local preview
  serve.pl        — Perl HTTP server (fallback)
CLAUDE.md         — this file
```

No package.json, no build tools, no framework. Do not create additional files unless absolutely necessary.

## Property Details

- **Address:** 1110 6th St NE, Unit #2, Washington DC 20002
- **Purchase price:** $850,000 (April 2018, primary residence until 2022)
- **Loan:** Truist, loan #6311573544, 2.875% fixed, matures Oct 2050
- **Monthly payment:** $3,678.68 (P+I + escrow)
  - Principal: ~$1,515
  - Interest: ~$1,555
  - Escrow (taxes & insurance): $608.48
- **Current loan balance:** ~$648,874
- **HOA:** $500/month
- **Maintenance reserve:** $300/month (budgeted)
- **Equity invested (basis):** $118,360.23
- **Current rent:** $4,500/month
- **Lease:** Month-to-month (no fixed end date)

## Dashboard Panels

| Panel | Purpose |
|-------|---------|
| Returns | Equity, NOI, cash flow, cash-on-cash return, charts |
| Valuation | Compare Zillow/Redfin/Compass/owner estimate; pick active one |
| Operating Costs | Fixed monthly breakdown + maintenance expense log |
| Tenant & Lease | Tenant info, lease dates, rent history |
| Scenarios | Sliders to model future sale: appreciation, rent growth, MOIC |

## Data Persistence

User-entered data (valuation estimates, tenant details, expenses) is saved to **browser localStorage** under the key `condo_1110_6th_v1`. This is per-browser and survives page refreshes but is not synced across devices. Pushing new code does not wipe localStorage.

Default/hardcoded values live in the `DEFAULTS` object at the top of the `<script>` block. On first load (or if localStorage is empty), these defaults are used.

## In-Building Comp Sales (1110 6th St NE)

| Date | Unit | Sale Price |
|------|------|------------|
| 2017 | #2 (ours) | $850,000 (purchase) |
| 2019 | #3 | $740,000 |
| Mar 2019 | #4 | $877,000 |
| Sep 2020 | #1 | $756,000 |
| Dec 2021 | #6 | $905,000 |
| 2023 | #5 | $810,000 |

## Maintenance Expense Log (pre-loaded)

| Date | Category | Description | Amount |
|------|----------|-------------|--------|
| 2024-05-21 | Repair | Toilet gasket replacement | $165 |
| 2024-06-01 | Repair | Special assessment — roof | $4,277.61 |
| 2024-07-15 | Repair | Peppermint test (smell in bathroom) | $238 |
| 2023-04-20 | Repair | AC leak — Roto Rooter plumbing | $1,233.10 |
| 2023-05-26 | Repair | AC leak — floor damage | $600 |
| 2023-05-21 | Repair | AC leak — drywall damage | $1,650 |
| 2023-05-28 | Turn Over | Lights, filters, hardware, putty | $63.44 |
| 2023-05-29 | Turn Over | Water filter | $55.63 |
| 2022-04-19 | Appliances | New range (defective original) | $1,334.85 |
| 2022-08-08 | Maintenance | HVAC — Freon top off | $318.98 |
| 2022-06-06 | Maintenance | HVAC — Freon top off | $232.24 |
| 2022-09-27 | Loan | AC replacement (EnerBank) | $7,550 |

## Rent History

| Period | Monthly Rent |
|--------|-------------|
| Apr 2018–2021 | Owner-occupied (primary residence) |
| 2022–2023 | $4,250 (first tenant, investment property) |
| 2024–present | $4,500 (month-to-month) |

## Valuation Notes

- Zillow doesn't expose Zestimate via API — must be entered manually from zillow.com
- Owner's current estimate: $950,000 (Mar 2026)
- Refi appraisal (Sep 2020): $925,000 — basis for 2.875% refi at 80% LTV
- Active valuation source is user-selectable and drives all Returns/Scenario calculations

## Local Preview

The in-chat preview is unreliable on this Windows setup. The simplest way to preview is to open `index.html` directly in a browser (double-click or File > Open). No server needed since there is no backend.
