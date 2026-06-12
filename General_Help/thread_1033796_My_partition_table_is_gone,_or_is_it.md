---
title: "My partition table is gone, or is it?"
date: 2009-01-07
forum: General Help
---

### Post by PlayWithFire on 2009-01-07
I am trying to set up a quad boot laptop. 
I installed XP and Vista, and those worked just fine. Then i installed OS X and that went well (i thought). But when i booted into Ubuntu to install it, i notice that my HD is unallocated under GParted. The entire disk. I created 4 paritions there following [this tutorial ]("http://wiki.osx86project.org/wiki/index.php/Quad_booting")
Am i screwed, and do i have to start over? 

Doing "fdisk -l" says that it can't open /dev/sda

---

### Post by louieb on 2009-01-07
Gparted won't display a partition table if its doesn't follow all the rules. 
Most common violation is a primary partition inside an extended partition. PC still works but Gparted (and the Ubuntu installer)  will show a blank drive.

fdisk needs to be run with root privlages With the live CD try 
```
sudo fdisk =l
``` (lowercase L)

---

### Post by bodhi.zazen on 2009-01-07
> **PlayWithFire said:**
> I am trying to set up a quad boot laptop. 
I installed XP and Vista, and those worked just fine. Then i installed OS X and that went well (i thought). But when i booted into Ubuntu to install it, i notice that my HD is unallocated under GParted. The entire disk. I created 4 paritions there following [this tutorial ]("http://wiki.osx86project.org/wiki/index.php/Quad_booting")
Am i screwed, and do i have to start over? 

Doing "fdisk -l" says that it can't open /dev/sda

If you know the geometry you can manually restore the partitions with fdisk.

If you do not know the exact geometry use testdisk.

Testdisk is in the repos and can be installed and run on the live ubutnu CD.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by caljohnsmith on 2009-01-07
Please also post the output of:
```
sudo sfdisk -VluS
sudo sfdisk -d /dev/sda
```
So we can get a better idea if your partition table is the problem.

---

### Post by -kg- on 2009-01-07
> **louieb said:**
> Gparted won't display a partition table if its doesn't follow all the rules. 
Most common violation is a primary partition inside an extended partition. PC still works but Gparted (and the Ubuntu installer)  will show a blank drive.

fdisk needs to be run with root privlages With the live CD try 
```
sudo fdisk =l
``` (lowercase L)

Under what circumstances can a Primary partition be created inside of an Extended partition?  No partition editor I have ever used will create a Primary partition inside an Extended partition.

The only type of partition you can create inside an Extended partition is a Logical partition.  Under GPartEd (and Partition Magic, and others I have used) creating a new partition inside of an Extended partition will only allow the creation of a Logical partition.  The other options (Extended, as well as Primary) will be grayed out and not selectable.

PlayWithFire:  Did you create one of those partitions as an Extended Partition, or did you create 4 Primary partitions?  If you have 3 OSes to install and then go to create a Linux installation, you will not have the ability to create sufficient Primary partitions due to the 4 Primary partition limit rule.

If you created an ext3 /root partition as a Primary partition for Ubuntu, you will be unable to create the other partition you need...the Swap partition.  You will need to delete that partition, create an Extended partition in the Unallocated space, then create the ext3 and swap partitions within it as Logical partitions.

I would say that, if you delete the partition you created as ext3 and create an Extended partition (you probably don't even need to take the second step, but it won't hurt anything), then install Ubuntu using the "Guided Install - Use Largest Contiguous Space" option for installation.  This will automatically create the required partitions in the free space within the Extended partition.

For further details on partitioning operations, see ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") from the Community Documentation.

I realize that I could be wrong, but I've never experienced some of the partitioning problems I've seen on this site, and I try my best to visualize what possibly could be wrong from my experience over the years in partitioning hard drives.  I come from an era of 8- and 16-bit Operating Systems and the limited BIOSes of that time, where partitioning a larger hard drive was literally a necessity.

---

### Post by louieb on 2009-01-07
> **-kg- said:**
> Under what circumstances can a Primary partition be created inside of an Extended partition?  No partition editor I have ever used will create a Primary partition inside an Extended partition.

Gparted and other partitioner's based on parted make you follow the rules.  

The one partitioner that looks like it will is Disk Drake (used by Mandriva and Mandriva based distributions).  From what I've see it does not create a primary partition inside the extended. But when it creates an extended it will wrap it around a primary partition(s). 

Take a look at this thread   **[installer not recognizing existing partitions ]("http://ubuntuforums.org/showthread.php?t=1033640&highlight=partitions")**[URL="http://ubuntuforums.org/showthread.php?t=1033640&highlight=partitions"]
[/URL] here the whole drive (including two primary partitions) is enclosed in one big extended partition.

fdisk will place a primary partition inside an extended partition. It assumes you know what your doing and has few edits. It pretty much just does what you tell it to whether it makes any sense or not.

---

### Post by -kg- on 2009-01-07
> **louieb said:**
> Gparted and other partitioner's based on parted make you follow the rules.  

The one partitioner that looks like it will is Disk Drake (used by Mandriva and Mandriva based distributions).  From what I've see it does not create a primary partition inside the extended. But when it creates an extended it will wrap it around a primary partition(s). 

Take a look at this thread   **[installer not recognizing existing partitions ]("http://ubuntuforums.org/showthread.php?t=1033640&highlight=partitions")**[URL="http://ubuntuforums.org/showthread.php?t=1033640&highlight=partitions"]
[/URL] here the whole drive (including two primary partitions) is enclosed in one big extended partition.

fdisk will place a primary partition inside an extended partition. It assumes you know what your doing and has few edits. It pretty much just does what you tell it to whether it makes any sense or not.

I just got done Googling Disk Drake.  As far as I can tell, it is no longer available, and any links I found threw an Internet "404" error.  The only other thing I could find on it were older bug reports reporting that indeed, it would surround Primary partitions with Extended partitions and create no end of problems.  There were work-arounds (like creating the Extended partition first then resizing and creating the required Primary partitions afterwards) but not worth the trouble.

I would say that we need to find what partition editor PlayWithFire used to create the partitions for the first 3 OS installations.  It really doesn't seem likely he would have been using an obviously outdated tool like Disk Drake, and with the superior partitioning tools available for free today (that won't allow a screw up like that) I wouldn't be using fdisk, either.

He said he tried to use GPartEd for the Linux installation (and that it wouldn't read the disk).  I'm guessing we're going to have to wait and see what "fdisk -l" shows us.  If he did use a tool that would allow a screw up like that, he'll likely have to wipe the disk and start over.

I remember "fdisk" that came with earlier DOS (and how onerous it was to use), but I never had occasion to create an extended partition with it, since at the time I never had over a 10 MB hard drive (and *they* were d@mned expensive!).

---

### Post by PlayWithFire on 2009-01-08
i lost my internet connection, so i just now saw all your messages
i decided to saw screw it, and start over with my install and this time it worked
thank you all for your help

---

