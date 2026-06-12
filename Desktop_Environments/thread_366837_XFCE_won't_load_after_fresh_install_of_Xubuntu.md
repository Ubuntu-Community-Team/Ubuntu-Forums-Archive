---
title: "XFCE won't load after fresh install of Xubuntu"
date: 2007-02-21
forum: Desktop Environments
---

### Post by elev on 2007-02-21
I just installed Xubuntu 6.10 on an old Celeron 533 with 96MB of RAM (I used the alernate install disc because of the low RAM).  Installation took quite a while (~90 minutes), but it went smooth.  When I boot and the login screen loads I can login to a terminal session, but if I try to load into XFCE it starts to load then quits back to the login screen.  Do you guys have any ideas?

---

### Post by K.Mandla on 2007-02-21
If it just kicks you back to the login, it's probably an error starting the graphical screen, which means a possible video configuration issue.

Can you double-check your xorg.conf file? If necessary, in the section that lists the driver, change it to "vesa" and see if you at least get the desktop.

---

