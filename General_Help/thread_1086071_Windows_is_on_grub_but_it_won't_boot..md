---
title: "Windows is on grub but it won't boot."
date: 2009-03-03
forum: General Help
---

### Post by linux noooob on 2009-03-03
I installed Windows XP on partition (0,0) (so it isn't the windows on first partition thing) Also because it was an older version of windows I installed it in IDE mode on my laptop and then installed ubuntu in SATA mode. Here is the important part of my menu.lst:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f235a127-22b4-42ab-81e7-5d247bb1c1c8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f235a127-22b4-42ab-81e7-5d247bb1c1c8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by CrucifiedEgo on 2009-03-03
Can you post any errors you recieve when trying to boot into the windows partition?

---

### Post by linux noooob on 2009-03-03
I didn't get any errors it just stays at Starting up... doesn't seem to lock up either.

---

### Post by ajgreeny on 2009-03-03
Show us the output of ```
sudo fdisk -l
``` in terminal, which may give a clue.

---

### Post by linux noooob on 2009-03-03
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43c2efb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1648       14593   103988745    7  HPFS/NTFS
/dev/sda2               1        1647    13229496    5  Extended
/dev/sda5               1        1572    12627027   83  Linux
/dev/sda6            1573        1647      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

```

here you go!

---

### Post by ajgreeny on 2009-03-04
OK, from that it looks as if your windows partition is not at the front of the drive as you will note that the start and end are numbers after the linux partitions.
/dev/sda1   *        **1648**       14593   103988745    7  HPFS/NTFS
/dev/sda2               1        1647    13229496    5  Extended
/dev/sda5               1        1572    12627027   83  Linux
/dev/sda6            1573        **1647**      602406   82  Linux swap / Solaris
I wonder therefore if you need to remap the drives for the sake of grub finding windows properly, or perhaps even try using the UUID for the windows partition, which you can get from ```
sudo blkid
```I don't think I have seen windows partitions shown in this way in grub, so do not know if it even works, but it could be worth a try.  I will try to find more info about the remapping of drives as I do not know much about it at the moment, but I think it needs a line edited in your /boot/grub/menu.lst file in the windows entry, something like ```
rootnoverify (hdo,3)
```EDIT:  No, I don't think the option of the UUID is any good for the windows partition, so I could be leading you right up the garden path here.  Wait for more help, I think, or just try the rootnoverify trick.  If it does not work, you have lost nothing.

---

### Post by linux noooob on 2009-03-04
First problem is that the uuid thing made it return an error 15 : no file found. Also I put rootnovarify (hd0,0) and that didn't change anything I also put it at (hd0,3) but it said file not found.

---

### Post by ajgreeny on 2009-03-04
Well I'm afraid I'm baffled and don't think I can go much further, other than suggesting you download [supergrub]("http://stmaarten.globat.com/%7Esupergrubdisk.org/") and boot from that to try and find your windows install.  I have never used it as grub has never let me down (yet) but it is apparently dead easy to use.

---

