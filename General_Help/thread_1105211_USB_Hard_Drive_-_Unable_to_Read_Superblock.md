---
title: "USB Hard Drive - Unable to Read Superblock"
date: 2009-03-24
forum: General Help
---

### Post by jsheely on 2009-03-24
Back Story:

I have a hard drive that was at one time running the main partition / operating system for a server. We were giving the drive and put it into a USB Encloser. I fired up Ubuntu Live CD and am attempting to read the disk.

I have two problems.
1.) I need to mount this drive
2.) I need to access /home/(user) directory that I don't have permissions too

when I try and run command: mount -t ext3 /dev/sdb1 /mnt/usbdrive I get the following error: "unable to read superblock" in dmesg

When I do a fdisk -l I see the drive listed there as a Linux Extended partition.

My ultimate goal is to get the files off this drive onto another system. Any ideas on where to go from here?

Thank you,
Jonathan

---

### Post by dcstar on 2009-03-25
> **jsheely said:**
> Back Story:

I have a hard drive that was at one time running the main partition / operating system for a server. We were giving the drive and put it into a USB Encloser. I fired up Ubuntu Live CD and am attempting to read the disk.

I have two problems.
1.) I need to mount this drive
2.) I need to access /home/(user) directory that I don't have permissions too

when I try and run command: mount -t ext3 /dev/sdb1 /mnt/usbdrive I get the following error: "unable to read superblock" in dmesg

When I do a fdisk -l I see the drive listed there as a Linux Extended partition.

My ultimate goal is to get the files off this drive onto another system. Any ideas on where to go from here?

Thank you,
Jonathan

External drives are auto-mounted when plugged in, if the drive is not visible in the "Places" menu then it either cannot be mounted or there are no partitions on it.

The Partition Editor will show you what it can find on the drive.

---

