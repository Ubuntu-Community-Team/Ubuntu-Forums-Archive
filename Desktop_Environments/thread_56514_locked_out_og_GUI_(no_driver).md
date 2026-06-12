---
title: "locked out og GUI (no driver)"
date: 2005-08-12
forum: Desktop Environments
---

### Post by floyd27 on 2005-08-12
Hi
I was attempting to install a ati driver but becasue there are 50 thousand diff wasy telling you how i messed it up...
I uninstalled my old fglrx driver and now cant get into KDE

I typed startx and it tells me i have no fglrx driver installed.
is there a way to get it back short of re-installing ubuntu?
thanx 

please hurry... windows is hurting my eyes.. :)

---

### Post by az on 2005-08-12
Boot into recovery mode and do
dpkg-reconfigure xserver-xorg

and pick the defaults for everything.

If that does not work, install xresprobe and try again.


type init 2 to boot into the full desktop.

---

### Post by floyd27 on 2005-08-13
worked like a charm
thanx a bunch...

---

