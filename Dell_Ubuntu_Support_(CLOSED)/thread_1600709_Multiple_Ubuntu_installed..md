---
title: "Multiple Ubuntu installed."
date: 2010-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cedric_316 on 2010-10-19
I have mistakenly installed Ubuntu in my system twice. So now i want to uninstall any one of them. please help me how to do it.

---

### Post by Lazaruss on 2010-10-19
get a [gparted live cd]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") and delete the partition with the copy you dont want

---

### Post by wojox on 2010-10-19
Just be sure you delete the right partition's. :)

---

### Post by cedric_316 on 2010-10-20
I used Gparted live. It just kept on loading zillions of files, then a complete black screen. Is there any substitute to this software?

---

### Post by Lazaruss on 2010-10-20
as in the iso burned to a cd? weird...

---

### Post by ubudog on 2010-10-20
You can use the Ubuntu Live CD too.  Also, are you sure you installed two Ubuntu's?  It could show up in the boot menu as two because you upgraded your kernel or something.  You can make sure by using the Ubuntu Live CD.  It comes with Gparted on it.

---

### Post by cedric_316 on 2010-10-20
Yeah, burned to a CD and selected "Boot from CD" while the computer starts.

---

### Post by Lazaruss on 2010-10-20
try the ubuntu live cd (assuming you have it, it's up to you if you want to create a whole new one)

What does it say on your grub menu?

---

### Post by cedric_316 on 2010-10-20
when my computer starts it shows 3 options: 2 of Ubuntu and one Windows 7 loader.
I remember installing Ubuntu twice. How can I make sure Im having 2 Ubuntu s?

---

### Post by SavageWolf on 2010-10-20
Does the "Places" menu (Or "Computer" from Nautilus) list any HDDs?

---

### Post by cedric_316 on 2010-10-20
Im not sure whether these are HDDs, but my Places>Computer contains:
320 GB Hard Disk: 132 MB Filesystem
320 GB Hard Disk: OS
File System
and a CD/DVD Drive

---

### Post by Lazaruss on 2010-10-20
In your grub menu, is it ubuntu and ubuntu recovery mode?

And/or is it ubuntu with two different kernels (2.3*.*)?

---

### Post by cedric_316 on 2010-10-20
Yes in the menu it shows to different Ubuntu & their recovery mode & also two memory tests

---

### Post by oldfred on 2010-10-20
It sounds like one install with two kernels shown. this will show partitions:
```

sudo fdisk -l
```

---

### Post by cedric_316 on 2010-10-20
Output:

:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a284

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  de  Dell Utility
/dev/sda2   *          17        1306    10360832    7  HPFS/NTFS
/dev/sda3            1306       26737   204272713    7  HPFS/NTFS
/dev/sda4           26737       38914    97807361    5  Extended
/dev/sda5           26737       38413    93785088   83  Linux
/dev/sda6           38413       38914     4021248   82  Linux swap / Solaris



Please explain this output to me.

---

### Post by ubudog on 2010-10-20
Looks like one Linux part. and one Windows part.  Am I wrong?

---

### Post by oldfred on 2010-10-20
Your sda1 has some Dell utilities, sda2 has the boot flag (*) so that is the partition windows uses to boot. It may be just for booting or it may be your main install but then sda3 is a larger windows NTFS partition. The first install of windows has to be booted from a primary partition which are sda1 thru sda4.

Ubuntu is installed in sda5 and swap is sda6. The sda4 is an extended partition which is one primary partition converted to a container for all the logical partitions you have,  currently sda5 & sda6. 

Some links to info on partitions:
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by ubudog on 2010-10-21
> **oldfred said:**
> Your sda1 has some Dell utilities, sda2 has the boot flag (*) so that is the partition windows uses to boot. It may be just for booting or it may be your main install but then sda3 is a larger windows NTFS partition. The first install of windows has to be booted from a primary partition which are sda1 thru sda4.

Ubuntu is installed in sda5 and swap is sda6. The sda4 is an extended partition which is one primary partition converted to a container for all the logical partitions you have,  currently sda5 & sda6. 

Some links to info on partitions:
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Sounds like my dentist, lol.

---

### Post by cedric_316 on 2010-10-21
So this means i only have one Linux and one windows right?. so how can i remove the second Linux from the boot menu?

---

### Post by oldfred on 2010-10-21
We recommend you keep 2. Just in case the new one has issues. You will keep getting more as new kernels are released.

HOWTO: Remove Older Kernels via GUI
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

You can also edit the grub code to limit the number shown. Kernels are not large.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by gibbylinks on 2010-10-21
> **SavageWolf said:**
> Does the "Places" menu (Or "Computer" from Nautilus) list any HDDs?

No. 

System monitor will show you the drives and partitions.

(oops apologies, I mssed page two completely duh !! )

---

