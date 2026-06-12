---
title: "Grub and windows xp 64bit - won't boot"
date: 2006-09-22
forum: Desktop Environments
---

### Post by devilkin on 2006-09-22
Hello all,

I've got the latest kubuntu installed on my pc, next to my windows XP 64bit.

Linux boots fine, windows won't. It keeps hanging after displaying 

```

rootnoverify    (hd0,0)
savedefault
makeactive
chainloader +1
```

After this I only see a blinking cursor, windows won't load. :confused: 

I can get it back by restoring the MBR, but then I lose linux, which isn't what I intend :/

I've tried several iterations of the grub settings, but I just can't get it to work. Anyone got any pointers or hints that I can try?

Thanks,

Jan


The GRUB section for win64 looks like this:
```

title           Windows XP Professional x64 Edition
rootnoverify    (hd0,0)
#savedefault
makeactive
chainloader +1

```

Partition table:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        20964825    22924754      979965   82  Linux swap / Solaris
/dev/sda3        22924755    22989014       32130   83  Linux
/dev/sda4        22989015   122929379    49970182+   f  W95 Ext'd (LBA)
/dev/sda5        22989078    23985044      497983+  83  Linux
/dev/sda6        23985108    25254179      634536   83  Linux
/dev/sda7        25254243    44789219     9767488+  83  Linux
/dev/sda8        44789283    54556739     4883728+  83  Linux
/dev/sda9        54556803    74091779     9767488+  fd  Linux raid autodetect
/dev/sda10       74091843    83859299     4883728+  fd  Linux raid autodetect
/dev/sda11       83859363   122929379    19535008+  fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78220484    39110211    7  HPFS/NTFS
/dev/sdb2        78220485    80180414      979965   82  Linux swap / Solaris
/dev/sdb3        80180415    99715454     9767520   fd  Linux raid autodetect
/dev/sdb4        99715455   258550109    79417327+   f  W95 Ext'd (LBA)
/dev/sdb5        99715518   109482974     4883728+  fd  Linux raid autodetect
/dev/sdb6       109483038   148553054    19535008+  fd  Linux raid autodetect
/dev/sdb7       148553118   158545484     4996183+  83  Linux
/dev/sdb8       158545548   258550109    50002281    b  W95 FAT32
```

Edit: I've read something about possibly setting the bios to use LBA mode, but I've only got LARGE and Automatic... Motherboard is an Abit KN9-SLI

---

### Post by catlett on 2006-09-23
Are you sure windows is on /dev/hda1 and not /dev/hdb1? Both your drives have ntfs partitions with boot flags
```
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
```
```
/dev/sdb1   *          63    78220484    39110211    7  HPFS/NTFS
```
The entry you are using, sends the boot to /dev/sda1.
Since it isn't working, try sending the boot to /dev/sdb1.
```
sudo kwrite /boot/grub/menu.lst
```
```
title           Windows XP Professional x64 Edition
rootnoverify    (hd1,0)
makeactive
chainloader +1
```
Try that and see what happens.

---

### Post by devilkin on 2006-09-24
Yes, quite sure. The /dev/sdb1 one isn't even formatted as ntfs yet - It's still an ext3 (which I used as a temp backup storage space for a while) that I want to format to ntfs as soon as I get a windows booted.

Jan

---

### Post by devilkin on 2006-09-24
In a vague attempt i just reinstalled the win64bit, and then re-installed grub using grub-install /dev/sda. No dice.

Tried the same but with --force-lba. No dice.

---

### Post by devilkin on 2006-09-24
And I'm pretty sure my setup is correct: LILO works! Yay! :)

---

