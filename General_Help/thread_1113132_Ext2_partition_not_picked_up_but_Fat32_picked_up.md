---
title: "Ext2 partition not picked up but Fat32 picked up"
date: 2009-04-01
forum: General Help
---

### Post by rlzyoner on 2009-04-01
Howdy,

This one has been kind of bugging me for a day or so now.
I have an 8gig usb stick.
I formatted the first 2 gigs to Fat32 and then formatted the remaining space to ext2.
I've put a live image on the Fat32 partition but when I boot into the system, the second partition does not exist under /dev

I've tried putting the usb stick into another machine with ibex and again, it picks up /dev/sdb1 but not /dev/sdb2 (the ext2 partition)

Any ideas ?

---

### Post by dcstar on 2009-04-02
> **rlzyoner said:**
> Howdy,

This one has been kind of bugging me for a day or so now.
I have an 8gig usb stick.
I formatted the first 2 gigs to Fat32 and then formatted the remaining space to ext2.
I've put a live image on the Fat32 partition but when I boot into the system, the second partition does not exist under /dev

I've tried putting the usb stick into another machine with ibex and again, it picks up /dev/sdb1 but not /dev/sdb2 (the ext2 partition)

Any ideas ?

Look in /media

---

### Post by rlzyoner on 2009-04-02
Cheers, thanks dude

---

