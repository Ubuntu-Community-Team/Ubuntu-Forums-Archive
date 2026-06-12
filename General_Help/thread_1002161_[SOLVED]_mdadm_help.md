---
title: "[SOLVED] mdadm help"
date: 2008-12-04
forum: General Help
---

### Post by sikk on 2008-12-04
Hello,

I have an Ubuntu 8.10 box running 4 x 500GB SATA drives in a software RAID5 cofiguration using mdmadm to administer etc. Additionally I have an old (13GB QUANTUM FIREBALL) IDE drive configured as the boot device.

The issue I have is that since the Ibex upgrade, each time I reboot, the old IDE device moves around (/dev/sda turns into /dev/sdc) and the array looses a drive.

I then need to edit /etc/mdadm/mdadm.conf and remove the offending /dev/sd* device and add the appropriate one and re add the correct drive to the RAID set, and rebuild.

While annoying there is also a risk of data loss which I would like to mitigate.

I have looked into UDEV rules, in the interest of locking down the IDE device to /dev/sda.

But I am wondering if there is a simpler way to achieve this, as I have never poked around in UDEV, and most of the howtos and information are related to USB devices and the like.

Is there a simple solution to my problem?

*My work around was to edit /etc/mdadm/mdadm.conf too look like this.*
```
DEVICE partitions
ARRAY /dev/md0 level=raid5 devices=4, UUID=fb2712f9-0826-4923-b8fa-1f19175f76c4
```

rather than
```
DEVICE partitions /dev/sda1 /dev/sdb1 /dev/sdd1 /sde1 /dev/sda1
ARRAY /dev/md0 level=raid5 devices=/dev/sda1,/dev/sdb1,/dev/sdd1,/dev/sde1,/dev/sda1

```

*This removes the mdadm dependancy on having the correct device names. You can find the correct UUID of the array by using blkid*

```
me@mybox:~$ blkid
/dev/mapper/Media-media_vol: UUID="bbb92994-46e0-4c42-ab1f-240a79fcfddd" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda1: UUID="c6729ef0-e218-398a-26d3-3687bdb49148" TYPE="mdraid"
/dev/sdd1: UUID="c6729ef0-e218-398a-26d3-3687bdb49148" TYPE="mdraid"
/dev/md0: [COLOR="Red"]UUID="fb2712f9-0826-4923-b8fa-1f19175f76c4"[/COLOR] SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="c6729ef0-e218-398a-26d3-3687bdb49148" TYPE="mdraid"
/dev/sdc1: UUID="c6729ef0-e218-398a-26d3-3687bdb49148" TYPE="mdraid"
/dev/sde1: UUID="8a35dd0b-fd7e-44cf-b8c5-f7ecc75804ce" TYPE="ext3"
/dev/sde5: UUID="52644884-021f-42b4-b5b5-cc090828e59c" TYPE="swap"

```

---

