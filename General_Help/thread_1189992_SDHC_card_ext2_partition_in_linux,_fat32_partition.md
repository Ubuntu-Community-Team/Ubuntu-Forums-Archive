---
title: "SDHC card: ext2 partition in linux, fat32 partition in windows"
date: 2009-06-17
forum: General Help
---

### Post by Sycron on 2009-06-17
I have a 8GB SDHC card. I'll install ubuntu on it and i want a second partition on it for windows.

I need something like this:
SDHC 8GB
[LIST]
[*]sdb1 ext2 ubuntu 7.2GB
[*]sdb2 fat32 616mb
[/LIST]

I've formated the card like above and windows can't recognize the fat partition. When I click on H: it will get stucked and I have to restart explorer.

The other things are fine.

---

### Post by sedawk on 2009-06-17
What is the output of 
```

sudo fdisk -l /dev/sdb

```

---

### Post by Sycron on 2009-06-17
```
Disk /dev/sdb: 7850 MB, 7850164224 bytes
255 heads, 63 sectors/track, 954 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00019168

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         879     7060536   83  Linux
/dev/sdb2             880         954      602437+   5  Extended
/dev/sdb5             880         954      602406    b  W95 FAT32
```

---

### Post by sedawk on 2009-06-21
This looks fine (Type of partition sdb5 is okay).

Which version of windows are you using?

When inserting the stick to ubuntu is 
sdb5 mounted correctly as (v)fat partition?

---

### Post by ralyon on 2009-07-02
From the older USB thumb drive instructions there were instructions for doing something like this and the issue was that windows only looks at the first partition on a usb drive. The trick is to put the fat32 partition as the first one and install ubuntu on the second one or any partitions after the first.

Windows will still continue to only see the first one however so you will not be able to access any files beyond the first one.

ralyon

---

