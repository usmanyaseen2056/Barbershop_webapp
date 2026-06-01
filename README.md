# TrimGo

Production-grade full-stack architecture for an Uber-style on-demand barber platform.

## Stack

- Frontend: Next.js (App Router), React, Tailwind CSS, Framer Motion, GSAP
- Backend: Node.js, Express, Socket.io, JWT auth, RBAC, Zod validation
- Database: PostgreSQL + Prisma ORM

## Monorepo Structure

- `apps/frontend` - customer/barber/admin web app
- `apps/backend` - REST + realtime API service

## Features Included

- Role-ready auth flow (`CLIENT`, `BARBER`, `ADMIN`)
- Booking APIs and listing
- Real-time barber bidding events (Socket.io)
- Live chat and tracking socket channels
- Reviews and ratings API
- Payment intent API scaffold (Stripe/JazzCash adapter point)
- Admin metrics endpoint
- Live map integration component (Google Maps)
- Premium dark UI scaffold with glassmorphism and animations

## Environment

Copy these files and fill values:

- `apps/frontend/.env.example` -> `apps/frontend/.env.local`
- `apps/backend/.env.example` -> `apps/backend/.env`

## Install

Run per app (recommended when disk is constrained):

1. `cd apps/backend && npm install`
2. `cd apps/frontend && npm install`

Then from root:

- Backend dev: `npm run dev:backend`
- Frontend dev: `npm run dev:frontend`

## Test

From root:

- `npm test` - backend API tests (health, 404, auth validation)
- `npm run test:frontend` - production build check for frontend
- `npm run test:all` - backend tests + frontend build

From `apps/backend`:

- `npm test`
- `npx prisma generate` (required before first run)

## Prisma

Inside `apps/backend`:

1. `npx prisma generate`
2. `npx prisma migrate dev --name init`

## Deployment

- Frontend deploy target: Vercel (`apps/frontend`)
- Backend deploy target: Railway or Render (`apps/backend`)
- Set env vars for both services
- Point `NEXT_PUBLIC_API_BASE_URL` to deployed backend URL
