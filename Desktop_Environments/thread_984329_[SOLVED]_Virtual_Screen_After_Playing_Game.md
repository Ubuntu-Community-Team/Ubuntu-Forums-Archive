---
title: "[SOLVED] Virtual Screen After Playing Game"
date: 2008-11-16
forum: Desktop Environments
---

### Post by Orange Luna on 2008-11-16
Hello all.  I just got KDE installed on my computer and I'm having trouble with my resolution.  When I quit tuxracer it sent me to a virtual screen (one that pans when a mouse cursor is moved to the edge of it).  I have to go into System Settings > Display and drop to a lower resolution and then select the proper on again to fix it.  Also this virtual screen is kept when I started the X today. Anyone have a idea on how to fix this?

---

### Post by 289Shelby on 2008-11-16
I don't know if this will work but you can try:

Control Centre -> Peripherals -> Display and set the resolution there. Also make sure that "Apply settings on KDE startup" is checked.

---

### Post by Orange Luna on 2008-11-16
did. no luck.  this is an nvidia driver bug.  whenever I set 1280x1024 in my /etc/X11/xorg.conf the screens loads as a 1440x1280 virtual screen.  appreciate the tip.

---

