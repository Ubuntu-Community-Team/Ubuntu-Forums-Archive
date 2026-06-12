---
title: "Xorg.conf issues"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Scarabomb on 2006-06-02
Haha, First post

I'm sorta new to Ubuntu
Anyway, I'm using Breezy with GNOME with xfwm4 and have been surfing around for weeks and weeks trying to figure out how to get Transparent windows.

Well what I've done so far is get fglrx driver for my ATI Mobility x700 and it works fine but my issue is I'm trying to put in 
```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```
in xorg.conf then either 1) End Session and try to get int Default system settings or 2) Reboot I end up with pretty much a dead everything.  Gets as far as loading up Window Manager then sorta dies.  Before xfwm4, fglrx would revert back to mesa unless I fixed the xorg.conf .  Actually, everytime I edit almost anything in xorg.conf , the mesa thing shows up during "flgrxinfo".  I installed the ATI driver through method two on the ATI wiki.

Help appreciated, thanks

---

