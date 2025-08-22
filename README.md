The Wild Oasis
================

An internal dashboard for managing a (fictional) boutique cabin retreat: bookings, guests, cabins, check‑ins/outs, and daily operations. Built as a focused React + Supabase playground to practice data fetching, optimistic UI flows, charts, and design systems.

Tech at a glance
----------------
* React 18 + Vite (fast dev, ESM build)
* React Router v6 for layout nesting & protected routes
* React Query (@tanstack) for async state & server cache
* Supabase (auth, Postgres, storage)
* React Hook Form for ergonomic forms + validation
* Styled‑components for encapsulated theming & dark mode
* Recharts for lightweight visuals (sales, stay durations)
* date-fns for time math
* react-hot-toast for non-blocking feedback

Core features
-------------
* Email/password auth, signup, profile update, password change
* Cabins CRUD (incl. image upload to Supabase storage)
* Bookings list with pagination, filtering (status, last X days), sorting
* Booking detail panel with derived stats (nights, extras, total)
* Check‑in & check‑out flow with optimistic UI + toasts
* Dashboard metrics (occupancy %, sales, stays length distribution)
* Today’s arrivals / departures activity list
* Reusable table system (head, body, empty state, skeleton/spinner)
* Global dark / light toggle (context + persisted localStorage)
* Defensive error boundary + retry hooks

Getting started
---------------
1. Clone / copy the repo.
2. Install deps:
   ```bash
   npm install
   ```
3. Environment: create a `.env` (or `.env.local`) and move the Supabase credentials there. (Right now the key is hard‑coded; intentionally left visible for early development. Replace before deploying.)
   ```bash
   VITE_SUPABASE_URL=YOUR_PROJECT_URL
   VITE_SUPABASE_ANON_KEY=YOUR_PUBLIC_ANON_KEY
   ```
4. Update `src/services/supabase.js` to read from `import.meta.env`:
   ```js
   // const supabaseUrl = "..."; const supabaseKey = "..."; (remove these)
   export const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
   const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;
   ```
5. Start dev server:
   ```bash
   npm run dev
   ```
6. Open the printed local URL (typically http://localhost:5173).

Scripts
-------
* `npm run dev` – Vite dev server
* `npm run build` – production build to `dist/`
* `npm run preview` – serve the built assets locally

High‑level structure
--------------------
```
src/
  features/        Domain slices (authentication, cabins, bookings...)
  ui/              Generic, styled primitives & layout pieces
  pages/           Route-level containers wiring features together
  services/        Supabase API wrappers & query helpers
  hooks/           Reusable generic hooks (outside click, localStorage)
  context/         Cross-cutting React contexts (dark mode, etc.)
  styles/          Global style & theme tokens
  utils/           Constants + pure helpers
```
