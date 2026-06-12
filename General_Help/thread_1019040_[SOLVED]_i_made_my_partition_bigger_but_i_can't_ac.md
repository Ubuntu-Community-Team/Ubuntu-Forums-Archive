---
title: "[SOLVED] i made my partition bigger but i can't access it??"
date: 2008-12-22
forum: General Help
---

### Post by DSL5 on 2008-12-22
Ok, so I dual boot Ubuntu and XP, and i decided today, since i hardly ever use XP, to make the XP partition smaller and give more space to Ubuntu. Running from a Live CD, I went to GParted, shrank the XP partition, Swapoff'd the linux-swap so I could expand the Extended partition linux is in, extended the Extened partition into the empty space on it's left, the grew the ext3 partition inside of the Extended partition into the newly created Extended space.

After it was all done, however, the extra 10GB I gave linux show up as used space (shaded in yellow) and I cannot access it. When i boot into linux, it still thinks it the same size as before???

Anyone know how to fix this? Attatched is a picture of my GParted window.

[[IMG]http://img176.imageshack.us/img176/2808/gpartedyx5.th.png[/IMG]](http://img176.imageshack.us/my.php?image=gpartedyx5.png)

---

### Post by taurus on 2008-12-22
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by DSL5 on 2008-12-22
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cab9cab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11749    94373811    7  HPFS/NTFS
/dev/sda2           11750       14593    22844430    5  Extended
/dev/sda5           11750       14462    21792141   83  Linux
/dev/sda6           14463       14593     1052226   82  Linux swap / Solaris

---

### Post by dcstar on 2008-12-22
> **DSL5 said:**
> Ok, so I dual boot Ubuntu and XP, and i decided today, since i hardly ever use XP, to make the XP partition smaller and give more space to Ubuntu. Running from a Live CD, I went to GParted, shrank the XP partition, Swapoff'd the linux-swap so I could expand the Extended partition linux is in, extended the Extened partition into the empty space on it's left, the grew the ext3 partition inside of the Extended partition into the newly created Extended space.

After it was all done, however, the extra 10GB I gave linux show up as used space (shaded in yellow) and I cannot access it. When i boot into linux, it still thinks it the same size as before???

Anyone know how to fix this? Attatched is a picture of my GParted window.


Boot off the live CD, and use the Gparted "Check" function on each (unmounted) partition to force a fsck and (hopefully) fix the problem.

---

### Post by taurus on 2008-12-22
What about

```
df -h
free -m
```

---

### Post by DSL5 on 2008-12-22
> **dcstar said:**
> Boot off the live CD, and use the Gparted "Check" function on each (unmounted) partition to force a fsck and (hopefully) fix the problem.

THANK YOU!!!!

Worked like a charm!

---

