---
title: "Sharing a ZFS-fuse zpool"
date: 2008-12-28
forum: General Help
---

### Post by bobbob1016 on 2008-12-28
I installed zfs-fuse, and made a zpool, and a raidz on it.  I've been google-ing, and this is what I found.

[http://unix.derkeiler.com/Mailing-Lists/FreeBSD/current/2008-03/msg00153.html](http://unix.derkeiler.com/Mailing-Lists/FreeBSD/current/2008-03/msg00153.html)

When I do the sharenfs=on line, it seems to go fine, but I can't connect from any other machine, it says access denied even though I told it to allow connections from my network.  Same goes for sharesmb=on.  Any ideas?

---

### Post by Thalandor on 2009-01-07
Yes. zfs-fuse simply doesn't support all ZFS features (yet). You're going to have to share your drives the old fashioned way.

---

### Post by yurac on 2012-03-23
sharenfs does work for me when I use the fsid=0 option

---

