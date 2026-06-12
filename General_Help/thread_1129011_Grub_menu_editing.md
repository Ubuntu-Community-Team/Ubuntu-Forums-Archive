---
title: "Grub menu editing"
date: 2009-04-18
forum: General Help
---

### Post by RuleMaker on 2009-04-18
For example this is the menu entry for my mint linux:

```
title		Linux Mint, kernel 2.6.27-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
```

I'm not sure what are these numbers mean **(hd0,4)**

What and why _hd0_ and what is the number _4_?

It would make some sense if mint would be on sda4, but its on my sda5.

```
rulemaker@linux ~ $ sudo fdisk -l /dev/sda

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef1aef1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9472        9602     1052257+  82  Linux swap / Solaris
/dev/sda2   *           1        9471    76075776    f  W95 Ext'd (LBA)
/dev/sda3            9603        9964     2907765   83  Linux
/dev/sda5               1        6375    51207124+  83  Linux
/dev/sda6            6376        9471    24868588+   7  HPFS/NTFS

Partition table entries are not in disk order
```

---

### Post by chriskin on 2009-04-18
hd starts counting from 0 while sd starts counting from 1

then hd0,4 IS sda5 

hope i helped

---

### Post by RuleMaker on 2009-04-18
Thanks for your help, worked perfectly.

---

