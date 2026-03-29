# 🌟 SocialBonds  
**Create bonds, make promises, spread rumors – bring your roleplay server to life!**

[![Paper](https://img.shields.io/badge/Paper-1.20+-blue?logo=paper)](https://papermc.io/)
[![Java](https://img.shields.io/badge/Java-21-orange)](https://adoptium.net/)
[![Version](https://img.shields.io/badge/version-1.1-brightgreen)](https://github.com/toplesssss/SocialBonds/releases)
[![Downloads](https://img.shields.io/github/downloads/toplesssss/SocialBonds/total)](https://github.com/toplesssss/SocialBonds/releases)

---

## 📖 Table of Contents

- [About](#-about)
- [Features](#-features)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Commands & Permissions](#-commands--permissions)
- [PlaceholderAPI Support](#-placeholderapi-support)
- [Database Setup](#-database-setup)
- [Building from Source](#-building-from-source)
- [Support](#-support)

---

## 🧐 About

**SocialBonds** is a Minecraft plugin designed to enrich roleplay servers by creating meaningful interactions between players – **without introducing new items or blocks**. It focuses on visual and social mechanics that encourage players to communicate, form relationships, and build a living world.

**Key Highlights:**
- Fully asynchronous database operations – no server lag.
- Built-in **English** and **Russian** translations. Easily add your own language.
- **PlaceholderAPI** support with 15+ placeholders.
- Lightweight, no extra items or resource packs required.

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🤝 **Gestures** | Use `/wave`, `/bow`, `/handshake`, etc. Mutual gestures create heart particles and increase sympathy. |
| 📜 **Promises** | Make promises (`/promise give <player> <text>`), mark them done, and confirm. Reputation rewards for keeping your word. |
| 👥 **Bonds & Sympathy** | Every interaction strengthens bonds. View all relationships in a GUI (`/bond`). |
| 🗣️ **Rumors** | Spread rumors about other players (`/rumor create <player> <text>`). The community votes; outcomes affect reputation. |
| ⭐ **Reputation System** | Reputation rises/falls based on promises kept, rumors, and social behavior. |
| 🏆 **Titles** | Earn titles automatically (“Trustworthy”, “Oathbreaker”, “Silver Tongue”) displayed above your head. |
| 🎨 **Visual Effects** | Particles, sounds, and animations bring every interaction to life. |
| 🖥️ **Intuitive GUI** | Simple GUIs for bonds, promises, and rumors. |
| 🌍 **Multilingual** | Built‑in English & Russian. Add your own language file easily. |
| 📊 **PlaceholderAPI** | Full set of placeholders for reputation, titles, stats, and even sympathy with specific players. |
| ⚙️ **Configurable** | Everything from cooldowns to reputation gains is adjustable. |

---

## 📦 Installation

1. Download the latest `SocialBonds-1.1.jar` from the [Releases](https://github.com/toplesssss/SocialBonds/releases) page.
2. Place it in your server’s `plugins/` folder.
3. Restart your server.
4. Edit `plugins/SocialBonds/config.yml` to set your language and other options.
5. (Optional) For MySQL, set `database.type: mysql` and fill in your credentials.

---

## ⚙️ Configuration

### `config.yml`

# Language (en, ru, or your own)
language: en

database:
  type: sqlite  # or mysql
  sqlite-file: plugins/SocialBonds/data.db
  # mysql settings (if type=mysql)
  host: localhost
  port: 3306
  name: socialbonds
  user: root
  password: ""

gestures:
  max-distance: 10
  response-timeout: 5
  cooldown-per-pair-minutes: 1
  sympathy-gain: 1

promises:
  max-active: 5
  cooldown-minutes: 10
  default-deadline-days: 7
  reputation-gain-on-fulfill: 5
  reputation-gain-on-confirm: 1
  reputation-loss-on-break: 10

rumors:
  max-per-day: 1
  rumor-lifetime-days: 7
  votes-required: 5

titles:
  update-interval-minutes: 60

limits:
  reputation-changes-per-minute: 1
  sympathy-gains-per-hour: 10

  ### 🌍 Languages

SocialBonds supports **multilingual** messages out of the box. Language files are stored in the `lang/` folder inside the plugin directory.

- **English** – `en.yml`
- **Russian** – `ru.yml`

To add your own language:
1. Copy `lang/en.yml` to `lang/yourlang.yml`
2. Translate all message values (keep the keys unchanged)
3. Set `language: yourlang` in `config.yml`

The plugin will automatically load the selected language on startup or after `/socialbonds reload`. If a key is missing, it falls back to English and logs a warning.

---

## 🔧 Commands & Permissions

| Command | Description | Permission |
|---------|-------------|------------|
| `/bond` | Open your bonds GUI | `socialbonds.use` |
| `/promise` | Manage promises (GUI) | `socialbonds.use` |
| `/rumor` | Manage rumors (GUI) | `socialbonds.use` |
| `/title` | Show your current title | `socialbonds.use` |
| `/wave`, `/bow`, `/handshake`, `/point`, `/nod`, `/facepalm`, `/cheer`, `/cry`, `/angry` | Perform gestures | `socialbonds.use` |
| `/socialbonds reload` | Reload configuration | `socialbonds.admin` |
| `/socialbonds give <player> <title>` | Give a custom title | `socialbonds.admin` |
| `/socialbonds reset <player>` | Reset all social data | `socialbonds.admin` |
| `/socialbonds punish <player> <reason>` | Punish a player (reputation loss) | `socialbonds.admin` |
| `/socialbonds info <player>` | Show player’s social stats | `socialbonds.admin` |

**Default permissions:**
- `socialbonds.use` – granted to all players by default
- `socialbonds.admin` – operators only

---

## 📊 PlaceholderAPI Support

If [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) is installed, SocialBonds provides the following placeholders:

| Placeholder | Description |
|-------------|-------------|
| `%socialbonds_reputation%` | Current reputation score |
| `%socialbonds_title%` | Current title |
| `%socialbonds_bonds_count%` | Number of active bonds |
| `%socialbonds_promises_active%` | Total active promises (sent + received) |
| `%socialbonds_promises_sent_active%` | Active promises you made |
| `%socialbonds_promises_received_active%` | Active promises made to you |
| `%socialbonds_promises_fulfilled%` | Number of promises fulfilled |
| `%socialbonds_promises_broken%` | Number of promises broken |
| `%socialbonds_rumors_about_active%` | Active rumors about you |
| `%socialbonds_rumors_about_confirmed%` | Confirmed rumors about you |
| `%socialbonds_rumors_about_refuted%` | Refuted rumors about you |
| `%socialbonds_rumors_by_active%` | Active rumors you created |
| `%socialbonds_rumors_by_confirmed%` | Confirmed rumors you created |
| `%socialbonds_rumors_by_refuted%` | Refuted rumors you created |
| `%socialbonds_gestures_total%` | Total gestures performed |
| `%socialbonds_sympathy_<player>%` | Sympathy level with a specific player (replace `<player>` with the player's name) |

---

## 🗄️ Database Setup

### SQLite (default)
- No configuration required.
- The database file is stored in `plugins/SocialBonds/data.db`.

### MySQL
1. Create a MySQL database (e.g., `socialbonds`).
2. In `config.yml`, set:
   ```yaml
   database:
     type: mysql
     host: localhost
     port: 3306
     name: socialbonds
     user: youruser
     password: yourpassword
3. Restart the server – tables will be created automatically.

All database operations are performed asynchronously to avoid lag.


Made with ❤️ by Toples
