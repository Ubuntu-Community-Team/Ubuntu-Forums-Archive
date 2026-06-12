---
title: "Just installed Fluxbox how can I get a prompt for sudo pass..."
date: 2007-12-21
forum: Desktop Environments
---

### Post by Majin Zero on 2007-12-21
...like in Xfce / Gnome / KDE; when I try to open something that needs sudo permissions?

right now, I just get a error prompt sayin' I don't have permission...

---

### Post by taurus on 2007-12-21
What are you trying to open?  Can you run it from a terminal with a sudo in front?

---

### Post by smartboyathome on 2007-12-21
By the way, use gksudo for GUI apps, and sudo for CLI apps.

---

### Post by Majin Zero on 2007-12-21
stuff like the network manager and synaptec.

And yes sudo and gksudo work fine; but I'd like a non-command line solution.

Can only Desktop environments do that? Or is there a way to make it happen with a window manager like Fluxbox?

---

### Post by smartboyathome on 2007-12-21
You can start something using gksudo by editing the menu command and adding in front of it gksudo command (I don't know how to edit menus in fluxbox, sorry :().

---

### Post by taurus on 2007-12-21
> **smartboyathome said:**
> You can start something using gksudo by editing the menu command and adding in front of it gksudo command (I don't know how to edit menus in fluxbox, sorry :().

Look in ~/.fluxbox/menu.

---

