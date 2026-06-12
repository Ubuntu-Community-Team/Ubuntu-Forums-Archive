---
title: "Help add xp partition to grub"
date: 2009-05-03
forum: General Help
---

### Post by elliotn on 2009-05-03
HERE IS MY sudo fdisk -l results

> elliotn@elliotn:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde1da92c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1752    14072908+  83  Linux
/dev/sda2   *        1753        2342     4739175    7  HPFS/NTFS
/dev/sda3            2343        2434      738990    5  Extended
/dev/sda5            2343        2434      738958+  82  Linux swap / Solaris
elliotn@elliotn:~$ 



I dont know what to do in menu.lst

title: Windows xp
root : (hd1,0)(please help here)

thanks

---

### Post by delcypher on 2009-05-03
I think you want the following

```

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader     +1

```

GRUB uses the following format for disc (hd[HARD_DISK_NO],[PARTION_NO]) both [HARD_DISK_NO] and [PARTION_NO] start from 0 rather than 1.

---

### Post by elliotn on 2009-05-03
> **delcypher said:**
> I think you want the following

```

title: Windows XP
root : (hd0,1)
savedefault
makeactive
chainloader     +1

```

GRUB uses the following format for disc (hd[HARD_DISK_NO],[PARTION_NO]) both [HARD_DISK_NO] and [PARTION_NO] start from 0 rather than 1.


K let me try that n come back

---

### Post by elliotn on 2009-05-03
Grrr it aint happenin, when I do that it says

Starting...

Is suppose to be

---

### Post by Legace on 2009-05-03
It should be:

```

title		Windows XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by delcypher on 2009-05-03
Opps I shouldn't of had semi-colons in a menu.lst file, sorry (corrected now). Legace's suggestion should work (If [rootnoverify]("http://www.gnu.org/software/grub/manual/grub.html#rootnoverify") doesn't work then try just root).

---

