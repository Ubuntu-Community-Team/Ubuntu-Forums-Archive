---
title: "Misreported Free Space"
date: 2006-06-29
forum: Desktop Environments
---

### Post by magii on 2006-06-29
I recently increased my ext3 main ubuntu partition from 30gb to 60 gb using gparted from the live cd...  Upon rebooting I found that I was reporting free space as though I hadn't increased the size....  

sudo fdisk -l gives the following:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/hda2            9632        9733      819315    5  Extended
/dev/hda3            1825        9631    62709727+  83  Linux
/dev/hda5            9632        9733      819283+  82  Linux swap / Solaris

while df -h reports:
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              32G   22G  8.5G  72% /
varrun                125M  136K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
udev                  125M  116K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   19M  107M  15% /lib/modules/2.6.15-25-386/volatile
/dev/hda1              14G  4.6G  9.5G  33% /media/ntfs
//familyroom/network   75G   22G   54G  29% /media/network
//familyroom/shareddocs
                       75G   22G   54G  29% /media/shareddocs


As a linux newbie I'm not sure where to start but boy I sure could use that extra space!

---

