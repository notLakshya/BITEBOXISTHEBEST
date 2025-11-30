# BITEBOXISTHEBEST

> A React + Firebase delivery/shop demo application showcasing authentication, Firestore-backed data, Redux state management, and Cloud Functions.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![React](https://img.shields.io/badge/React-16.x-blue?logo=react)](https://reactjs.org/)
[![Firebase](https://img.shields.io/badge/Firebase-Firestore-orange?logo=firebase)](https://firebase.google.com/)

---

## Table of contents

- [Project Overview](#project-overview)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Firebase / Environment](#firebase--environment)
- [Scripts](#scripts)
- [Project Layout](#project-layout)
- [Architecture & Design Notes](#architecture--design-notes)
- [Development Tips](#development-tips)
- [Contributing](#contributing)
- [License & Contact](#license--contact)

---

## Project Overview

This repository contains a Create React App front-end with Redux and Firestore integration (`react-redux-firebase` / `redux-firestore`), plus Firebase Cloud Functions in `functions/` for server-side tasks.

Key app flows:

- User authentication (email/password)
- Product listing and details
- Shopping cart + checkout flows
- Orders stored in Firestore
- Server-side functions for trusted operations


## Tech Stack

- React (Create React App)
- Redux + `redux-thunk`
- `react-redux-firebase`, `redux-firestore`
- Firebase: Auth, Firestore, Cloud Functions
- Utilities: `moment`, `react-slideshow-image`, `react-loader-spinner`


## Quick Start

Prerequisites

- Node.js (v12+ recommended for `functions`)
- npm or yarn
- Firebase CLI: `npm i -g firebase-tools`

Install & run

```powershell
# from repository root
npm install
cd functions
npm install
cd ..
npm start
```

Open `http://localhost:3000` in your browser.

Run Cloud Functions emulator (optional):

```powershell
cd functions
npm run serve
```


## Firebase / Environment

- Client Firebase config is in `src/FbConfig.js`. Replace it with your project config when deploying.
- For production, keep sensitive server-side credentials in Firebase project settings or Cloud Functions environment.

Example `.env` (recommended for CI/CD and local overrides):

```ini
REACT_APP_FIREBASE_API_KEY=your_api_key
REACT_APP_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
REACT_APP_FIREBASE_PROJECT_ID=your_project_id
REACT_APP_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
REACT_APP_FIREBASE_MESSAGING_SENDER_ID=...
REACT_APP_FIREBASE_APP_ID=...
```

> Note: Firebase client config is not secret by design; do not put service account keys on the client.


## Scripts

Client (root `package.json`):

- `npm start` — start dev server
- `npm run build` — production build
- `npm test` — run tests
- `npm run eject` — eject CRA config (one-way)

Functions (`functions/package.json`):

- `npm run serve` — run functions emulator
- `npm run shell` — interactive shell
- `npm run deploy` — deploy functions
- `npm run logs` — show logs


## Project Layout

```
.
├─ Public/
├─ src/
│  ├─ Components/
│  │  ├─ Auth/
│  │  ├─ Dashboard/
│  │  └─ Shop/
│  ├─ FbConfig.js
│  └─ index.js
├─ Store/
│  ├─ Actions/
│  └─ Reducers/
├─ functions/
├─ firebase.json
└─ package.json
```

Important files

- `src/FbConfig.js` — Firebase initialization
- `Store/` — Redux actions & reducers
- `functions/` — server-side Firebase functions


## Architecture & Design Notes

- Client initializes Firebase in `src/FbConfig.js` and connects to Firestore using `react-redux-firebase`.
- Redux stores UI state (cart, in-progress flags); Firestore stores persistent data (orders, users, inventory).
- Cloud Functions (Node 12) perform trusted operations such as order processing or integrations.
- UI follows small, focused components and keeps side-effects inside actions or functions.

Suggested improvements

- Move client config to environment variables for CI/CD.
- Add tests for reducers and actions.
- Add CI (GitHub Actions) to run tests & lint on PRs.


## Development Tips

- Use Firebase emulator suite for local end-to-end testing.
- When testing security rules, use the emulator to avoid hitting production data.


## Contributing

1. Fork the repo
2. Create a feature branch
3. Run tests and linters
4. Submit a PR with a clear description


## License & Contact

If you want an explicit license, tell me which one (MIT recommended). For CI or deployment automation, tell me the provider and I can scaffold configs.

---

*Generated: please review `src/FbConfig.js` and replace Firebase values with your own project settings before deploying.*
