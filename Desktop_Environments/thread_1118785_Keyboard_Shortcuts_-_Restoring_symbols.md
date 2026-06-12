---
title: "Keyboard Shortcuts - Restoring symbols"
date: 2009-04-07
forum: Desktop Environments
---

### Post by nfsnobody on 2009-04-07
Hey guys,

Just thought I'd share this with you, as I've spent a frustrating hour trying to get this fixed.

If using the Keyboard Shortcuts utility you remove a keyboard symbol shortcut (e.g. XF86Something), it's not simple to restore. You can click on the row and type in text, but it won't go in there.

If you open up gconf-editor though, and go to /apps/gnome_settings_daemon/keybindings, all settings are in there. You simply choose the corresponding name and modify the value.

N.B. I am using Linux Mint, however I don't believe gnome-keybinding-properties is changed in this distro from the Ubuntu original.

---

