---
title: "getting ma desktop with only my wallpaper"
date: 2010-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanidhyajain1990 on 2010-04-28
[\\hey]("file://\\hey"),
pls help me out...i m getting blank screen with mouse cursor n wallpaper after startup...
what to do ?
thanks in advance

---

### Post by leonhook on 2010-04-28
1. Press ALT+F2 and type 'gnome-terminal' to access the terminal
2. Execute these three commands:
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

---

