---
title: "Ubuntu crashes on login but Kubuntu works fine"
date: 2007-04-04
forum: Desktop Environments
---

### Post by beefcake on 2007-04-04
I'm running Kubuntu 7.04 on an HP zv5000 laptop (P4 2.4GHz, 512MB RAM, 40GB HDD, 128MB ATI 9100 video card), dual booted with Win XP. I installed ubuntu without any problems, but as soon as I try logging in, I get a black screen and return to the login screen. I have no such problems with KDE. Also, this problem isn't due to the beta version; I've tried Ubuntu dapper (6.06) and edgy (6.10) with the same problems, whereas the KDE versions work without a glitch. So far, this implies there's some problem with gdm, but I haven't been able to pinpoint the bug.

Any help on this matter is greatly appreciated.

---

### Post by CrazyGenie on 2007-04-05
check /var/log/gdm/:0.log for any hints or
/var/log/Xorg.0.log for X related issues.

---

