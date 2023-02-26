# Nuxt3 + Laravel を Docker で構築する

## .env.example から.env を作成する

```bash
cp .env.example .env
```

## コンテナを構築 & 立ち上げる

```bash
docker compose up -d
```

## Nuxt 環境構築

### コンテナに入る

```bash
docker compose exec front bash
```

### Nuxt3 をインストールする

```bash
npx nuxi init . --force
```

### パッケージインストール

```bash
yarn install
```

### 開発環境を立ち上げる

```bash
yarn dev
```

#### 初期構築後 docker-compose.yml を修正する

```yaml
front:
  # command: sh -c "yarn && yarn dev" ←コメント外す
```

## Laravel 環境構築

### コンテナに入る

```bash
docker compose exec app bash
```

### Laravel インストール

```bash
composer create-project --prefer-dist laravel/laravel . "9.*"
```

#### ※git clone 後は`composer install`

```bash
composer install
```

#### ※git clone 後は Laravel の.env をコピーする

```bash
cp .env .env.example
```
