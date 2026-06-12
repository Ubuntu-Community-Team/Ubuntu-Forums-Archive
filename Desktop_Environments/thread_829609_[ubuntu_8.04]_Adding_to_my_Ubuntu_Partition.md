---
title: "[ubuntu 8.04] Adding to my Ubuntu Partition"
date: 2008-06-15
forum: Desktop Environments
---

### Post by jeff369 on 2008-06-15
Hi, first timer, but I have had a great experience with Linux so far so I have decided to dive in head first......

  My problem is that I had first setup my computer to duel boot vista and ubuntu. It worked, I would turn on the computer and choose between then two and then go on my way. However, since I have liked linux so much I wanted to delete vista and increase ubuntu to my entire hard disk. I used gparted and got vista removed, and then formatted the left over space to the ubuntu partition. The open space and the ubuntu were tagged the same after formatting so I thought I was in the clear. I rebooted and Ubuntu booted clean, no Vista in sight. The only problem is that my Home folder is still showing the old hard disk size. How can I either merge, or check the status of my hard disk?

Thank You.

---

### Post by logos34 on 2008-06-15
post some info:

sudo fdisk -l

df -h

---

### Post by jeff369 on 2008-06-15
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13133   105490791   83  Linux
/dev/sda2           13134       37863   198643725   83  Linux
/dev/sda3           37864       38913     8434125    5  Extended
/dev/sda5           37864       38913     8434093+  82  Linux swap / Solaris

Disk /dev/sdb: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         979      250574+   6  FAT16
jeff@jeff-desktop:~$

---

### Post by jeff369 on 2008-06-15
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         979      250574+   6  FAT16
jeff@jeff-desktop:~$ 
jeff@jeff-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             187G  6.2G  171G   4% /
varrun                1.5G  100K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   20K  1.5G   1% /dev/shm
lrm                   1.5G   38M  1.5G   3% /lib/modules/2.6.24-18-generic/volatile
/dev/sdb1             245M  5.9M  239M   3% /media/disk
jeff@jeff-desktop:~$

---

### Post by logos34 on 2008-06-15
It appears sda1, the newly formatted ext3 partition formerly occupied by windows, is not mounting.  You apparently did not [edit fstab]("http://www.psychocats.net/ubuntu/mountlinux") (i.e. take out the windows line, if there, and replace it with new ext3 entry with new UUID).

Do that, or if you want enlarge root to take up that space instead, boot from the ubuntu live cd, delete sda1, and grow sda2 to the front of the disk. 

You could also turn it into a [separate /home]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by jeff369 on 2008-06-16
k, thanks a ton, solved

---

