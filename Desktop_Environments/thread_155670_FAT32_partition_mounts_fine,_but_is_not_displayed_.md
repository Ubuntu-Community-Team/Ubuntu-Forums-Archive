---
title: "FAT32 partition mounts fine, but is not displayed in GNOME on startup"
date: 2006-04-05
forum: Desktop Environments
---

### Post by Fafnir on 2006-04-05
OK, so I'm a fairly severe Linux newbie (just moved over from Windows), and this is almost certainly a very stupid question. On the other hand, I've been unable to find anything related to this online, so I suppose it's possible there's no PEBKAC error. BTW, I did verify the checksum of the install CD download, so I doubt there are any corrupted files.

I've got a system with an NTFS partition on the first hard drive (for XP), and two FAT32 partitions (for storage), a swap partition and an ext3 partition (for Ubuntu) on the second. Here's the output from fdisk -l:

```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3648    29302528+   c  W95 FAT32 (LBA)
/dev/hdb2            3649        7579    31575757+   f  W95 Ext'd (LBA)
/dev/hdb3   *        7580       14946    59175427+  83  Linux
/dev/hdb5            3649        7296    29302528+   b  W95 FAT32
/dev/hdb6            7297        7579     2273166   82  Linux swap / Solaris
```

I'm trying to auto-mount the NTFS partition and both FAT32 partitions on boot. To do this, I made a couple of folders in /media and edited /etc/fstab (after making a backup), adding three lines as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[COLOR="Red"]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0 0
/dev/hdb5       /media/data1    vfat    iocharset=utf8,umask=0000 0 0
/dev/hdb1       /media/data2    vfat    iocharset=utf8,umask=0000 0 0[/COLOR]
```

The partitions seem to mount fine on startup, and I can access them as normal. My problem is that only /dev/hdb5 appears on the desktop in GNOME! I've tried different media folders, I've tried changing the line order, I've tried everything I can think of, but no icon appears. And so I have been reduced to begging for help... ](*,) 

Since it's a fairly new installation, I guess it would probably be a good idea to list everything I've done so far:

- Installed all updates using the auto-update thingy in GNOME whose name I do not know (I *think* it's equivalent to apt-get upgrade).

- Followed the [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=75074") on getting nVidia's drivers to work with Ubuntu (using method 2).

- Installed planetpenguin-racer to check that method 2 worked (it did).

- Set up my printer - it didn't autodetect so I selected it manually and it seems to be working.

- Actually, that's pretty much it.

Here's my hardware:

VIA KM400 motherboard
nVidia GeForce 6600GT graphics card
On-board sound card

Please help!

EDIT: There's always SOMETHING you forget... I'm running Breezy Badger.

---

### Post by aysiu on 2006-04-05
Just go to the /media folder and middle-click-drag the appropriate folder to the desktop and select "link here."

---

### Post by dcstar on 2006-04-05
[QUOTE=Fafnir]
......
The partitions seem to mount fine on startup, and I can access them as normal. My problem is that only /dev/hdb5 appears on the desktop in GNOME! I've tried different media folders, I've tried changing the line order, I've tried everything I can think of, but no icon appears. And so I have been reduced to begging for help... ](*,) 
......[/QUOTE]
Check Applications-System Tools-Configuration Editor-Apps-Nautilus-Desktop and see if **volumes_visible** is set.

---

### Post by Fafnir on 2006-04-07
Fixed it! **volumes_visible** *was* set, actually - I have no idea what the problem was, but it went away when I checked whether /dev/hdb1 would automount correctly when I tried it in isolation - strange.... Thanks for the help!

---

