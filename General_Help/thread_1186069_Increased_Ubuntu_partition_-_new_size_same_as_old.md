---
title: "Increased Ubuntu partition - new size same as old"
date: 2009-06-13
forum: General Help
---

### Post by VMC on 2009-06-13
Below is some info on the subject. I increase my Ubuntu partition , but new size is not recongnized. Anyone have ideas. I only have one partitions "/". All the info except df reflect the new size. Interestingly, Gparted shows that I have new size but made it appear that I have now used over 9GB of data!?

========================
vmc@vmc-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             [COLOR="Red"]**3.7G**[/COLOR]  2.5G  1.1G  70% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
varrun               1006M   96K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
udev                 1006M  148K 1006M   1% /dev
tmpfs                1006M   76K 1006M   1% /dev/shm
lrm                  1006M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
======================================================================================
vmc@vmc-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc701877d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         657     5277321    7  HPFS/NTFS
/dev/sda2            2276       30401   225922091+   7  HPFS/NTFS
/dev/sda3             658        2116    [COLOR="Red"]**11719417**[/COLOR]+  83  Linux
/dev/sda4            2117        2275     1277167+   5  Extended
/dev/sda5            2117        2275     1277136   82  Linux swap / Solaris
=======================================================================================
                                    cfdisk (util-linux-ng 2.14.2)

                                        Disk Drive: /dev/sda
                                 Size: 250059350016 bytes, 250.0 GB
                        Heads: 255   Sectors per Track: 63   Cylinders: 30401

     Name           Flags         Part Type    FS Type               [Label]           Size (MB)
 ---------------------------------------------------------------------------------------------------
     sda1           Boot           Primary     NTFS                                      5404.01
     sda3                          Primary     Linux ext3                               [COLOR="Red"]**12000.69**[/COLOR]
     sda5                          Logical     Linux swap / Solaris                      1307.82
                                   Logical     Free Space                                   0.01    *
     sda2                          Primary     NTFS                  []                231344.23    *

====================
vmc@vmc-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  244198584 sda
   8        1    5277321 sda1
   8        2  225922091 sda2
   8        3   [COLOR="Red"]**11719417**[/COLOR] sda3
   8        4          1 sda4
   8        5    1277136 sda5
=====================
vmc@vmc-desktop:~$ cat /proc/diskstats
   1       0 ram0 0 0 0 0 0 0 0 0 0 0 0
   1       1 ram1 0 0 0 0 0 0 0 0 0 0 0
   1       2 ram2 0 0 0 0 0 0 0 0 0 0 0
   1       3 ram3 0 0 0 0 0 0 0 0 0 0 0
   1       4 ram4 0 0 0 0 0 0 0 0 0 0 0
   1       5 ram5 0 0 0 0 0 0 0 0 0 0 0
   1       6 ram6 0 0 0 0 0 0 0 0 0 0 0
   1       7 ram7 0 0 0 0 0 0 0 0 0 0 0
   1       8 ram8 0 0 0 0 0 0 0 0 0 0 0
   1       9 ram9 0 0 0 0 0 0 0 0 0 0 0
   1      10 ram10 0 0 0 0 0 0 0 0 0 0 0
   1      11 ram11 0 0 0 0 0 0 0 0 0 0 0
   1      12 ram12 0 0 0 0 0 0 0 0 0 0 0
   1      13 ram13 0 0 0 0 0 0 0 0 0 0 0
   1      14 ram14 0 0 0 0 0 0 0 0 0 0 0
   1      15 ram15 0 0 0 0 0 0 0 0 0 0 0
  11       0 sr0 0 0 0 0 0 0 0 0 0 0 0
   8       0 sda 8845 39472 592941 228368 479 969 11672 4252 0 22964 232616
   8       1 sda1 41 595 1860 368 0 0 0 0 0 288 368
   8       2 sda2 39 1079 1118 568 0 0 0 0 0 436 568
   8       3 sda3 8702 37609 587965 226804 422 969 11672 4136 0 22836 230936
   8       4 sda4 3 0 6 120 0 0 0 0 0 120 120
   8       5 sda5 39 170 1672 356 0 0 0 0 0 336 356
   2       0 fd0 0 0 0 0 0 0 0 0 0 0 0

---

### Post by dcstar on 2009-06-13
> **VMC said:**
> Below is some info on the subject. I increase my Ubuntu partition , but new size is not recongnized. Anyone have ideas. I only have one partitions "/". All the info except df reflect the new size. Interestingly, Gparted shows that I have new size but made it appear that I have now used over 9GB of data!?
.........

I have previously seen in the forums the command to fix this sort of thing, you should be able to eventually find it by searching for the problem terms.

---

### Post by VMC on 2009-06-13
> **dcstar said:**
> I have previously seen in the forums the command to fix this sort of thing, you should be able to eventually find it by searching for the problem terms.I did in fact search for an answer. That's why I left a topic. There's been plenty of questions similar to this but none that worked.

---

### Post by merlinus on 2009-06-13
sudo fdisk /dev/sda
press **x** to enter expert mode
press **f** to fix partition order
press **w** to write the partition table changes to disk

But you may wish to back up critical data just in case....

---

### Post by dcstar on 2009-06-13
> **VMC said:**
> I did in fact search for an answer. That's why I left a topic. There's been plenty of questions similar to this but none that worked.

If you had bothered to tell all of us what you have actually tried, then we would know that, wouldn't we?

I have seen people solve this problem previously, and someone who actually has the answer may have been able to offer it if they had seen that you had tried that didn't work.

---

### Post by VMC on 2009-06-13
> **merlinus said:**
> sudo fdisk /dev/sda
press **x** to enter expert mode
press **f** to fix partition order
press **w** to write the partition table changes to disk

But you may wish to back up critical data just in case....

Thank you Merlinus!

Edit: Merlinus. Actually you answered a question here that I didn't ask but wondered about before. Now my disk are in order and the message telling me that they are out of order is gone. Thanks for that.

The fix for my mismatch in size was the **resize2fs** command. I finally figured that out on my own.

---

### Post by merlinus on 2009-06-14
Glad it worked, and thanks for the **resize2fs** command.  Good to know...

---

