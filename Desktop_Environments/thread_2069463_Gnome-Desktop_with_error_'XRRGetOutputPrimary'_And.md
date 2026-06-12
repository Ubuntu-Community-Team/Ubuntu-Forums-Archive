---
title: "Gnome-Desktop with error 'XRRGetOutputPrimary' And 'XRRGetScreenResourcesCurrent'"
date: 2012-10-10
forum: Desktop Environments
---

### Post by offline369 on 2012-10-10
#I have the problem as following when install gnome-desktop version 2.30.2 and the same for installation of gnome-menus and  gnome-panel version 2.30.2.

CCLD   test-ditem
./.libs/libgnome-desktop-2.so: undefined reference to `XRRGetOutputPrimary'
./.libs/libgnome-desktop-2.so: undefined reference to `XRRSetOutputPrimary'
./.libs/libgnome-desktop-2.so: undefined reference to `XRRGetScreenResourcesCurrent'
collect2: ld returned 1 exit status
make[3]: *** [test-ditem] Error 1
make[3]: Leaving directory `/home/rosie/gnome/gnome-desktop-2.30.2/libgnome-desktop'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rosie/gnome/gnome-desktop-2.30.2/libgnome-desktop'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rosie/gnome/gnome-desktop-2.30.2'
make: *** [all] Error 2

#It took me a few days. Help me! Thanks in advance!

---

### Post by nothingspecial on 2012-10-11
*Thread moved to **Desktop Environments**.*

---

