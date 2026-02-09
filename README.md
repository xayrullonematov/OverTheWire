# PPD Test Roadmap

This roadmap tracks what is **done**, what is **in progress/needs hardening**, and what is **next** to reach a stable, future‑proof production product.

---

## ✅ Achieved (Core Product)

### Platform & Architecture
- Monorepo structure: **apps/web**, **apps/api**, **apps/bot**, **packages/shared**.
- Dockerized stack with Postgres, API, Web, Bot.
- Alembic migrations + seed data.
- Telegram WebApp auth with JWT.

### Phase 0–3 (Core User Flows)
- **Phase 0**: Project setup, Docker, env templates, Alembic, seed, healthcheck.
- **Phase 1**: Telegram initData verification, JWT, `/api/me`, dev auth (guarded).
- **Phase 2**: Test mode (start, random questions, submit, premium explanation gating, daily limit).
- **Phase 3**: Exam mode (start/answer/submit, timeout handling, results).

### Phase 4–6 (User Growth + Admin)
- **Phase 4**: Marathon mode (spaced repetition + persistence).
- **Phase 5**: Profile + leaderboard (stats, ranking, history).
- **Phase 6**: Admin CRUD (questions add/edit/delete).

---

## ⚠️ Must‑Fix Before “Production‑Ready”

### Production Runtime
- Ensure production deployment uses **build + start** (no dev servers).  
- Validate Docker build output and resource usage.

### Ops & Reliability
- Production guide is written (Nginx + SSL + backups + monitoring), but must be **followed and validated** in a real deployment.
- Confirm monitoring and backup schedule on VPS.

### Security
- Validate `ENVIRONMENT=production` and `NEXT_PUBLIC_ALLOW_DEV_AUTH=false` in production.
- Confirm `ADMIN_TELEGRAM_IDS` is set and access control is enforced.

---

## ✅ Near‑Term Roadmap (Stabilization)

### 1) Deployment Validation (1–2 days)
- Run full prod stack on VPS (compose + Nginx + SSL).
- Validate healthcheck, logs, and DB backups.
- Confirm Telegram WebApp initData works in production.

### 2) QA & Test Coverage (3–5 days)
- Backend tests:
  - exam timeout
  - marathon flow
  - leaderboard scoring + resets
  - admin CRUD permissions
- Frontend tests:
  - exam/test flows
  - persistence across refresh
  - auth + premium gating

### 3) Performance + Ops (2–4 days)
- Add caching or rate‑limiting for leaderboard endpoints.
- Add error tracking (e.g., Sentry).
- Add uptime alerts.

---

## 🚀 Future‑Proof Roadmap (Next 2–6 Weeks)

### Product Growth
- Richer analytics dashboard for admins.
- Badges + achievements.
- Streaks + retention features.
- Offline/low‑connectivity fallback for Telegram WebApp.

### Data / Intelligence
- Category‑level performance reports.
- Adaptive test generation (weak areas first).
- Advanced leaderboard (Elo or weighted scores).

### Scalability
- Background jobs (Celery / RQ) for heavy tasks.
- Redis for caching + session storage.
- Horizontal scaling (API/Web behind load balancer).

---

## ✅ “Done” vs “Next” Summary

### Done ✅
- Core test/exam/marathon flows
- Profile + leaderboard
- Admin CRUD
- Docker + migrations + seed

### Next 🔜
- Full production validation on VPS
- QA test suite coverage
- Monitoring + alerting
- Performance tuning

---

## Owners & Tracking (Suggested)
- **Backend**: auth, DB, marathon, leaderboard
- **Frontend**: UX flows, caching, error handling
- **DevOps**: deploy, monitoring, backups

---

*This roadmap is meant to stay updated as milestones are completed. Use it as the single source of truth for delivery status.*
