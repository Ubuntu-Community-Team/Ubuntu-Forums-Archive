---
title: "[SOLVED] Desktop lockdown issue"
date: 2008-03-26
forum: Desktop Environments
---

### Post by potam on 2008-03-26
Hello guys,

When I click on the Super button (formerly Windows button) **twice** my desktop locks down, just like the way in the System menu. I want to turn this behavior off, but can't find how.
My system parameters:
Ubuntu 7.10
Gnome 2.20.1
Nautilus 2.20.0 as window manager
and Compiz fusion 0.6.3

Thanks for your help.

---

### Post by pseudo-random on 2008-03-26
Try your system > preferences > keyboard shortcuts.
My win key spawns a terminal. ;)

---

### Post by potam on 2008-03-26
> **pseudo-random said:**
> Try your system > preferences > keyboard shortcuts.
My win key spawns a terminal. ;)

Already tried, but the lockdown hotkey is set to SUPER+L (just like in windows), so I don't understand this SUPER+SUPER hotkey. Pretty strange.

---

### Post by potam on 2008-03-29
Up

---

### Post by potam on 2008-04-09
OMG, the solution hurts me! In the hotkeys window "Super L" does not mean the Super key+the L key. Oh no, it means the left super key! No '_' to make it clear, just 'Super L'. Ubuntu ignored my L key, and binded logout to the left super key.

---

