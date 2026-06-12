---
title: "Help! Xfce desktop environment has gone missing"
date: 2007-01-31
forum: Desktop Environments
---

### Post by ewan21 on 2007-01-31
Hi there,

Thanks in advance for your help.. I'm new to ubuntu (and linux), and have recently installed Ubuntu 6.10, with Xfce 4.2.

However, when using xkill" to close a program, I miss-clicked and clicked on of the xfce desktop panels.

This closed all the panels, and now I'm left with a blank desktop whenever I log into xfce - no icons or menus.

I've tried to reinstall xfce via apt-get, then aptitude, then (finally) the package manager, which worked ok, but the newly installed xfce hade the same problem.

Searching around I couldn't find anything to fix this, so any help at all would be great!!

Ewan.

ps. Gnome is working fine.

---

### Post by mikeym on 2007-01-31
[Alt] + F2 will take you into the run dialogue then run *xfce4-panel* and it should bring it back.

---

### Post by zedmaster on 2007-02-14
I was suffering from nearly the same problem myself, and it fixed it perfectly.  Just remember to make sure "run in terminal" isn't checked if you're using ALT-F2.  That was all that tripped me up.

---

