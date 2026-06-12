---
title: "(WW) intel(0): first get vblank counter failed: Invalid argument"
date: 2011-09-18
forum: Desktop Environments
---

### Post by AlphaWeapon on 2011-09-18
Hi. I'm using Ubuntu 11.04 with Unity on my laptop. It's great but I'm suffering of the infamous "close the laptop lid" freeze.
Basically, when I close the laptop lid, I have to pray that it didn't freeze when I open it up again, else I'll only be able to move the mouse and be forced to ctrl+alt+F1 and then ```
sudo pkill X
``` to restart the X server, losing all my open applications.
I already did the disable sync to vblank trick, but it still crashes. Interestingly enough, I saw this in the /var/log/Xorg.0.log
```

[ 58541.804] (WW) intel(0): first get vblank counter failed: Invalid argument
```
This is repeated MANY times, it fills up 90% of the file, and this is after both restarting the X server and the whole PC. It keeps dumping them even as I'm typing this. Is it related in any way? How can I fix this in the hope of fixing the continuous crash?

---

### Post by AlphaWeapon on 2011-09-19
Please help. It keeps crashing and I can't find any fix.

---

### Post by AlphaWeapon on 2011-09-23
Solved, thanks for help.

---

### Post by fallingleaf on 2011-09-28
What was the solution?

---

### Post by AlphaWeapon on 2011-10-01
> **fallingleaf said:**
> What was the solution?
I installed Windows

---

