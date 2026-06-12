---
title: "Second hard disk not detected"
date: 2012-03-11
forum: Desktop Environments
---

### Post by Corvair on 2012-03-11
Hello everyone.

I have a seagate 500 Gb hard drive for my OS 10.04.3. I have added recently a second hard drive Wd 500 Gb  and it is detected on the Bios. But when I run the OS the second hard drive is not detected. I look on "computer" and it does not show. I want to use the second drive for backup. The first WD drive I bought was detected but it gave up after a few weeks after giving me all sorts of problems. The seller replaced it with another new drive. This one I can see also on the BIOS but it does not show on "computer".

I have an ASUS PK5 Premium mobo with ubuntu 10.04.3. Is there something in the BIOS or in the OS that should be set up differently or would it be the WD disk that is at fault again?

Thank you

---

### Post by lindsay7 on 2012-03-11
I would run Gparted and it should see the drive in question. Look under the device drop down menu and reset up a new partition table. Then format the partitons as you would like. Hopefully this will solve your problem.

---

### Post by Corvair on 2012-03-11
I have installed gparted on terminal and now I can't get any further.
Could you be more explicit?
I still do not see the hardisk.

claude@claude-desktop:~$ gparted
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon
claude@claude-desktop:~$

---

### Post by Corvair on 2012-03-11
claude@claude-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ba93ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59326   476536063+  83  Linux
/dev/sda2           59327       60801    11847937+   5  Extended
/dev/sda5           59327       60801    11847906   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
claude@claude-desktop:~$

---

### Post by oldfred on 2012-03-11
Root is UID 0, so this is saying to use sudo. But with graphical applications you should use gksu or gksudo.

 Only uid 0 is authorized 

gksu gparted

You can run gparted from your install where most of the time we have to suggest using liveCD as you cannot edit the partition(s) that are mounted or those you are running gparted from. But since you are modifying another drive, you should not have that issue.

---

### Post by Corvair on 2012-03-11
Case solved.

Thank you for your help.
I went to System-disk utility and the new disk was listed.
So I formatted it and now it is visible as new volume.
Thanks again

---

