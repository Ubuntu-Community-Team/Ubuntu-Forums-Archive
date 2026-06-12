---
title: "Help with Partition Editor"
date: 2008-12-03
forum: General Help
---

### Post by David Vincent-Jones on 2008-12-03
I am having a problem changing a partition size:

I am in the process of moving from 7.10 to 8.10 but I still have unresolved difficulties in 8.10 thus I have both systems on my disk.

In addition I have a separate partition containing a very large amount of image data.

Before changes my disk layout looked like this:
********** 7.10 **********|****** Images *****|** 8.10 **|

I had too much space allocated for 7.10 and am running out of space for my Images so I freed up the 7.10 area and now have this:
**7.10**|UNALLOCATED|****** Images *****|** 8.10 **|

Now I find that I cannot expand my Image area into the unallocated section. What is going on. I have tried using the 'boot' disk and with the Image partition both mounted and unmounted but the PartEd appears to refuse to increase the size or move the Image partition towards the front.

Help would be appreciated... thanks

David

---

### Post by taurus on 2008-12-03
Is the partition for Image a primary or logical partition?  Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by caljohnsmith on 2008-12-03
Do you have a swap partition on that HDD I assume? When you use the partition editor from the Live CD, try right-clicking the swap partition and choose "swapoff". I'm guessing that your images partition is part of the extended partition with the swap partition, and having swap mounted could then prevent you from resizing the images partition. If that doesn't work, how about opening a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
And let me know how it goes.

---

### Post by bodhi.zazen on 2008-12-03
Better to post a screen shot or the output of 

```
sudo fdisk -l
```

My guess is your images are in an extended partition.

Or that you need to do this in two steps. downsize the first partition -> apply changes -> add space to second partition.

---

### Post by David Vincent-Jones on 2008-12-03
Here is my terminal output:

david@david-laptop:~$ sudo fdisk -l
[sudo] password for david:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5e5d5e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            8034       19457    91763280    5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
/dev/sda6           15805       18704    23294218+  83  Linux
/dev/sda7           18705       19080     3020188+  82  Linux swap / Solaris
/dev/sda8            8034       15804    62420494+  83  Linux

Partition table entries are not in disk order

**** end of output ****

In order .. these are the partitions
/dev/sda1 is my 7.10 ...29.29 GB
Unallocated between sda1 and sda8 ... 32.24 GB
/dev/sda8 is Images  ...59.93 GB
/dev/sda6 is my 8.10 ...22.22 GB
sda5 and 6 are my swap files

David

---

### Post by bodhi.zazen on 2008-12-04
Well, that was my guess

sda8 is a logical partition contained within sda2

So you need to add the unallocated space to sda2, and then possible move the partitions within sda2

---

### Post by David Vincent-Jones on 2008-12-04
/dev/sda2 "looks" as if it only contains the swap areas sda5 and sda7 ... but it shows a size of 87.51 GB. Also sda2 is stuck at the end of the disk and advises that it is "Busy".

I assume that any changes that I need to make would need to be made from a boot disk ... could you give a step-by-step for the procedure.

David

---

### Post by bodhi.zazen on 2008-12-04
ah, yes, IMO best to manage your partitions from a live CD :)

You need to move your partitions so the free space is adjacent to the partition you want to add it into.

Your disk is out of order and I apologize if I did not read the cylinders in detail.

Documentation: [Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

You can also fix this from a live CD. If you wish, first resize all your partitions.

Then re-boot the desktop CD (always a good idea to reboot after changing the partitions).

Then use fdisk :

```
sudo fdisk /dev/sda
```

at the menu type x (for expert menu)-> 
m to list commands

fix -> exit -> write changes to disk -> exit fdisk

reboot to hard drive.

---

