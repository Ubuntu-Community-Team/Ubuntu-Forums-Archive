---
title: "Filesystem/partitions question"
date: 2009-05-02
forum: General Help
---

### Post by kcredden on 2009-05-02
Hey folks. I'd like a bit of help in re-partitioning my system. 

I've enclosed a copy of a Fdisk -l printout of my system (on the bottom):  SDa is an encrypted PATA drive for business records and such. 

SDb is my boot drive, with Kubuntu 8.04 on /sdb1
SDB5 is my /Home partition

SDc is used mainly for a storage drive (with static data, like MP3s). I have that on SDc1. SDc5 is the swap drive

Right now, SDc1 is being used as /USR, in which I also add /private, and /public for my storage files. 

What I want to do, is put the /USR files, on the SDb1 partition, use the remainder of SDb as /HOME, and then make the SDc1 partition as a pure storage drive.  

I have gPARTED, but would it be easier to wipe, and re-partition the drives? I know how to manually re-partition the drives (which is how I got this current config.) But I'm not sure yet how to do as I wish above. The partitioner on the installer doesn't quite make it clear how to do this. 

Can you help?

- Kc

-- Fdisk -l printout

255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb13d59ea

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e45b14c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433       24321   175823392+   5  Extended
/dev/sdb5            2433       24321   175823361   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a1f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38536   309540388+  83  Linux
/dev/sdc2           38537       38913     3028252+   5  Extended
/dev/sdc5           38537       38913     3028221   82  Linux swap / Solaris

---

