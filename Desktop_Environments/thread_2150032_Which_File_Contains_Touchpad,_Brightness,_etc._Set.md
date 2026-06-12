---
title: "Which File Contains Touchpad, Brightness, etc. Settings?"
date: 2013-05-30
forum: Desktop Environments
---

### Post by ping-wu on 2013-05-30
I apologize if this question has been asked.  My search on this forum was not helpful.

Does anyone know which file in the home directory that contains settings for touchpad/mouse, brightness, screen lock, etc (that we input thru System Settings)?

---

### Post by mc4man on 2013-05-30
That would depend on what release of Ubuntu you're using

---

### Post by ping-wu on 2013-05-30
> **mc4man said:**
> That would depend on what release of Ubuntu you're using

Ubuntu 13.04 Raring

---

### Post by mc4man on 2013-05-30
user settings such as those are stored in ~/.config/dconf/user but you'll do little with that file.

Most settings can be seen in dconf-editor somewhere.
Example of touchpad in screen
(org.gnome.settings-daemon.peripherals.touchpad

---

