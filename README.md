# Next.js Supabase Template

Full-stack-ready Next.js template with TypeScript, TailwindCSS, Supabase, and lucide-react icons.

This repository is designed as a clean GitHub template for starting apps with the Next.js App Router and Supabase. Supabase provides authentication, database, storage, and API access, so the project uses one Next.js app at the root instead of separate client and server folders.

## Tech Stack

- Next.js App Router
- React
- TypeScript
- TailwindCSS
- Supabase JavaScript client
- Supabase SSR
- lucide-react
- npm

## Folder Structure

```txt
nextjs-supabase-template/
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   └── auth/
│   │   │       ├── callback/
│   │   │       │   └── route.ts
│   │   │       ├── login/
│   │   │       │   └── page.tsx
│   │   │       └── register/
│   │   │           └── page.tsx
│   │   ├── (protected)/
│   │   │   ├── dashboard/
│   │   │   │   └── page.tsx
│   │   │   └── settings/
│   │   │       └── page.tsx
│   │   ├── error.tsx
│   │   ├── layout.tsx
│   │   ├── loading.tsx
│   │   ├── not-found.tsx
│   │   └── page.tsx
│   ├── components/
│   │   ├── Footer.tsx
│   │   ├── LoadingSkeleton.tsx
│   │   ├── Navbar.tsx
│   │   └── ui/
│   │       └── Icons.tsx
│   ├── constants/
│   │   └── index.ts
│   ├── hooks/
│   │   └── useAuth.ts
│   ├── lib/
│   │   ├── supabase/
│   │   │   ├── client.ts
│   │   │   └── server.ts
│   │   └── utils.ts
│   ├── styles/
│   │   └── globals.css
│   ├── types/
│   │   ├── auth.ts
│   │   └── database.types.ts
│   ├── utils/
│   │   └── index.ts
│   └── proxy.ts
├── supabase/
│   ├── migrations/
│   │   └── .gitkeep
│   ├── README.md
│   └── seed.sql
├── .env.example
├── .gitignore
├── LICENSE
├── next.config.ts
├── package.json
├── postcss.config.js
├── tailwind.config.ts
└── tsconfig.json
```

## Setup

## Use This Template Without Git History

Recommended: click **Use this template** on GitHub, then create a new repository from this template. This gives your new project its own clean history instead of copying this repository's commits.

You can also create a copy without Git history by using `degit`:

```bash
npx degit zekuuu/nextjs-supabase-template my-app
cd my-app
npm install
```

Another option is to download the repository as a ZIP from GitHub, extract it, then run:

```bash
npm install
```

Avoid `git clone` if you do not want this template's Git history or `origin` remote in your new project.

If you already cloned it, remove the old Git history and start fresh:

```bash
Remove-Item -Recurse -Force .git
git init
git add .
git commit -m "Initial commit"
```

Install dependencies:

```bash
npm install
```

Copy the example environment file:

```bash
cp .env.example .env.local
```

Add your real Supabase values to `.env.local`. Do not commit `.env.local` or real secrets to GitHub.

Run the development server:

```bash
npm run dev
```

The app normally runs at:

```txt
http://localhost:3000
```

## Environment Variables

```env
NEXT_PUBLIC_APP_NAME="Next.js Supabase Template"
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
```

- `NEXT_PUBLIC_SUPABASE_URL` is safe to expose to the browser.
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` is safe to expose to the browser when Row Level Security is configured properly.
- `SUPABASE_SERVICE_ROLE_KEY` must never be exposed to client-side code.
- Real secrets belong in `.env.local`, not in GitHub.

## Supabase Setup

Create a Supabase project, then copy your project URL and anon key into `.env.local`.

This template uses:

- `src/lib/supabase/client.ts` for browser/client-side Supabase usage.
- `src/lib/supabase/server.ts` for Server Components, Server Actions, and Route Handlers.
- `src/app/(auth)/auth/callback/route.ts` for the future Supabase Auth callback flow.

Supabase Auth, Database, and Storage are ready to wire in, but this template intentionally avoids full auth UI and business logic.

## Supabase CLI

Install the Supabase CLI locally:

```bash
npm install supabase --save-dev
```

Initialize Supabase configuration:

```bash
npm run supabase:init
```

Start local Supabase services:

```bash
npm run supabase:start
```

Generate database types after replacing `YOUR_PROJECT_ID` with your actual Supabase project ID:

```bash
npm run types:supabase
```

The generated types are written to:

```txt
src/types/database.types.ts
```

If you use local Supabase development, you can also generate types from your local instance later.

## Proxy

Next.js 16 renamed Middleware to Proxy. This template uses `src/proxy.ts`, placed next to `src/app`, as a minimal placeholder for future authentication checks, protected routes, role-based access, and Supabase session handling.

Do not rely on Proxy as the only authorization layer. Re-check sensitive permissions in Server Components, Server Actions, or Route Handlers.

## Development Commands

```bash
npm install
npm run dev
npm run build
npm start
npm run lint
npm run types:supabase
```

## Where To Customize

- Routes: `src/app`
- Pages: files named `page.tsx`
- Components: `src/components`
- Icons: `src/components/ui/Icons.tsx`
- Supabase clients: `src/lib/supabase`
- Auth logic: `src/app/(auth)` and `src/hooks/useAuth.ts`
- Protected app routes: `src/app/(protected)`
- Proxy/auth checks: `src/proxy.ts`
- Database schema and seed data: `supabase/`
- Environment variables: `.env.local`

## Deployment

Vercel is the recommended deployment platform for this template.

Before deploying:

- Add Supabase environment variables in the hosting provider dashboard.
- Never expose `SUPABASE_SERVICE_ROLE_KEY` to client-side code.
- Make sure the production Supabase URL and anon key are configured.
- Configure Supabase Auth redirect URLs for production.

## License

This project is licensed under the MIT License.

## Credits

Created by Zean Kurt G. Balboa
