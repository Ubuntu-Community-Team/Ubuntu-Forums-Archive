---
title: "Having trouble mounting hard drive"
date: 2007-03-20
forum: Desktop Environments
---

### Post by chejrw on 2007-03-20
Hey everyone.  Hopefully one of you can help me out.  A buddy of mine was having problems with their hard drive, so I offered to try to pull their files off of it.  I've run into some snags.

Ubuntu recognizes the drive in the device manager, and it shows up in the computer places, but when I try to access it, I get the following error:

> 
Unable to mount the selected volume.

error: device /dev/hdd1 is not removable

error: could not execute pmount


fdisk -l gives me:

```


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7178    57657253+   7  HPFS/NTFS
/dev/hda2            7179        8453    10241437+   b  W95 FAT32
/dev/hda3            9696        9729      273105    5  Extended
/dev/hda4            8454        9695     9976365   83  Linux
/dev/hda5            9696        9729      273073+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3647    29294496    7  HPFS/NTFS

```

The second drive with just the NTFS partition is the one I'm hacing trouble with.

Any suggestions?

---

### Post by taurus on 2007-03-20
From a terminal, run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/hhd1
sudo mount -t ntfs /dev/hdd1 /media/hdd1 -o nls=utf8,umask=0222
df -h
```

---

### Post by chejrw on 2007-03-20
oh, that may have worked.  Thanks.

Now to see if I can actually read any data of this drive.

---

