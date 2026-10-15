# Деплой Harlem park на Cloudflare Pages (с серверной функцией /api/lead)

## Зачем
GitHub Pages — статика, там `/api/lead` не работает. Cloudflare Pages бесплатный и
умеет выполнять `functions/api/lead.js`, который уже написан.

## Разовая настройка (нужен аккаунт Cloudflare)

1. Регистрация: https://dash.cloudflare.com/sign-up (бесплатно, 1 минута).
2. В терминале в папке `harlem-park-site`:
   npx wrangler login
   npx wrangler pages project create harlem-park --production-branch main
3. Секреты (токен бота и chat_id):
   npx wrangler pages secret put TELEGRAM_BOT_TOKEN
   npx wrangler pages secret put TELEGRAM_CHAT_ID
4. Деплой:
   npx wrangler pages deploy . --project-name=harlem-park --branch=main

Ссылка будет вида https://harlem-park.pages.dev

## Проверка
Открыть сайт, заполнить форму, нажать «Отправить» — в Telegram должно прийти сообщение
«Новая заявка (Harlem park)» с именем, телефоном, авто и услугой.

## GitHub Pages
Репозиторий и воркфлоу не трогаем — публичная демо-ссылка
https://zxcira.github.io/harlem-park-landing/ остаётся рабочей (там форма откатывается
на звонок по tel:, как и сейчас).
