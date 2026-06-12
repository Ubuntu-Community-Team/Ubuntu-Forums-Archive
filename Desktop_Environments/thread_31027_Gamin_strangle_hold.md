---
title: "Gamin strangle hold"
date: 2005-05-01
forum: Desktop Environments
---

### Post by JonahRowley on 2005-05-01
Gamin is monitoring /media/cdrom0, and I can't unmount/eject my cdrom.  What causes Gamin to do this (using KDE)?

```
$ fuser /media/cdrom0
/media/cdrom0:        7156
$ ps aux | grep 7156
mik       7156  0.2  0.4   3440  2244 ?        S    11:49   0:27 /usr/lib/gamin/gam_server
```

Is there a gentle way of telling gamin to let go of my cdrom?  Or a way to make it not monitor my cdrom (what's going to change anyway)?  I could just kill the process, but will that break things using gamin at the moment?

---

### Post by snairofilac on 2005-05-04
some investigation is occurring here:

[http://ubuntuforums.org/showthread.php?t=19331&highlight=gamin]("showthread.php?t=19331&highlight=gamin")

although not specifically to gam's effects on the cd drive.  I run gnome, and i have seen gam_server using as much as 30% of my CPU, although it drops to sleep just as quickly.

My drive sometimes will not eject unless i right click it's icon on the desktop, I had not isolated gamin as the culprit.

gl

---

