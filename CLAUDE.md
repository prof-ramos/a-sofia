# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Next.js AI chatbot application called "a-sofia" built with Google Gemini models for flight booking assistance. The application uses modern Next.js App Router architecture with React Server Components and Server Actions.

## Development Commands

- **Development**: `pnpm dev` - Starts development server with Turbo
- **Build**: `pnpm build` - Runs database migrations then builds the application
- **Production**: `pnpm start` - Starts production server
- **Lint**: `pnpm lint` - Runs ESLint with Next.js configuration

## Database Setup

The project uses Drizzle ORM with PostgreSQL (Vercel Postgres):
- **Schema**: `db/schema.ts` - Defines User, Chat, and Reservation tables
- **Migrations**: Run automatically during build via `tsx db/migrate`
- **Config**: `drizzle.config.ts` - Uses `.env.local` for database URL
- **Migration files**: Stored in `lib/drizzle/`

## Architecture

### Core Structure
- **AI Layer**: `ai/` - Contains Gemini model configurations and custom middleware
- **App Router**: `app/` - Next.js App Router with grouped routes
  - `(auth)/` - Authentication pages and API routes
  - `(chat)/` - Chat interface and chat API endpoints
- **Components**: `components/` - Organized into custom, flights, and ui folders
- **Database**: `db/` - Schema, queries, and migrations
- **Lib**: `lib/` - Utilities and database migration files

### Key Components
- **Authentication**: NextAuth.js with credentials provider using bcrypt-ts
- **AI Models**: Google Gemini 1.5 Pro/Flash with custom middleware
- **UI**: shadcn/ui components with Tailwind CSS and Radix UI primitives
- **Styling**: Tailwind CSS with custom Geist fonts and theme support

### Flight Booking Flow
The chatbot implements a specific flight booking workflow:
1. Search flights
2. Choose flight
3. Select seats
4. Create reservation
5. Authorize payment
6. Display boarding pass

### Tools Available in Chat API
- `getWeather` - Weather information via Open-Meteo API
- `displayFlightStatus` - Mock flight status display
- `searchFlights` - Mock flight search results
- `selectSeats` - Mock seat selection interface
- `createReservation` - Creates reservation in database
- `authorizePayment` - Payment authorization flow
- `verifyPayment` - Payment verification
- `displayBoardingPass` - Boarding pass generation

## Environment Requirements

Create `.env.local` with:
- `POSTGRES_URL` - Vercel Postgres database connection
- `AUTH_SECRET` - NextAuth.js secret
- `GOOGLE_GENERATIVE_AI_API_KEY` - Google AI API key

## TypeScript Configuration

- Uses strict TypeScript with ESNext target
- Path aliases configured: `@/*` maps to project root
- Includes Next.js plugin for optimal integration

## UI System

- **Design System**: shadcn/ui with default style
- **Theme**: Zinc base color with CSS variables
- **Components**: Located in `components/ui/`
- **Icons**: Radix UI icons and Lucide React
- **Motion**: Framer Motion for animations