---
title: "External hard drive wont work"
date: 2009-03-07
forum: General Help
---

### Post by StarThorn1 on 2009-03-07
I had myth/unbuntu distro before. My hard drive worked on it. I installed the real Unbuntu then boxee. I tried to plug in my external drive but it gave me the error message about not being able to mount it.  Something to do with NTFS...



so how do I get it working so I can put my video files on it?

---

### Post by taurus on 2009-03-07
With your external drive still plugged in, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by StarThorn1 on 2009-03-07
before I do that...what does it do? I dont want to format it or anything. I have all my stuff backed up on my drive right now.

---

### Post by DeMus on 2009-03-07
> **taurus said:**
> With your external drive still plugged in, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

No no, it won't format or repartition or anything. It just gives information about all the disks in, or connected to, your computer.
You will get a list like this: (with other info of course)

jan@2-Quad:~$ sudo fdisk -l
[sudo] password for jan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b328b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       58132   441345712+   7  HPFS/NTFS
/dev/sda3           58133       60801    21438742+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b6e8b6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        3648     9767520   83  Linux
/dev/sdb3            3649        4864     9767520   83  Linux
/dev/sdb4            4865       60801   449313952+   5  Extended
/dev/sdb5            4865        5362     4000153+  82  Linux swap / Solaris
/dev/sdb6            5363       60801   445313736   83  Linux
jan@2-Quad:~$

---

### Post by StarThorn1 on 2009-03-08
> **DeMus said:**
> No no, it won't format or repartition or anything. It just gives information about all the disks in, or connected to, your computer.
You will get a list like this: (with other info of course)

jan@2-Quad:~$ sudo fdisk -l
[sudo] password for jan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b328b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       58132   441345712+   7  HPFS/NTFS
/dev/sda3           58133       60801    21438742+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b6e8b6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        3648     9767520   83  Linux
/dev/sdb3            3649        4864     9767520   83  Linux
/dev/sdb4            4865       60801   449313952+   5  Extended
/dev/sdb5            4865        5362     4000153+  82  Linux swap / Solaris
/dev/sdb6            5363       60801   445313736   83  Linux
jan@2-Quad:~$

Disk /dev/sda: 40.0 GB 
255 heads 63 sectors/tracks,  4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b351b19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83   Linux
/dev/sda2            4661       4865   1646662+    5  Extended
/dev/sda3            4661       4865    1646631+   82 Linux Swap/ solaris

Disk /dev/sdb: 100.2 GB, 200356292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b2461b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        12187    97892046+  7  HPFS/NTFS



That sucked to type.  Also the error message said something about the drive not being safely removed from an NTFS file system. I plugged it back into my windows box then safely removed it. Still didnt work

---

### Post by StarThorn1 on 2009-03-08
bump

---

### Post by vanadium on 2009-03-08
> That sucked to type. Also the error message said something about the drive not being safely removed from an NTFS file system. I plugged it back into my windows box then safely removed it. Still didnt work
That *is* the cause of the problem. If it did not work, then also have a file system check in Windows, then shut down Windows, and start/stop Windows another time. After that, it will most certainly work.

---

### Post by taurus on 2009-03-08
```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by vanadium on 2009-03-09
ntfsfix is a good suggestion, but if you have Windows, then using Windows to check and repair the disk is preferred. ntfsfix does not know all the ins and the outs of the ntfs file system. It can repair common errors, but not all.

---

