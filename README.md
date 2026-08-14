# Vice Smartphone

**Version: V1.0.0 Beta**

Full-featured smartphone resource for FiveM (Qbox / QBCore).

Resource name: `vice_smartphone`  
Provides: `qb-phone`, `vice_phone`, `qb-smartphone` (legacy compatibility)

---

## JOIN OUR DISCORD FOR SUPPORT

# [discord.gg/U7q7S45UCV](https://discord.gg/U7q7S45UCV)

**Need help installing, configuring the camera, Fivemanage, inventory items, or anything else?**

### → Join the ViceLabs Discord: https://discord.gg/U7q7S45UCV

That is the **only official support channel** for this resource.

- Install help and setup questions  
- Bug reports and screenshots / F8 logs  
- Feature requests and update news  
- Community chat with other server owners  

**Do not open random issues expecting instant fixes without joining Discord first.**  
Post in the support channels with your framework (`qbox` / `qb-core`), inventory, and console errors.

### Discord invite (copy/paste)

```
https://discord.gg/U7q7S45UCV
```

---

## Features

- Phone, contacts, SMS (vMessages), mail
- Camera with Fivemanage upload and Photos gallery
- Banking (Renewed Banking, wasabi, qb-banking, framework fallback)
- Maps with local GTA atlas and GPS waypoints
- Notes, clock, calculator, weather, garage, city services
- Skittle and PicPlace social apps, App World store
- DropIt nearby file share
- Control Center, flashlight, battery, optional PIN, factory reset
- Optional Vice Crime app (activates when a supported gangs resource is running)

## Package contents

| Folder | Purpose |
|--------|---------|
| `vice_smartphone/` | Phone resource |
| `screencapture/` | Screenshot dependency for the camera (provides `screenshot-basic`) |

## Requirements

Required:

- [oxmysql](https://github.com/overextended/oxmysql)
- [ox_lib](https://github.com/overextended/ox_lib)
- `qbx_core` or `qb-core`

Recommended:

- This package’s `screencapture` (camera)
- [Fivemanage](https://fivemanage.com) API key for photo hosting
- `ox_inventory` or qb-inventory (phone item)
- `pma-voice` (calls)
- `xsound` (optional ringtone boost)

## Installation

1. Copy both folders into your server resources, for example:

```
resources/[vice_smartphone]/vice_smartphone
resources/[vice_smartphone]/screencapture
```

2. Import the database schema once:

```
vice_smartphone/sql/install.sql
```

This recreates all `vice_phone_*` tables. Existing phone numbers in player metadata are kept.

3. Add the phone item (see `vice_smartphone/install/items.md`).

4. In `server.cfg`:

```cfg
setr vice_smartphone:fivemanage_key "YOUR_FIVEMANAGE_API_KEY"

ensure ox_lib
ensure oxmysql
ensure screencapture
ensure vice_smartphone
```

Start `screencapture` before `vice_smartphone`.

5. Restart the server (or `ensure` both resources in order).

Stuck? **Join Discord first:** https://discord.gg/U7q7S45UCV

## Configuration

Main config: `vice_smartphone/config.lua`

| Option | Description |
|--------|-------------|
| `Config.Framework` | `auto`, `qbox`, or `qb` |
| `Config.Inventory` | `auto`, `ox_inventory`, or `qb-inventory` |
| `Config.OpenKey` | Default keybind (default `M`) |
| `Config.PhoneItem` | Item name (default `phone`) |
| `Config.RequireItem` | Require the item to open the phone |
| `Config.NumberPrefix` / `Config.NumberDigits` | Phone number format |
| `Config.ViceCrime.gangsResources` | Resource names that unlock the Vice Crime app |
| `Config.ViceCrime.storeUrl` | Store link shown when gangs is not installed |

Fivemanage key (server only — never put it in shared `config.lua`):

```cfg
setr vice_smartphone:fivemanage_key "YOUR_KEY"
```

Legacy convars also work: `vice_phone:fivemanage_key`, `fivemanage:key`.

## Camera

1. Ensure `screencapture` is started.
2. Set a valid Fivemanage API key.
3. Open Camera on the phone, take a photo, save to Photos.

Photos are stored as hosted URLs in `vice_phone_gallery`.

If capture times out, check F8 / server console for `[vice_smartphone]` lines, then ask on Discord with those logs:  
https://discord.gg/U7q7S45UCV

## Vice Crime (optional)

The phone ships with a **Vice Crime** app in App World.

- If any resource listed in `Config.ViceCrime.gangsResources` is **started**, the app unlocks and can open the gangs tablet.
- If none are running, the app shows your store URL only.

No gangs scripts are included in this package. Detection is name-based only; the tablet opens via public events/exports provided by your gangs resource.

Default resource names checked:

- `vice_gangs_creator`
- `vice_gangs_stable`
- `Vice_Gangs`

Add or remove names in `config.lua` to match your server.

## Compatibility

| Expectation | Supported |
|-------------|-----------|
| `ensure qb-phone` / `GetResourceState('qb-phone')` | Yes (`provide`) |
| `qb-phone:server:sendNewMail` / offline mail | Yes |
| `qb-phone:client:NewMailNotify` | Yes |
| `exports['qb-phone']` / `exports.vice_smartphone` | Yes |
| Legacy `vice_phone` events and callbacks | Yes (dual namespace) |

Database tables remain `vice_phone_*` for continuity with older installs.

## Default controls

| Action | Control |
|--------|---------|
| Open / close phone | `M` (configurable) |
| Camera shutter | Enter / Return |
| Camera flip | Arrow up |
| Camera cancel | Backspace |

## File layout

```
[vice_smartphone]/
  README.md
  .gitignore
  screencapture/          # camera dependency
  vice_smartphone/
    fxmanifest.lua
    config.lua
    client/
    server/
    shared/
    web/
    sql/
    install/
    locales/
```

## Version

**V1.0.0 Beta**

Beta release. Features and APIs may change before a stable 1.0.

## Support

# JOIN DISCORD FOR SUPPORT

### https://discord.gg/U7q7S45UCV

Before asking for help, have ready:

1. Framework (`qbox` / `qb-core`) and inventory  
2. Whether `screencapture` and `ox_lib` are started  
3. Server console + F8 client logs containing `[vice_smartphone]`  
4. What you already tried (SQL, item, Fivemanage key, start order)

Official support lives on Discord. That is the fastest way to get answers.

**Invite:** https://discord.gg/U7q7S45UCV

## License

See `LICENSE` for terms. Third-party code (`screencapture`, Leaflet) keeps its own licenses inside those folders.

## Credits

ViceLabs — Vice Smartphone  
ScreenCapture — [itschip/screencapture](https://github.com/itschip/screencapture) (or your vendored build)  
Leaflet — maps UI  
ox_lib / oxmysql — Overextended

---

## JOIN OUR DISCORD

# https://discord.gg/U7q7S45UCV

**Support · updates · community — ViceLabs**
