---
title: "Windows option gone from GRUB"
date: 2009-04-12
forum: General Help
---

### Post by javierd on 2009-04-12
I have a dell laptop with vista as default and i installed ubuntu 8.10. As the laptop is being used by other people besides me, i set windows as the default boot. However, being a newbie, the easiest way of doing so was editing menu.lst and put the vista option at the top.

Yesterday i updated the kernel and the vista option is gone. I have been googling and it seems that the update overwrote the vista option and i just need to create it again. This has been proven very difficult. 

The standard
> title Microsoft Windows
> root (hd0,0)
> savedefault
> makeactive
> chainloader +1

failed miserably

I kept investigating and found that for dell users, there is only one minor change:

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

I did that and i still cant  boot windows, but at least i got a message: error with bootmsg, press alt control del. And then im back to windowless-grub.

Any help?

Sorry for my english and newbishness.

---

### Post by fooman on 2009-04-12
open a terminal (applications > accessories > terminal) and type or copy/paste the following command into it:

```
sudo fdisk -l
```

then post the output back here.

---

### Post by javierd on 2009-04-12
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2   *          11        1316    10485760    7  HPFS/NTFS
/dev/sda3            1316       32385   249559531    7  HPFS/NTFS
/dev/sda4           32386       38913    52436160    5  Extended
/dev/sda5           38641       38913     2192841   82  Linux swap / Solaris
/dev/sda6           32386       38640    50243224+  83  Linux

Partition table entries are not in disk order

---

### Post by javierd on 2009-04-12
Does alterying the title helps?

I thought that was only a name but now im readig this: 
[I]
Can you try:

  title Windows chainloader directly
  chainloader (hd0,0)+1

or if that doesn't work:

  title Windows rootnoverify
  rootnoverify (hd0,0)
  chainloader +1 [/I]

---

