---
title: "Desktop icons, Title bar, Graphic settings missing"
date: 2011-05-07
forum: Desktop Environments
---

### Post by snisarg on 2011-05-07
Ubuntu 10.10, was working perfectly for months and suddenly, when i boot my laptop, i cant see any desktop icons, and get nothing on right-clicking. All applications that i start do not have title bars, and the Appearence->visual effect->
which was always set to Extra, now boots with None.

when i select Extra manually every time, it then checks for drivers and then the title bars suddenly appear. The desktop problem persists.

---

### Post by Krytarik on 2011-05-08
- It seems like Compiz crashes for some reason at login. Try adding "compiz --replace" to "Startup Applications". If that works, remove "windowmanager" from the key "/desktop/gnome/session/required_components_list" in "gconf-editor".

- Make sure that the key "/apps/nautilus/preferences/show_desktop" is enabled in "gconf-editor".

Greetings.

---

