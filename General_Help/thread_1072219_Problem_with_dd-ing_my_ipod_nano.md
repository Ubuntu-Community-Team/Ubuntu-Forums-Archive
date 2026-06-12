---
title: "Problem with dd-ing my ipod nano"
date: 2009-02-17
forum: General Help
---

### Post by Free4Eternity on 2009-02-17
Hi all,
I have been trying to manually install ipodlinux (I am just curious, and the installation program doesn't work for me). I have been told to backup the native firmware by the following command:
```
dd if=/dev/sdb1 of=ipod_os_partition_backup
```
it used to keep giving me the following error.
```
dd: reading `/dev/sdd1': Input/output error
```
Out of frustration, I abandoned the project for a few days, restored the firmware and used my ipod as I did. A few days ago, I tried backing-up the firmware again, and this time, it worked. However, I mistakenly deleted the file, and I only realised it after I rewrote the partition table. I therefore had to start again, but then the error came again, and I cannot get rid of it no matter how I try.

Any ideas?

---

### Post by caljohnsmith on 2009-02-17
Are you running the "dd" command as root user? If not, try putting a "sudo" in front of it.

---

### Post by Free4Eternity on 2009-02-17
I did try, with both my normal account and as root, but to no avail.

---

### Post by wu-stix on 2009-02-18
I have used gtkpod and banshee for ipod 120Gb with no problems.  Not as many features as itunes though it gets the music and playlists on there.  I would suggest gtkpod though if you cant get your program to work.

---

### Post by Free4Eternity on 2009-02-18
Thanks for the suggestion. Guess I'll try it someday...though I just really want to make this work...

---

### Post by caljohnsmith on 2009-02-18
How about with your IPod plugged in, please post the output of:
```
sudo fdisk -lu
```

---

### Post by Free4Eternity on 2009-02-19
Okay. What I got is
```

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12d012d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   311837714   155918826   83  Linux
/dev/sda2       311837715   320159384     4160835    f  W95 Ext'd (LBA)
/dev/sda5       311837778   320159384     4160803+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ff81ff7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    63826244    31913091    7  HPFS/NTFS
/dev/sdb2        63826245    78156224     7164990   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x926b192a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625137344   312568641    b  W95 FAT32

Disk /dev/sdd: 2047 MB, 2047868416 bytes
248 heads, 62 sectors/track, 260 cylinders, total 3999743 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63      160649       80293+   0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(9, 254, 63) logical=(10, 111, 8)
Partition 1 does not end on cylinder boundary.
/dev/sdd2          160656     3999742     1919543+   b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(10, 0, 7) logical=(10, 111, 15)
Partition 2 has different physical/logical endings:
     phys=(248, 247, 62) logical=(260, 31, 61)

```

---

### Post by caljohnsmith on 2009-02-19
So is the 40 GB sdb drive your IPod? If so, how about posting:
```
sudo mount /dev/sdb1 /mnt && ls -l /mnt | head
```

---

### Post by Free4Eternity on 2009-03-13
Thank you everyone for your help. I abandoned the project again two weeks ago due to increasing homework stress. Yesterday, I tried again, and dd-ing worked again. So I make a zillion backups of it, and it is now fine. Thanks again, guys.

---

