---
title: "ut2004 from cd's"
date: 2010-01-07
forum: Gaming &amp; Leisure
---

### Post by HolyPhoenix on 2010-01-07
I am having trouble running the installer for from the cd's for ut2004.  It runs fine, but when it tells me to get the 2nd cd I can pull the first cd out, but I can't get it to unmount completely in order for me to get the 2nd cd mounted.  Can someone help?  My ubuntu is completely updated.

---

### Post by sakuramboo on 2010-01-07
[http://sakuramboo.com/blog/2009/04/another-useful-tip/](http://sakuramboo.com/blog/2009/04/another-useful-tip/)

---

### Post by Brebs on 2010-01-08
> **HolyPhoenix said:**
> can't get it to unmount

*DON'T* do this:

```
cd /media/cdrom
./installer.sh
```
Because that locks the mountpoint, due to the current directory being within the mountpoint.

Instead, do this:

```
cd
/media/cdrom/installer.sh
```
Yes, that first line is a simple "cd" command, which will change the current directory to the home directory of the current user, which is safely away from /media/cdrom.

---

