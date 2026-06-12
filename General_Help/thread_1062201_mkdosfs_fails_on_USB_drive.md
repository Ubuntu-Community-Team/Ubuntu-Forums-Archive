---
title: "mkdosfs fails on USB drive"
date: 2009-02-06
forum: General Help
---

### Post by bixejo on 2009-02-06
Ok, I've got a 4Gb USB drive that after making partitions with fdisk looks like the following:

> 
# fdisk /dev/sdb
Note: sector size is 2048 (not 512)

Command (m for help): p

Disk /dev/sdb: 4255 MB, 4255645696 bytes
131 heads, 62 sectors/track, 255 cilindros
Units = cilindros of 8122 * 2048 = 16633856 bytes
Disk id: 0x428ad130

Device.      Boot    Start      End      Blocks       Id  System
/dev/sdb1   *           1         255     4142096    b  W95 FAT32
(**NOTE:** I'm trying to translate most of this stuff into English)

I tried to create a FAT32 filesystem in this device with:

> 
# mkdosfs -n MYFLASH /dev/sdb1
And it ran without apparent problems. But whenever I try to mount this device I get:

> 
# mount -t vfat /dev/sdb1 /media/tests
/dev/sdb1: Cannot read superblock
Same results with -t msdos. Windows systems cannot either read this USB drive (they all suggest me to format it).

The point is that if I try it with a simulated filesystem (made in a regular file) I get no problems. For example:

> 
# dd bs=4096 count=1048576 if=/dev/zero of=test_filesystem
# mkdosfs -n MYFLASH ./test_filesystem 
# mount -t vfat -o loop ./test_filesystem /media/tests
All this works without apparent problems. I can even create/read/write/modify files within /media/tests.

I get no problems like these when I create ext[2|3] filesystems in this USB drive.

Any clue about this?

Thank you in advance,

---

