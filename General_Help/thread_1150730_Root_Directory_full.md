---
title: "Root Directory full"
date: 2009-05-06
forum: General Help
---

### Post by randome20170520 on 2009-05-06
I received the error 'unable to to write mmap msync 28' when using synaptic package manager.  I did some searching on the forums, and cleaned off my hard disk to free up the root partition.  The gnome disk usage analyzer says my root partition is still full...but df shows only 9% full. 

The machine seems to be running OK on Ubuntu 9.04. Please tell me what am I overlooking?

df 

/dev/sda2             48062468   3895500  41725492   9% /
tmpfs                   998036         0    998036   0% /lib/init/rw
varrun                  998036       324    997712   1% /var/run
varlock                 998036         0    998036   0% /var/lock
udev                    998036       172    997864   1% /dev
tmpfs                   998036         0    998036   0% /dev/shm
lrm                     998036      2392    995644   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6            103754904  87985764  10498620  90% /mnt/storage


 sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        6086    48829567+  83  Linux
/dev/sda3            6087       19452   107362395    5  Extended
/dev/sda5            6087        6329     1951866   82  Linux swap / Solaris
/dev/sda6            6330       19452   105410466   83  Linux

---

