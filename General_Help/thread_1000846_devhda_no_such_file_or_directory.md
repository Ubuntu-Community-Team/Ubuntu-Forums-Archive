---
title: "/dev/hda no such file or directory"
date: 2008-12-03
forum: General Help
---

### Post by Ampi on 2008-12-03
I want to use the command hdparm to do some tweaking.
But when I try 

hdparm -d /dev/hda

it tells me that I don't have such file or directory.

I do indeed not have this directory, I have my hda1 in my /media directory, but there the command doesn't work either since it seems to be empty.

But my devices do work. One of them has my home directory the other one has Ubuntu. 

How do I find my devices? (this questions somehow doesn't sound right ;))

---

### Post by taurus on 2008-12-03
Maybe it's /dev/sda!  Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Ampi on 2008-12-03
you're so right!! sda and sdb!!!
```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d34c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4998    40146403+  83  Linux

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098445

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4773    38339091   83  Linux
/dev/sdb2            4774        4866      747022+   5  Extended
/dev/sdb5            4774        4866      746991   82  Linux swap / Solaris
```

Bur for most of the options I use with hdparm I get the following warning: 

```
HDIO_GET_MULTCOUNT failed: Inappropriate ioctl for device
```

I have no idea what this means..

---

### Post by Ampi on 2008-12-09
Nobody has any idea?

---

