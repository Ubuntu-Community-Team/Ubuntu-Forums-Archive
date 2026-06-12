---
title: "Switching Desktops"
date: 2007-08-30
forum: Desktop Environments
---

### Post by Tanth9 on 2007-08-30
I am running 7.04 Server, and have GDE, KDE and XFCE installed, but when I boot I don't automatically start the desktop. I just type startx from the command line.

The problem is that every time I type startx it defaults to the GDE login, and I was wondering if there was a way to choose which desktop environment it goes to?

---

### Post by Happy_Man on 2007-08-30
If you have KDE installed, then instead of startx, you can use the command ```
sudo /etc/init.d/kdm start
``` That will give you KDE login manager, and from there you can choose what you want to log in to.

---

