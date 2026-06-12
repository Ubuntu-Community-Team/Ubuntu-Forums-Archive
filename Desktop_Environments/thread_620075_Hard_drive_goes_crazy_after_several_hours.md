---
title: "Hard drive goes crazy after several hours"
date: 2007-11-22
forum: Desktop Environments
---

### Post by afonteijn on 2007-11-22
Just a week ago I made the step from openSUSE to Ubuntu 7.10. Everything will run fine for several hours, but at some unspecified moment the hard drive will start reading/writing like crazy. Music will be interrupted, programs hardly start or close anymore. The only way out is to log off (which takes a long time) and then log in again. Then i have another few hours without troubles.

I have looked through some of the topics on this forum, but I haven't been able to find anything that would solve this problem. I do have a swap file enabled. 
I'm running ubuntu 7.10 386 version.
PC: AMD64 3200+
1Gb mem
More then enough hd space free (over 100gb)

---

### Post by coolguy2006delhi on 2007-11-22
I think  it is the problem of swap partition. You can check whether you have correctly given the size of partition. Also if you can repartition it , then it is well and good.

---

### Post by afonteijn on 2007-11-22
Thanks coolguy2006delhi for your quick reply,

According to gparted /dev/sda1 is a healthy and active linux-swap partition of 1.91 Gb. When I run "free -m" command I see that currently only 82mb is used, 1870mb is still free. As far as I can see, there is nothing wrong with the swap partition.

I forgot to add two other details. When the hd is going crazy the system monitor doesn't show any increased activity. The total cpu load never peaks over 10%. I have also completely turned off the indexing services, because I have had trouble with these kind of programs before. (haven't removed it yet though)

---

### Post by afonteijn on 2007-11-24
Anybody? I'm still having the same problem. Reformatting the swap partition seems a little awkward to me, considering that all programs show a healthy swap partition. But if that is the only way, I might give it a try.

---

### Post by LinuxGuy1234 on 2007-11-24
> **afonteijn said:**
> Anybody? I'm still having the same problem. Reformatting the swap partition seems a little awkward to me, considering that all programs show a healthy swap partition. But if that is the only way, I might give it a try.

Reformat your swap. BTW, what does sudo fdisk -l show?

---

### Post by afonteijn on 2007-11-24
Hi LinuxGuy1234,

Earlier today I ran gparted and repartioned the swap-partition. Didn't help, I just ran into the same problem.

Fdisk-l shows the following:
______________________________________________
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b93f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2            5113       60800   447313860    f  W95 Ext'd (LBA)
/dev/sda3   *         250        5112    39062047+  83  Linux
/dev/sda5            5113       60800   447313828+  83  Linux

Partition table entries are not in disk order
_____________________________________________________
sda2 looks a bit awkward because I never completely reformated my drive after I stopped using windows. Still, I haven't ever ran into any problems since (k)ubuntu 6.10 .

---

### Post by Random-penguin on 2007-11-25
Hi I've been having similar problems to yours. My thinking is that it is due to the indexing and using System Monitor noticed a package Trackerd using a huge amount of my system resources. Is this the cause? It seems that when I googled this package that developers were complaining about this using too much resourses, during the summer. Perhaps this is where the problem lies?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by afonteijn on 2007-12-05
I found out something interesting. I turned of the 3d visual effects and the problem seemingly disappeared, until I started google earth and the PC slowed down very quickly. I have two hypothesis:
- either there is something wrong with the nVidia drivers
- or the 3d applications use more memory, this is transfered to the swap file - so it is still the swap file which is the problem.

I don't know how to improve the swap file, so I'll try to install a nVidia driver from scratch.

Random-penguin: I didn't notice any increase in the system monitor. Trackerd doesn't seem to act weird either. I have already disabled all indexing features.

---

### Post by adam.tropics on 2007-12-05
I would have gone with those suggesting tracker simply because I had a lousy time with it.

That said, you can play with how aggressively swap is used. Seeing how large your swap is, I assume you actually have a fair bit of memory, tuning your 'swappiness' may (or may not!) help.

Have a read [here]("http://linux.wordpress.com/2007/03/28/tip-manage-the-use-of-swap-memory/") and [here.]("http://rudd-o.com/archives/2007/10/02/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that/2/")

---

### Post by afonteijn on 2007-12-18
Well, it seems I've solved the problem. coolguy2006delhi was on the right track all along. The swap file it self was perfectly okay, it simply wasn't turned on. I just had to add a line to the fstab telling it where the swap file was. In my case: 

/dev/sda1       swap            swap        default          0       0

Anyway, thanks for all the help, and I hope this solution might help someone some day! ;-)

---

### Post by dark_cossack on 2008-03-20
I'm having the same problem...

However, my fstab already has an entry for the swap file. The entry looks like this:

UUID=f73918be-6d76-407e-b5be-240eb45edeed none            swap    sw              0       0

My fdisk -l returns this:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000000a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1288    10345828+  83  Linux
/dev/hda2   *        1289        3838    20482875    7  HPFS/NTFSDisk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000000a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1288    10345828+  83  Linux
/dev/hda2   *        1289        3838    20482875    7  HPFS/NTFS
/dev/hda3            3839        9729    47319457+   f  W95 Ext'd (LBA)
/dev/hda5            3839        5751    15366141    7  HPFS/NTFS
/dev/hda6            5752        7664    15366141    7  HPFS/NTFS
/dev/hda7            7665        7919     2048256    7  HPFS/NTFS
/dev/hda8            7920        9729    14538793+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e7c5e07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1004     8064598+   c  W95 FAT32 (LBA)
/dev/hdb2            1005        1247     1951897+  82  Linux swap / Solaris

/dev/hda3            3839        9729    47319457+   f  W95 Ext'd (LBA)
/dev/hda5            3839        5751    15366141    7  HPFS/NTFS
/dev/hda6            5752        7664    15366141    7  HPFS/NTFS
/dev/hda7            7665        7919     2048256    7  HPFS/NTFS
/dev/hda8            7920        9729    14538793+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e7c5e07

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1004     8064598+   c  W95 FAT32 (LBA)
/dev/hdb2            1005        1247     1951897+  82  Linux swap / Solaris

I'm unsure as to whether the fstab line relating to the swap needs to be changed or not. Please help!

---

