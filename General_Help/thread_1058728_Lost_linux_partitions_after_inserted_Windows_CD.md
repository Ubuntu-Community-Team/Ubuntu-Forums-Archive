---
title: "Lost linux partitions after inserted Windows CD"
date: 2009-02-03
forum: General Help
---

### Post by knh94 on 2009-02-03
Can't booting ubuntu after inserted Windows CD. Windows not install. work is noting.
So, Check partitions after booting Ubuntu CD.

Linux partitions is losted... Forced convert to FAT16
Help me.

notice: Only installed Ubuntu 8.10 on my computer.

Informations
Size: Swap < Root(EXT3) < Other(NTFS)

ubuntu@ubuntu:~$ cat /proc/partitions
major minor #blocks name

254 0 126500 ramzswap0
8 0 57387753 sda
8 1 1 sda1
8 2 36893241 sda2
8 5 20474811 sda5
7 0 691600 loop0

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 58.7 GB, 58765059072 bytes
255 heads, 63 sectors/track, 7144 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd380d380

Device Boot Start End Blocks Id System
/dev/sda1 2 2550 20474842+ f W95 Ext'd (LBA)
/dev/sda2 * 2551 7143 36893241 7 HPFS/NTFS
/dev/sda5 2 2550 20474811 e W95 FAT16 (LBA)

---

### Post by eotakos on 2009-02-03
Hi!

windows's tricks messing up with the partitions is something that happened to me a couple of months ago. check this thread out: 

[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

in the beginning the discusion is about using testdisk correctly to restore partitions, and the second half is about fine tuning of the partition table so that everything is exactly as it is supposed to be.

make sure to read and understand exactly what you are about to do, because messing up with the partition table is serious business. making a mistake is as good as risking your data.

should you have any further questions post again.

---

