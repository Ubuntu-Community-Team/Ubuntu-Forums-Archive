---
title: "Problems with Failsafe"
date: 2011-01-28
forum: Desktop Environments
---

### Post by mqevolution on 2011-01-28
Recently I changes settings on Ubuntu Desktop and I choose gnome failsafe login, hence everything loads nice except when the user accounts is load it only appears the background and the terminal. Is there anyway to have the desktop back the way it was with the complete gui interface?

---

### Post by wormyblackburny on 2011-01-28
check /etc/inittab and see if it says 'id:1:initdefault:' if it does, change the 1 to a 2 and reboot, that should fix it and set it to boot into "full" user mode.

---

