---
title: "Need your input: /dev/.static/dev read-only"
date: 2009-01-09
forum: General Help
---

### Post by MacUntu on 2009-01-09
Looks like I'm hit by this bug: [https://bugs.launchpad.net/debian/+source/udev/+bug/253786](https://bugs.launchpad.net/debian/+source/udev/+bug/253786)

/dev/.static/dev is mounted read-only and causes some problems (you can even see "read-only file system"-errors during the boot process).

The bug seems to be fixed for Jaunty but as the last entry indicates it's not fixed for Intrepid (yet?). I just want to know if this is an Intrepid-bug or if I did something wrong so please post the output of:

```
cat /proc/mounts | grep static
```
Mine looks like:

```
/dev/disk/by-uuid/bla /dev/.static/dev ext3 [COLOR="Red"]ro[/COLOR],errors=remount-ro,data=ordered 0 0
```
"ro" being the problem.

TIA,
MacUntu

---

### Post by MacUntu on 2009-01-10
*push*

---

