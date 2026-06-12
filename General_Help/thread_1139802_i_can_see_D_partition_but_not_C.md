---
title: "i can see D partition but not C:"
date: 2009-04-27
forum: General Help
---

### Post by erdal123 on 2009-04-27
as the titel says. i remember using some tool to get access to D but i couldnt fix C at the time 

btw i forget the name of the tool

---

### Post by mali2297 on 2009-04-27
Please elaborate. What are you trying to do? Are you trying to access a Windows partition from Ubuntu?

---

### Post by erdal123 on 2009-04-27
> **mali2297 said:**
> Please elaborate. What are you trying to do? Are you trying to access a Windows partition from Ubuntu?

yes

im able to access D:

but for some reason C: is not visible

---

### Post by Jammanuser on 2009-04-27
Hello. 
Drive letters are not seen by any version of Linux, because it is a Windows thing.
Check your /etc/fstab, and verify that you have a line in there for whatever drive and partition number your C: partition is (though of course the C: can only be seen from Windows).

---

### Post by erdal123 on 2009-04-27
> **Jammanuser said:**
> Hello. 
Drive letters are not seen by any version of Linux, because it is a Windows thing.
Check your /etc/fstab, and verify that you have a line in there for whatever drive and partition number your C: partition is (though of course the C: can only be seen from Windows).

/etc/fstab?

im sorry

---

### Post by Jammanuser on 2009-04-27
> **erdal123 said:**
> /etc/fstab?

im sorry
Yes, on your Ubuntu partition. Navigate to Places>Computer, and then double-click on the Ubuntu partition (should be shown as "Filesystem") to open it. Next, navigate to /etc/fstab, and post the contents of that file.

-Jam man

:guitar:

---

### Post by erdal123 on 2009-04-27
> **Jammanuser said:**
> Yes, on your Ubuntu partition. Navigate to Places>Computer, and then double-click on the Ubuntu partition (should be shown as "Filesystem") to open it. Next, navigate to /etc/fstab, and post the contents of that file.

-Jam man

:guitar:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by mb_webguy on 2009-04-27
I think it might be useful here to have a quick introduction to the Linux filesystem...

Windows separates different partitions on a drive and assigns them different drive letters.  If you have two drives, and one of them has three partitions, you might have something like C, D, E, and F.  Each partition is its own separate directory structure.

Linux has what's called a unified filesystem.  While Windows may have several separate directory structures, one for each partition, Linux has only the one.  Partitions are mounted as directories somewhere in this singular directory structure.  Accessing the information on a partition, therefore, is as simple as navigating to that directory.  Any partition can be mounted as any directory, and any directory can be on its own partition.  So in Linux, the partition you call "D" in Windows could be "/mnt/D" or "/home/mystuff" or "/hey/howareya/fine/howaboutyou/imgood" or anything else you think appropriate.  

While partitions in Windows tend to be used as generic data storage locations, partitions in Linux tend to be used for a specific purpose.  For example, if a partition is mounted as "/home", the only information stored on that partition will be user data like documents, movies, and music, as well as user-specific configuration files.  A partition mounted as "/usr" would contain applications and nothing else.  Of course, you *can* mount a partition as a generic data storage location if you want, such as "/mnt/whatever" or "~/stuff".

The "/etc/fstab" file contains information about partitions to be automatically mounted at startup.  These are your permanently mounted partitions.  What Jammanuser wants you to do is copy the contents of that file and post it here.  One way of doing this is to open the terminal, enter the command "cat /etc/fstab", and copy-and-paste the output.

By the way, here are a few links you might want to look at as a former Windows user new to Linux:
[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")
The Linux [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")
[Ultimate Linux Newbie Guide]("http://www.linuxnewbieguide.org/")
[Security on Ubuntu]("http://www.psychocats.net/ubuntu/security")

---

### Post by Jammanuser on 2009-04-27
> **erdal123 said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
Ok, you appear to be using Wubi...
In that case then, your "host" partition (i.e. the Windows partition that contains your root.disk), I'm guessing, is probably your D: partition in Windows, and that is why you can see it at all, but can't see your C: partition. 

Please post the output of "sudo fdisk -l" (the last letter is a lowercase "L") run in the Terminal, and clarify which partition in the output is your C: partition in Windows.

---

### Post by erdal123 on 2009-04-28
> **Jammanuser said:**
> Ok, you appear to be using Wubi...
In that case then, your "host" partition (i.e. the Windows partition that contains your root.disk), I'm guessing, is probably your D: partition in Windows, and that is why you can see it at all, but can't see your C: partition. 

Please post the output of "sudo fdisk -l" (the last letter is a lowercase "L") run in the Terminal, and clarify which partition in the output is your C: partition in Windows.

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x229c326a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22192   178257208+   7  HPFS/NTFS
/dev/sda2           22193       30351    65537167+   7  HPFS/NTFS

im not sure

---

### Post by erdal123 on 2009-04-28
> **Jammanuser said:**
> Ok, you appear to be using Wubi...
.

i dont even remember that, i heard of that but i dont know what that is. how do you know

i feel totally noob, what is the best way to get more knowledge about ubuntu

---

### Post by erdal123 on 2009-04-29
> **erdal123 said:**
> i dont even remember that, i heard of that but i dont know what that is. how do you know

i feel totally noob, what is the best way to get more knowledge about ubuntu

ehggggm

---

### Post by Legace on 2009-04-29
Try to see if you can access
```
/host
```
from Computer..


For a Ubuntu tutorial, check this out:
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

---

### Post by mali2297 on 2009-04-29
> **erdal123 said:**
> i dont even remember that, i heard of that but i dont know what that is. how do you know

Wubi allows you to run Ubuntu from Windows, see [http://en.wikipedia.org/wiki/Wubi_(Ubuntu)](http://en.wikipedia.org/wiki/Wubi_(Ubuntu)). Do you start Windows before Ubuntu?

> 
i feel totally noob, what is the best way to get more knowledge about ubuntu

A collection of tutorials can be found at [http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/).

---

### Post by erdal123 on 2009-04-30
> **Legace said:**
> Try to see if you can access
```
/host
```
from Computer..


For a Ubuntu tutorial, check this out:
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

cant access it :(

---

