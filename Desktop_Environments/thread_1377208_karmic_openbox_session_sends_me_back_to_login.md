---
title: "karmic openbox session sends me back to login"
date: 2010-01-10
forum: Desktop Environments
---

### Post by rmills on 2010-01-10
I just installed openbox on a vanilla Karmic install, and when I login to Ubuntu with an Openbox session, it sends me right back to to the login screen.  Any ideas?

---

### Post by tba967 on 2010-02-15
I have the same problem, except with UNR 9.1.  Curiously, I noticed that I can run openbox-session from the "xterm" login.

---

### Post by tba967 on 2010-02-15
there are at least two bugs reported on launchpad related to openbox-session in karmic.  They have both to some extent been solved:

cannot log into openbox-session from GDM:
[https://bugs.launchpad.net/bugs/459005](https://bugs.launchpad.net/bugs/459005)


openbox-session will not open with the default of 4 virtual desktops
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/435501](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/435501)

---

