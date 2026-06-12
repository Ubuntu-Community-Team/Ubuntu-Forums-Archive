---
title: "help needed with partitioning"
date: 2005-11-16
forum: Desktop Environments
---

### Post by guuzjo on 2005-11-16
Hi Kubuntu-folks out there!

I want to give Kubuntu a try, but without messing up my windows. I installed Suse 9.3 before on partition #2 and #3, so I want to format them and put Kubuntu instead on it. My windows disks have to remain untouched!

My FStab:

Harddisk one (master) 
   #1   25 GB    NTFS
   #2   1.1 GB   Swap
   #3   14 GB    ReiserFS (old Suse)

Harddisk two (slave)
    #1   80 GB    NTFS

So I formatted the Reiser-disk with Ext3 and made the swap partition a Kubuntu-swap, but then I got the error of a missing root-folder! Please help me with my partitions guys!

Other point of concern is how to install the bootloader, on which disk and what's the moint point?

Thanks in advance

---

### Post by Koybe on 2005-11-16
You need to specify the mount point for the partition during installation.
In your case put mount point as "/" for you old reiserfs suse partition.

Good luck

---

### Post by Rackerz on 2005-11-16
I had the exact same problem, just set a mount point / - root file system.

---

