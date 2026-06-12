---
title: "hard drive error (FAT32)"
date: 2009-03-18
forum: General Help
---

### Post by slimx3m on 2009-03-18
my disk got corrupt so i decided to format it from NTFS to FAT32.  now that i run a check i got the following error message.

any thoughts on how this could be fixed?

```
GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (fat32) on /dev/sdb1  00:03:09    ( ERROR )
     	
calibrate /dev/sdb1  00:00:14    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 80292869
size: 80292807 (38.29 GiB)
check filesystem on /dev/sdb1 for errors and (if possible) fix them  00:01:08    ( SUCCESS )
     	
dosfsck -a -w -v /dev/sdb1
     	
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
87:3c/20, 89:88/20, 91:0f/1f, 94:ea/7c, 96:23/22, 97:2b/c0, 143:68/69
, 144:b3/73, 145:5a/6b, 146:5c/2e, 147:d0/20, 151:67/65, 153:19/73
, 155:3c/20, 156:d9/69, 422:10/00, 441:03/00, 442:f0/00, 506:3e/00
Not automatically fixing this.
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
16384 bytes per cluster
32 reserved sectors
First FAT starts at byte 16384 (sector 32)
2 FATs, 32 bit entries
10032128 bytes per FAT (= 19594 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 20080640 (sector 39220)
2507924 data clusters (41089826816 bytes)
63 sectors/track, 255 heads
63 hidden sectors
80292806 sectors total
Got 9633792 bytes instead of 10031704 at 16384
grow filesystem to fill the partition  00:01:47    ( ERROR )
     	
using libparted
libparted messages    ( INFO )
     	
File system is reporting the free space as 2507923 clusters, not 2507813 clusters.

========================================

```

---

### Post by LiamWilson on 2009-03-18
Well if it got corrupted, changing the filesystem isn't going to do much. Can you even open the hard drive in nautilitus?

---

### Post by slimx3m on 2009-03-18
yes, i can.  i am actually able to open the drive and navigate through it with no problems.  the problem comes whenever i try to access certain files and the drive behavior is really, really slow.  so i tried to do a check and that is the outcome that i get.

---

### Post by LiamWilson on 2009-03-18
What you may have to do is take all important files/folders from the hard drive and format it. BUT ONLY USE THIS AS A LAST RESORT. There is probably another option, so only use this as a Final Option!!

---

### Post by slimx3m on 2009-03-18
> **LiamWilson said:**
> What you may have to do is take all important files/folders from the hard drive and format it. BUT ONLY USE THIS AS A LAST RESORT. There is probably another option, so only use this as a Final Option!!

i already did that.  i think that i am just going to format it since i extract "all my data" (hopefully) already.  but, i am going to wait and see if it is fixable first.

thanks for your help.

---

### Post by slimx3m on 2009-03-18
ok... now literally i am fkd'

i tried to fix the hard drive that it was bad by formatting it and then the other hard drive just went crazy on my.  it confused itself and it didn't know that it was the main drive.  so i bootup with gparted and ran this command ```
e2fsck -b 32768 /dev/sda1
``` and then it gave me an error on a block.  apparently it fixed it but now when i boot i get a error message saying "PLEASE INSERT THE DISK..." or something like that.

any thoughts would be appreciated. 

thanx in advance

---

### Post by cariboo on 2009-03-19
Give [thread=224351]this [/thread] a try to see if you can restore your mbr.

Jim

---

### Post by slimx3m on 2009-03-23
> **cariboo907 said:**
> Give [thread=224351]this [/thread] a try to see if you can restore your mbr.

Jim
thnx for the information... but i think that i  am going to close this thread since my hard drive has died.

whenever i bootup with a live CD sometimes it tells me the wrong amount of hard drive space or it will not boot up at all even form the live CD.

thnx again for your help.

---

