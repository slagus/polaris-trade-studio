# Polaris Trade Studio

An ultra-low-latency, dual-themed options scalping dashboard and execution client designed for high-frequency index trading (focused on Nifty 50). Built with an event-driven architecture to process real-time tick feeds, render dynamic entry/target/loss price shading, and route orders safely with instant paper/live execution mode switching.

## Key Features

* **Real-time Charting:** Powered by Lightweight Charts v5 with baseline data injection and dynamic target/stop-loss price line plugins.
* **Paper / Live Router:** Isolated execution engine with real-time paper trading simulation and Upstox REST API integration.
* **Decoupled Signal Architecture:** Consumes trading signals asynchronously via Redis Pub/Sub, keeping the user interface completely independent of strategy logic.
* **Dual-Theme UI:** High-contrast dark and light themes optimized for dynamic trading environments.

## System Architecture
```text
┌─────────────────────────────────────────────────────────────┐
│                    polaris-trade-studio                     │
│                                                             │
│  ┌───────────────────────┐       ┌───────────────────────┐  │
│  │ React (Vite) Frontend │ ◄───► │ Node.js Engine & WS   │  │
│  └───────────────────────┘       └───────────┬───────────┘  │
└──────────────────────────────────────────────│──────────────┘
                                               │
                                               │ Subscribes:
                                               │ "scalp_signals"
                                               ▼
                                    ┌─────────────────┐
                                    │  Redis Pub/Sub  │
                                    └─────────────────┘
```

## Tech Stack

* **Frontend:** React (Vite), Lightweight Charts v5, Tailwind CSS
* **Backend:** Node.js, Express, WebSockets, Redis Pub/Sub
* **Broker Data:** Upstox v2 API / WebSockets

## License

This project is licensed under the [MIT License](LICENSE).
