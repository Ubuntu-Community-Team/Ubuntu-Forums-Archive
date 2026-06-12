---
title: "gnome keyboard settings not preserved when keyboard plugged back in"
date: 2009-04-20
forum: General Help
---

### Post by Elfan on 2009-04-20
I have Microsoft "Natural® Ergonomic Keyboard 4000" usb keyboard attached to my thinkpad 61p laptop.  I have custom keyboard settings (control and caps switched) through the Gnome UI.  When I unplug the keyboard and plug it back in the configuration is lost (that is, caps lock is caps lock again on the usb keyboard).  However, it is preserved on the laptop keyboard.


Other info:
```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
$ uname -a
Linux chris-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
```

---

### Post by Elfan on 2009-04-20
I should clarify that this problem did not exist before the upgrade to Ibex.

---

