---
title: "Booting Problem"
date: 2006-04-13
forum: Desktop Environments
---

### Post by ace4000 on 2006-04-13
I cant load Ubuntu anymore.  I keep getting this message:
> /dev/cdrom: open failed no medium found
/dev/cdrom1: open failed no medium found
Unable to find volume group "Ubuntu"
ALERT! /dev/mapper/Ubuntu-root dose not exist.  Dropping to shell
I try the live boot and the live boot works just fine but I still can't get Ubuntu to boot up.  Please help if you can, this is such an alsome OS and I have so much fun with it.
Thanks,
Ace

---

### Post by Sef on 2006-04-13
Using the live cd, do this:

Applications > Accessories > Terminal

then type

sudo fdisk -l 

and post the results here.

---

### Post by ace4000 on 2006-04-14
Thanks for the info, I will try it later today.  I hope I dont have to reinstall Ubuntu, what a pain that will be ](*,) 
Thanks,
Ace

---

### Post by ace4000 on 2006-04-14
I got the Live up and went to the fdisk -l and this what I got:
```
Disk /dva/hda:  (size, heads, etc.)

   Device Boot   Start   End   Blocks   Id   System
/dev/hda1 *       1      31    2434    83   HPES/NTFS

Disk /dva/hdb:  (size, heads, etc.)

   Device Boot   Start   End    Blocks   Id   System
/dev/hdb1 *        1      31    248976   83   Linux
/dev/hdb2         32    2434 193020097+  5   Extended
/dev/hdb5         32    2434 193020066   8e  Linux LVM
```
Hope this helps. 
Thanks, 
Ace

---

### Post by robcarr2 on 2006-05-14
I am having this same problem :( been trying to fix it for 2 weeks but no luck yet

---

### Post by fmuniz on 2006-05-24
I get the same thing. Works fine with 2.6.15-19. Can't boot with 2.6.15-23.

---

