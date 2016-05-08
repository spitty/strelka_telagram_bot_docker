# strelka-bot

Dockerized [`strelka_telegram_bot`](https://github.com/spitty/strelka_telegram_bot).

# Creating Docker image

```
TAG=latest; docker build --no-cache --build-arg TAG=${TAG} -t spitty/strelka-bot:${TAG} .
```

# Usage

1. Generate token for your bot and put it to `strelka_data/token.lst`.
2. Create data-only container for storing bot database and token:
```
docker run -d -v $(pwd)/strelka_data:/strelka_data --name=strelka-data busybox /bin/echo strelka-data
```
3. Start dockerized strelka-bot:
```
docker run -d --volumes-from strelka-data --name strelka-bot spitty/strelka-bot
```

# Run with [Docker Compose](https://docs.docker.com/compose/)
After creating `strelka_data/token.lst` just simply run

```
docker-compose up
```
