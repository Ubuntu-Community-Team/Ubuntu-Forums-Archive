---
title: "Messed up my DVD drive"
date: 2006-01-03
forum: General Help
---

### Post by Brinstar on 2006-01-03
I was trying to mount an iso file, and I didn't know i needed to create a folder to mount the ISO into, no-one mentioned on the info pages I found on the net (except one). Being a n00b, I mounted the iso into the place where my dvd drive normally mounts into (its called learning the hard way). How do I undo this?

---

### Post by pchachte on 2006-01-03
[QUOTE=Brinstar]I was trying to mount an iso file, and I didn't know i needed to create a folder to mount the ISO into, no-one mentioned on the info pages I found on the net (except one). Being a n00b, I mounted the iso into the place where my dvd drive normally mounts into (its called learning the hard way). How do I undo this?[/QUOTE]

I would think you could just unmount the iso (e.g., umount /media/dvd)
and then reset things by typing: sudo mount -a to remount everything
from fstab. 

This might not be the best response, but I don't believe there's
anything bad that could happen.  Hope this works.

charles

---

