---
title: "can't mount FAT32 partitions"
date: 2004-12-02
forum: Desktop Environments
---

### Post by shlomik on 2004-12-02
I have FAT32 partitions on the same HD with ubuntu whan i try to do that

mount -t vfat /media/C /dev/hda1

everything works fine but whan i try to mount the other partitions it doesn't work 
whan i do this

mount -t vfat /media/E /dev/hda2

or

mount -t vfat /media/F /dev/hda3

this isn't working I don't know why

also all the partitions on the HD are FAT32 so I  dont know why it  happens

thanks
Shlomik

---

### Post by Rancoras on 2004-12-02
Is there an error message with the second 2 commands?

---

### Post by bazuka on 2004-12-02
Shlomik: Are you sudo'd in? You'll need to do that.
You have the dev path and mount path in the opposite order, should look like

>  mount -t vfat /dev/hda2 /media/E 

---

### Post by shlomik on 2004-12-03
I am in root mode so this isn't the problem

whan I do
fdisk -l 

I get this:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2468    19824178+   c  W95 FAT32 (LBA)
/dev/hda2            2469        7476    40226760    f  W95 Ext'd (LBA)
/dev/hda5            2469        4309    14787801    b  W95 FAT32
/dev/hda6            4310        6454    17229681    b  W95 FAT32
/dev/hda7            7347        7476     1044193+  82  Linux swap
/dev/hda8            6455        7346     7164958+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9461    75995451    c  W95 FAT32 (LBA)
/dev/hdb2            9462        9733     2184840    f  W95 Ext'd (LBA)
/dev/hdb5            9462        9733     2184808+   b  W95 FAT32


so if I mount hda5 or hda6 it's works but hda2 is extended how does I mount it?

---

### Post by diebels on 2004-12-03
You don't mount extended partitions. You mount the logical partitions inside the extended partition.

---

### Post by wangwei on 2004-12-03
[QUOTE=shlomik]
so if I mount hda5 or hda6 it's works but hda2 is extended how does I mount it?[/QUOTE]

extended partition cann't be mounted.

---

### Post by rikkulinux on 2004-12-03
[QUOTE=wangwei]extended partition cann't be mounted.[/QUOTE]

Is this true?!...

-rikku

---

### Post by M@t on 2004-12-03
You might try the following:
```
mount -t vfat /dev/hda5 /media/E
mount -t vfat /dev/hda6 /media/E
``` 
hda2 is not a FAT32 partition but an extended one. hda5 to hda8 are included in the extended hda2 partition, you don't have any reason to mount hda2.

---

