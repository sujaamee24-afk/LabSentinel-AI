# LabSentinel AI

An interactive laboratory safety demo that combines explicitly labeled simulated sensor readings and user-provided incident reports into transparent, rule-based risk assessments.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/labsentinel-ai run dev` — run the LabSentinel AI web app
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/labsentinel-ai/` — LabSentinel AI React dashboard
- `artifacts/api-server/` — shared API service (not used by the demo dashboard)
- `lib/api-spec/openapi.yaml` — shared API contract

## Architecture decisions

- The dashboard is a frontend-only demo; incident history and settings are stored in the browser.
- Risk assessments use transparent configurable rules. No real vision model, LLM, or connected lab sensors are implied.

## Product

Users can review demo sensor trends, assess a scenario, inspect the step-by-step risk reasoning, configure illustrative thresholds, browse incident history, and download a report.

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
