# AGENTS.md — Base44 Dev Environment

## Project Overview
Student Discipline Management System (SDMS) for ETP Nyarurema. A Vite + React + TypeScript frontend-only app. All data persists in browser localStorage (no backend database).

## Setup
- `docker compose -f docker-compose.base44.yml up -d` starts the Vite dev server on port 3000.
- Node 22 image; npm installs deps on container startup, then runs `vite --host 0.0.0.0 --port 3000`.
- No external credentials required to boot. The Gemini AI service is disabled (returns null). The Africa's Talking SMS service has a hardcoded sandbox API key in `services/smsService.ts`.

## Fixes Applied During Setup
1. **index.html**: Removed the esm.sh importmap and added `<script type="module" src="/index.tsx">` — Vite needs a module entry point and resolves deps from node_modules, not importmaps.
2. **components/Cases.tsx**: Fixed missing closing brace on the `.map()` arrow function block body (line ~189). `))}` → `);})}`.

## Login Credentials (seeded defaults)
- Administrator: `administrator@school.edu` / `admin123`
- Staff: `staff@school.edu` / `staff123`

## Verification
- `curl http://localhost:3000/` returns 200.
- Login screen renders with no console errors.
