# Docker Compose Practice

A Flask app connected to Redis via Docker Compose. Tracks page visits using a Redis-backed counter. Built as a hands-on practice project for learning multi-container Docker setups.

## What it does

A minimal Flask web server increments a visit counter in Redis every time the root route is hit.

## Run it locally

```bash
docker compose up
```

Then visit `http://localhost:5000`

## Persistence

Redis data is stored in a named Docker volume (`redis-data`), so the visit counter survives container restarts. Without this, Redis data would live only in the container's temporary layer and reset to 0 every time `docker compose down` runs.

## What I learned

- Docker Compose: running multiple containers together with one command instead of separate `docker run`s
- Service-to-service networking by name (Flask connects to Redis using `host='redis'`, no manual IP config)
- Docker named volumes for persistent storage
- Difference between a container's disposable filesystem and a volume's persistent storage
