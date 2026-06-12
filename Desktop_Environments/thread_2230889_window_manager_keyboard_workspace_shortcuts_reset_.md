---
title: "window manager keyboard workspace shortcuts reset constantly on 14.04"
date: 2014-06-21
forum: Desktop Environments
---

### Post by xoloki on 2014-06-21
I normally use Alt-1 through Alt-5 to access workspaces 1-5 under Xubuntu.  Wevern I set this in 14.04, it initially works.  However, as soon as I put my laptop to sleep, or reboot, the shortcuts stop functioning.  However, the new settings are still present in Settings -> Window Manager ->Shortcuts, they just don't work.  

If I reset the the shortcuts, they work again, but only until the next sleep or reboot.  This is obnoxious enough to make 14.04 basically unusable.

---

### Post by Toz on 2014-06-23
Sounds like you may be suffering from [this bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1292290").

---

### Post by xoloki on 2014-06-25
> **Toz said:**
> Sounds like you may be suffering from [this bug]("https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1292290").

You are correct, thats precisely my issue.  The workaround in the bug worked for me.

Thanks!

---

