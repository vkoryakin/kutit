# Kutit

**English** · [Русский](README.ru.md)

*Pronounced like "cut it".*

**Cut the switching.**

For everyone who types in more than one language. You reply to a colleague in one language, look something up in another, go back to the chat, and every time you switch the layout first. Kutit does it for you: every field and every tab remembers its layout and brings it back on its own.

> [!CAUTION]
> Side effect: after a week with Kutit you may forget where the layout switch key is. 😉

Kutit works with whatever keyboard layouts you have enabled in macOS. New fields start in your **default layout**: the first layout with Latin letters in your Mac's language (Spanish on a Spanish Mac, German on a German one); when your language has none, as Russian, Greek or Thai, the first Latin layout for English (U.S., ABC, British…). There are no app lists to maintain and no shortcuts to learn: Kutit simply notices where you are typing.

## How it works

- **Every field remembers its layout.** Type in Russian in one note and in English in another: each gets its own layout back when you return to it.
- **Every browser tab, too.** Each tab keeps its layout as you browse inside it, and each field in the tab, the address bar included, keeps its own. A new tab starts in the default layout.
- **Sensible defaults.** A field you have never typed in starts in the default layout. Spotlight, Siri and password fields always get it and are never remembered.
- **A small indicator** shows the layout right above the field you are typing in, every time you move to another field; if you like, only when the layout changes.
- **The 🌐 key** switches between the two layouts you use most with a single tap, and a longer press takes you to the others. Kutit learns the pair as you work; at first it is your first two layouts. If you prefer, a tap goes through all of them in turn.
- **A menu bar icon.** Click it for the menu: the Globe key switch, the indicator and its look, Pause and Quit. Pause ▸ Suspend stops Kutit until it restarts (with the Mac, for one), Pause ▸ Turn Off until you turn it on again; 🌐 keeps working either way, and a red badge on the icon shows which. ⌥-click the icon to suspend or resume at once. The menu speaks the language of your Mac: English, Russian, Spanish, Portuguese, German, French, Swedish, Italian, Turkish, Thai or Greek, and English otherwise. Only English and Russian are written by hand; the other languages are machine translations, and corrections are welcome.

## Privacy

Everything stays on your machine; nothing is sent anywhere. Kutit stores which app, window, field and tab had which layout, and nothing else: no window titles, no typed text, no keystrokes.

## Requirements

- macOS. Checked on macOS 27.0.1; older versions are not tested.
- [Hammerspoon](https://www.hammerspoon.org/) with Accessibility access. Checked with Hammerspoon 1.1.1; the installer gets it for you.
- At least two keyboard layouts in macOS.
- **"Automatically switch to a document's input source"** turned off (Keyboard → Input Sources): it switches layouts on its own and fights Kutit. Until it is off Kutit waits, and its menu takes you to it.
- For the 🌐 key to switch layouts through Kutit: **"Press 🌐 key to"** set to **Do Nothing** (Keyboard). Otherwise the 🌐 key keeps its macOS action, and Kutit still remembers every layout you choose.

## Light on resources

Kutit is careful with your battery and your CPU: it reacts to what you do and asks macOS as little as it can.

- It works on events (switching windows, fields or tabs, typing, changing the layout) and does not scan apps in the background.
- Typing is never slowed down: keys are never swallowed or delayed.
- Only the app in front is ever asked anything; background apps are left alone.
- The memory is written to disk rarely, after a minute without changes, and takes a few kilobytes.
- No daemon, no network, no helper process: Kutit is just a Hammerspoon configuration.

## Works with

What Kutit remembers in each app it was checked with.

<!-- apps:begin -->
| App | Kind | Window | Field | Tab | Workspace | Stack | Channel | Address bar | Secure field | App restart | Kutit restart | System restart | Checked |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [Vivaldi](#works-with "every tab also inside stacks and across workspaces") | browser | ✅ | ✅ | ✅ | ✅ | ✅ | — | ✅ | ❔ | ❌ | ✅ | ❌ | 0.9.0 |
| Chrome | browser | ✅ | ✅ | ✅ | — | — | — | ✅ | ❔ | ❌ | ✅ | ❌ | ≤0.2.0 |
| [Safari](#works-with "no tab memory in a one-tab window; tabs forgotten when Kutit restarts") | browser | ✅ | ✅ | ⚠️ | — | — | — | ✅ | ❔ | ❌ | ⚠️ | ❌ | ≤0.2.0 |
| Firefox | browser | ✅ | ✅ | ✅ | — | — | — | ❔ | ❔ | ❌ | ✅ | ❌ | ≤0.2.0 |
| [iTerm2](#works-with "tabs forgotten when Kutit restarts") | terminal | ✅ | ✅ | ✅ | — | — | — | — | ❔ | ❌ | ⚠️ | ❌ | 0.10.0 |
| [Slack](#works-with "every channel and DM; kept when Slack restarts") | web app | ✅ | ✅ | — | — | — | ✅ | — | ❔ | ✅ | ✅ | ❌ | 0.9.0 |
| [VSCodium](#works-with "each window its own; a rare missed focus in the command palette") | Electron | ✅ | ✅ | — | — | — | — | — | ❔ | ❌ | ✅ | ❌ | 0.9.0 |
| Notes | native | ✅ | ✅ | — | — | — | — | — | ❔ | ❌ | ✅ | ❌ | 0.9.0 |
| TextEdit | native | ✅ | ✅ | — | — | — | — | — | ❔ | ❌ | ✅ | ❌ | ≤0.2.0 |
| Finder | native | ✅ | ✅ | — | — | — | — | — | ❔ | ❌ | ✅ | ❌ | ≤0.2.0 |
| [Screen Sharing](#works-with "one memory for the remote screen in every window and connection; if the remote Mac runs Kutit too, turn it off there: Pause ▸ Turn Off") | remote screen | — | ✅ | — | — | — | — | — | — | ❔ | ✅ | ❌ | 0.10.0 |
| [Telegram](#works-with "one memory for every chat: the app tells no chat apart") | native | ✅ | ⚠️ | — | — | — | ❌ | — | ❔ | ❌ | ✅ | ❌ | 0.9.0 |
| [Spotlight and Siri](#works-with "always the default layout, so a search starts in Latin letters") | launcher | 🔒 | 🔒 | — | — | — | — | — | — | — | — | — | 0.9.0 |

✅ works · ⚠️ partly · ❌ no · 🔒 by design: never remembered · ❔ not checked live · — does not apply. Checked: the Kutit version of the last live check. A name in blue has a note: point at it.
<!-- apps:end -->

## Installation

1. Run in Terminal:

   ```bash
   curl -fsSL https://github.com/vkoryakin/kutit/releases/latest/download/install.sh | bash
   ```

   It installs Hammerspoon if it is missing, adds the Kutit Spoon and starts it. Or download `install.sh` from the [latest release](../../releases/latest) and run `bash install.sh`. Run it again to update.
2. When macOS asks, allow Accessibility access for Hammerspoon.
3. Change the keyboard settings above. Kutit's menu shows which one is still in the way.

To remove Kutit, run the installer with `--uninstall`:

```bash
curl -fsSL https://github.com/vkoryakin/kutit/releases/latest/download/install.sh | bash -s -- --uninstall
```

Your other Hammerspoon settings stay as they are.

## Reporting a bug

Open an [issue](../../issues). Say what you did, what you expected and what happened instead, in which app, and your Kutit and macOS versions (Kutit's version is at the top of its menu).

If you can repeat it, a trace helps most:

1. Open the Hammerspoon console (the Hammerspoon icon in the menu bar → Console).
2. Type `spoon.Kutit.trace.start("bug")` and press Return.
3. Repeat the problem.
4. Type `spoon.Kutit.trace.stop()` and press Return.
5. Attach the file `~/.hammerspoon/kutit_traces/bug.lua` to the issue.

A trace holds app names, window numbers, field identifiers and layouts. It never holds window titles, web addresses or anything you type.

## Status

Under development: expect rough edges, and tell me about them.

## License

Copyright (C) 2026 Vitaly Koryakin.

Kutit is free software: you can redistribute it and/or modify it under the terms of the GNU General
Public License as published by the Free Software Foundation, version 3 of the License. A modified
version you distribute must be released under the same license. See [`LICENSE`](LICENSE).

---

*Kutit — Cut the switching. Less switching, more flow.*
