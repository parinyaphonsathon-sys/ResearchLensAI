# ResearchLens AI — Production-ready web app

This package turns the prototype into a deployable web application architecture:

- Email/password authentication via Supabase Auth
- Per-user project storage in Supabase Postgres + Row Level Security
- Real scholarly discovery via OpenAlex public API
- Server-side AI analysis endpoint using OpenAI Responses API
- Evidence → Potential Gap → Feasibility → GO/MODIFY/STOP → Research Blueprint
- Project history and reload
- Responsive UI

## What you need to make it public

1. Create a Supabase project.
2. Run `supabase/schema.sql` in Supabase SQL Editor.
3. Copy the Supabase project URL and publishable key into `.env` as `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY`.
4. Create an OpenAI API key and put it ONLY in the server environment as `OPENAI_API_KEY`. OpenAI explicitly says API keys must not be exposed in browser/client code.
5. Deploy this folder to Vercel. Vite projects can be deployed there; Vercel also supports deploying a project by dragging it into Vercel Drop.
6. Add the same environment variables in the Vercel project settings.
7. In Supabase Auth, configure the production site URL and redirect URL for email confirmation/password auth.

## Local test

```bash
npm install
npm run dev
```

## Important production notes

- Do not commit `.env` or API keys.
- Keep Supabase RLS enabled. The included policies ensure users only see their own projects.
- OpenAlex is used for discovery; the app labels results as evidence candidates and does not treat titles/metadata alone as proof of a research gap.
- AI output is decision support, not a substitute for human academic judgment.
- Before a public launch, add rate limiting, abuse protection/CAPTCHA, analytics, error monitoring, privacy/terms pages, and a billing/quota strategy if you expect significant traffic.
