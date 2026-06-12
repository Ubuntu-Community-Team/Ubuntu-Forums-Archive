---
title: "I can't get my USB work!"
date: 2008-12-29
forum: General Help
---

### Post by JafaarNhh on 2008-12-29
I can't get my USB work when I open it it say: Cannot mount volume.
What do I have to do.:confused:

---

### Post by Bachstelze on 2008-12-29
I'm assuming you're talking of an USB flash drive, right?

After you plug it in, open a terminal and run the command

```
sudo fdisk -l
```

and paste the results.

---

### Post by colsandurz on 2008-12-29
How are you trying to mount it?  Are you just sticking it in and using automount?  if not try this

```
sudo mount /dev/sda1 /mnt/mountPoint
```

first find out what the device is, i.e. it could be sdb1 sdc1 etc.  Then make sure your mount point actually exists, that is the one I use, but anything will do.

What is probably going on is that auto mount doesn't have root access (which it needs to mount) for some reason

---

### Post by JafaarNhh on 2008-12-30
Thanks Guys it helped very much

---

### Post by JafaarNhh on 2008-12-30
this is the results:
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa3eded

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9546    76678213+  83  Linux
/dev/sda2            9547        9733     1502077+   5  Extended
/dev/sda5            9547        9733     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

---

### Post by JafaarNhh on 2008-12-30
And now thanks to you i get my USB flash drive getting work!!
Thanks again :):)

---

