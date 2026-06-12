---
title: "Mount Ubuntu partition in D-Lenny"
date: 2009-03-11
forum: General Help
---

### Post by utnubuuser on 2009-03-11
Hi -- Any chance I could get some help mounting my Ubuntu /home partition in Lenny?  (not as the /home partition for Lenny - just to be able to access the data.)

8.04/Lenny dual boot****

---

### Post by MaxIBoy on 2009-03-11
Sure. Boot in Ubuntu, run this:
```
cat /etc/fstab | grep /home
```You should get a single line of text with the configuration of your system for how to handle that partition.

Save that line of text to a flash drive or something, and boot into Debian.

As root, edit paste the line into /etc/fstab again, but (this is important) **change the /home mount point to something else!** 

After that, just type "mount /dev/whatever" and it'll work.

---

### Post by utnubuuser on 2009-03-11
Thanks, but...

That worked in Lenny, but not in Hardy Heron.

In Lenny, cat /etc/fstab | grep /home produces the desired effect, but not in Hardy Heron.

This is the output of fdisk -l> brad@brad-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f614f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          43      345366   83  Linux
/dev/sda2              44        4870    38772877+   5  Extended
/dev/sda5            3259        4870    12948390   83  Linux
/dev/sda6            2009        3153     9197181   83  Linux
/dev/sda7            3154        3258      843381   82  Linux swap / Solaris
/dev/sda8              44         651     4883697   83  Linux
/dev/sda9             652        1016     2931831   83  Linux
/dev/sda10           1017        1145     1036161   82  Linux swap / Solaris
/dev/sda11           1146        1194      393561   83  Linux
/dev/sda12           1195        2008     6538423+  83  Linux

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 2030 MB, 2030043136 bytes
179 heads, 52 sectors/track, 106 cylinders
Units = cylinders of 9308 * 2048 = 19062784 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           6       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 12)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(5, 31, 43)
Partition 1 does not end on cylinder boundary.
/dev/sdb2               6         107     1886072    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(5, 31, 44)
Partition 2 has different physical/logical endings:
     phys=(61, 178, 52) logical=(106, 88, 7)
brad@brad-desktop:~$ 


Ubuntu is on 5,6,and 7,  Lenny the rest.
The partitioning is kinda wonky, but it works.
My Ubuntu /home partition is hda5, but when I try to mount it, I get the error message saying "Cannot mount volume, you are not privileged to mount this volume.
My Ubuntu and Debian passwords/usernames are the same.
Is it just a matter of doing a "mkdir /dev/hda5" and then a  "mount /dev/hda5"?

---

### Post by utnubuuser on 2009-03-11
Got it!  Solved.

Added an entry to /etc/fstab> /dev/hda5  /adir ext3 defaults 0  2 (which is essentially how the other /home partition was listed, and "/adir" since I couldn't call it /home)
then > cd /mnt
and mkdir adir
then restart

---

### Post by MaxIBoy on 2009-03-11
Glad you got it working.

---

