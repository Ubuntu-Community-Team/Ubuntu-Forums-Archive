---
title: "XGL messed up windows"
date: 2006-08-30
forum: Desktop Environments
---

### Post by eggmanpete on 2006-08-30
just installed xgl using the routine on ubuntuguide.org
i'm using nvidia.
my problem is that all the title bars (bar with minimise, maximise, close buttons) has disappeared from all windows, i cannot switch desktops and cannot switch windows either.
Anyone with more experience than me that knows why it could be doing this? :confused:

---

### Post by eggmanpete on 2006-08-30
slight update: when i log out, everything is normal gnome
when i type "thefuture" in the console to start the script:
```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.gb
```
everthing stated in above post happens

---

