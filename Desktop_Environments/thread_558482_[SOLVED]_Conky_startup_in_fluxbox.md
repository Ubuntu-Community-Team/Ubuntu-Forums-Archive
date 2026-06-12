---
title: "[SOLVED] Conky startup in fluxbox?"
date: 2007-09-24
forum: Desktop Environments
---

### Post by WiFi Ed on 2007-09-24
Ok, I'm an idiot. I've managed to install Fluxbox and have my right-click menus with all my apps, but I don't know how to make Conky load on startup. It works fine in Gnome, and works in Fluxbox if I start it from the terminal. I've searched the forums and found something about an ".Xinitrc" file but I am now overwhelmed by cluelessness.

Help!?

---

### Post by kerry_s on 2007-09-24
gedit ~/.fluxbox/startup

conky &

you'll see a sample section, put it there.

---

### Post by WiFi Ed on 2007-09-24
> **kerry_s said:**
> gedit ~/.fluxbox/startup

conky &

you'll see a sample section, put it there.

Thank you, I'll do that tonight when I get home:)

---

### Post by WiFi Ed on 2007-09-24
> **kerry_s said:**
> gedit ~/.fluxbox/startup

conky &

you'll see a sample section, put it there.

Thanks very much, that worked perfectly!:guitar:

---

