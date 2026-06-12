---
title: "crashing menu bar"
date: 2011-02-16
forum: Desktop Environments
---

### Post by ugsquish on 2011-02-16
I rebooted my computer and there was strangely 2 audio icons next to the clock. I right clicked 1 and removed it from the bar. Now I can t seem to get that bar to quit flashing. I tried the recovery console. to repair any broken packages. Still flashing. I can't seem to get any programs open. What could be causing this issue and how I can fix it?

---

### Post by Krytarik on 2011-02-17
Are you talking about the (usually upper) gnome-panel?

If so, try resetting them from within the console:
```
rm -rf ~/.gconf/apps/panel
```
Following your post, I suppose you know how to get to the console and switch back to GDM.

---

### Post by ugsquish on 2011-02-18
I tried it and it seems to be working. tyvm for the help :)

---

