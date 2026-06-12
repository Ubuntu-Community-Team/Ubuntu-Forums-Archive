---
title: "keyboard locale incorrect"
date: 2008-07-21
forum: Desktop Environments
---

### Post by ali3nx on 2008-07-21
i setup ubuntu for a relative and my keyboard map was set to the wrong locale during install. i attempted to change it using the keyboard system prefs utils but haven't been able to change it to the correct setting as it claims to be the correct one however the keyboard locale is clearly still incorrect. anyone know how to set the keyboard locale manually? the locale was set to canada during install and despite changing it to usa in the gnome prefs its still incorrect both in gnome and gterm.

---

### Post by ali3nx on 2008-07-21
got it figured out after some luck googling. the system prefs util for setting keyboard locales in gnome doesn't modify the xkb map defined in xorg.conf

[https://help.ubuntu.com/xubuntu/desktopguide/C/switch-keyboard-layout.html](https://help.ubuntu.com/xubuntu/desktopguide/C/switch-keyboard-layout.html)

editing xorg.conf and setxkbmap us fixed it

---

