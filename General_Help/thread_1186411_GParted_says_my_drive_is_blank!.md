---
title: "GParted says my drive is blank!"
date: 2009-06-13
forum: General Help
---

### Post by moosehadley on 2009-06-13
Trying to move my partitions around, but GParted keeps telling me my HDD is blank!! I know this isn't possible. It's bootable!
It's laid out like this: [ ext3 | ntfs | <ext3|swap|swap> | swap ]

And I can mount them all from this LiveCD just by clicking on them from 'Places'.

---

### Post by Therion on 2009-06-13
Are you using a gParted LiveCD to look at your partitions, or are you trying to boot your system normally and look at a mounted volume?

---

### Post by moosehadley on 2009-06-13
I'm using GParted on an Ubuntu 9.04 LiveCD. I want to move some of my partitions around. And delete one of the swaps.

---

### Post by moosehadley on 2009-06-13
I tried a Linux Mint LiveCD too, they both claim it to be blank in GParted, yet can mount the drives.

---

### Post by Therion on 2009-06-13
So you can't see the partitions when you boot using the gParted LiveCD?  

Do you see unpartitioned space or...  What?

---

### Post by drs305 on 2009-06-13
Was the ntfs partition umounted cleanly? 

Can you mount the ntfs partition (or the others) by specifying a specific partition with the gparted command, such as:
```

gksudo gparted /dev/sdXX  # Example: gksudo gparted /dev/sda2

```

If you think the partition table may have errors, please post the results of the following command so we can look at the partitions:
```

sudo fdisk -l  # Lowercase L

```

---

### Post by statistic on 2009-06-13
I always feel like such a jerk for suggesting the obvious things, but are you sure you have the right device selected in gparted?

---

### Post by moosehadley on 2009-06-13
Okay, heres a screenshot:

[IMG]http://i44.tinypic.com/19qgsl.png[/IMG]


As you can see, GParted says the whole drive is blank, however, on the desktop to the left, you can see the partitons mounted.
(I did this to prove they are there, if I unmount them, it still says the drive is blank)

---

### Post by moosehadley on 2009-06-13
> **drs305 said:**
> 
If you think the partition table may have errors, please post the results of the following command so we can look at the partitions:
```

sudo fdisk -l  # Lowercase L

```

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001741a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         559     4490136   83  Linux
/dev/sda2   *         560        5118    36620167+   7  HPFS/NTFS
/dev/sda3            5119        9964    38925495    5  Extended
/dev/sda4            9778        9964     1502046   82  Linux swap / Solaris
/dev/sda5            5120        9544    35543781   83  Linux
/dev/sda6            9545        9777     1871541   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by statistic on 2009-06-13
Have you tried looking at it with any other partition managers? If you start running the install and get it to the point where it wants you to partition things, you could go into the manual setup and do all the drive chagnes you want, then just cancel out of actually installing ubuntu.

---

### Post by moosehadley on 2009-06-13
The ubuntu installer does the same thing

[IMG]http://i41.tinypic.com/2nujdkn.png[/IMG]

---

### Post by drs305 on 2009-06-13
Looking at the fdisk output, none of the partitions overlap. I would let *testdisk* take a look at it. Here is a link on how to run it:

[TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by PeterBBB on 2009-06-13
Looks like this open bug
[http://bugzilla.gnome.org/show_bug.cgi?id=337244]("http://bugzilla.gnome.org/show_bug.cgi?id=337244")

Your partions are not in "disk order". Gparted won't handle that it seems.

---

### Post by drs305 on 2009-06-13
> **PeterBBB said:**
> Looks like this open bug
[http://bugzilla.gnome.org/show_bug.cgi?id=337244]("http://http://bugzilla.gnome.org/show_bug.cgi?id=337244")

Your partions are not in "disk order". Gparted won't handle that it seems.


I get a 404 error with that link.

I have run gparted with the 'Partition table entries are not in disk order' message many times, if that is the message to which the link refers. That is not to say it can't happen, but it doesn't *always*. I can't tell if that is message the bug refers to since I cannot access the link.

I can't say I've seen "omitting empty partition". 

Note: To fix a simple "Partition table entries are not in disk order" message, you can run these commands. Please remember that any time you are changing partition tables you are invoking some degree of risk:

Caution: If fstab and/or your boot menu refers to sdXX instead of UUIDs or labels, make sure the applicable partition designation has not changed. In other words, if fstab references sd*a**6*** and the command below renumbers it to *sda**5***, make sure you change it to *sda5* in fstab and menu.lst before rebooting!

```

sudo fdisk /dev/sdX  # Example: sudo fdisk /dev/sda  Don't put a partition *number*, just the device.
#  Then select the following menu items:
m  # Menu
x  # Expert mode
f  # Fix partition order
w  # Write to partition table (saves the changes)

```

It says to reboot but the even before that the *fdisk* command will show the correct order.

---

### Post by PeterBBB on 2009-06-13
> I get a 404 error with that link.

Link should be OK now. 
If not, just go to bugzilla and use the number 337244

---

