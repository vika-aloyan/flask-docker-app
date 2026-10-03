# Flask + PostgreSQL в Docker

Двухконтейнерное приложение: Flask API и PostgreSQL, связанные Docker-сетью.
Данные БД хранятся в именованном volume.

## Стек
- Python 3.11, Flask 3
- PostgreSQL 16
- Docker, Docker Compose

## Запуск

    cp .env.example .env
    docker compose up --build -d
    curl http://localhost:5000

## Архитектура
- `web` — Flask, слушает :5000, в сети `appnet`
- `db` — PostgreSQL 16, volume `pgdata`
- `web` ждёт готовности `db` через `healthcheck`

## Эндпоинты
- `GET /` — версия PostgreSQL
- `GET /health` — статус сервиса
