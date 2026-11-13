# Multilingual AI Telegram Community Bot

A Python starter bot with:
- AI group conversations in the language members use, including Nigerian Pidgin
- Short, isolated in-memory context per Telegram group
- Image generation from `/image` prompts
- `/groupimage` to create an image inspired by recent group discussion
- Optional image requests detected in normal conversation
- Admin toggles for AI chat and image generation

## 1. Create the Telegram bot

1. Open `@BotFather` in Telegram and create a bot with `/newbot`.
2. Copy its token.
3. Add the bot to your Telegram group.
4. In BotFather, use `/setprivacy` and disable privacy mode if you want it to read ordinary group messages.
5. Give it admin permissions only if you want it to use moderation or other admin-only Telegram features. This starter does not implement full moderation.

Telegram privacy mode and group permissions affect which messages the bot can receive. Follow Telegram's current bot rules.

## 2. Configure

Copy `.env.example` to `.env` and fill in:
- `BOT_TOKEN`
- `OPENAI_API_KEY`

Never commit `.env` or publish either key on GitHub. The `.gitignore` file excludes it.

## 3. Run locally

Python 3.10+ recommended.

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
python bot.py
```

## 4. Commands

- `/start`
- `/help`
- `/ask your question`
- `/image describe an image`
- `/groupimage` — creates an image inspired by recent group discussion
- `/setimages on` or `/setimages off` — group admins only
- `/setchat on` or `/setchat off` — group admins only
- `/status`

To chat naturally, mention the bot or reply to one of its messages. Optional automatic chat is controlled by `.env`.

## 5. Important notes

- Image generation uses the OpenAI Images API. API access, model availability, and billing must be enabled for your account.
- Image generation can incur costs. It is disabled in groups by default and has a per-group cooldown.
- The bot does not generate an image for every conversation message. It detects clear image requests only when an admin enables images, or members can use `/image` and `/groupimage`.
- This is a starter project, not a complete clone of ChatFightBot, MajorBuyBot, or MissRose. It does not yet include their full game, crypto-tracking, or moderation systems.
- Settings and conversation context are in memory and reset when the process restarts. Add PostgreSQL/Redis persistence before running at scale.
- Do not use the bot to collect or expose sensitive personal information. Make the bot's AI identity clear to group members.
