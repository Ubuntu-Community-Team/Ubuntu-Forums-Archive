---
title: "System backup"
date: 2009-01-18
forum: General Help
---

### Post by Frickler on 2009-01-18
Hi,

I want to backup my system completely. So I searched for methods to do this and found dd, partimage, tar and rsync.

But I have some questions about this tools:

When I backup a complete disc with dd, is the MBR included? Is it (the MBR, bootloader, partition table) still included when I only backup a single partition like sdb3?

What about partimage? Does partimage backup the MBR? If so, why? Because partimage only backups single partitions and not the whole disc.

Thanks ahead

---

### Post by indytim on 2009-01-18
For information on Partimage:
[Partimage Home]("http://www.partimage.org/Partimage-manual_Usage")

For one application of using Partimage see the link in my signature (does not cover mbr, but it shouldn't be any different from any other partition backup.

IndyTim

---

### Post by jerome1232 on 2009-01-18
> **Frickler said:**
> Hi,

I want to backup my system completely. So I searched for methods to do this and found dd, partimage, tar and rsync.

But I have some questions about this tools:

When I backup a complete disc with dd, is the MBR included? Is it (the MBR, bootloader, partition table) still included when I only backup a single partition like sdb3?

What about partimage? Does partimage backup the MBR? If so, why? Because partimage only backups single partitions and not the whole disc.

Thanks ahead

The boot record is just the first 512 bytes of your drive, the Master Boot Record is just the boot record of the drive that the bios considers first in the priority list of boot devices. If you image an entire drive it's boot record will be backed up. If you image a single partition the boot record will not be backed up. You can always make an image of the first 512 bytes of the disc to backup the mbr.

---

### Post by Frickler on 2009-01-18
Hey thank you. I already know that I can backup the fiirst 512Byte and how. But I am still considering about partimage. What about the "restore mbr from image" function. Partimage only makes a backup of single partitions and I think there is now MBR included.

And there is another question regarding dd:

I tried to make a backup of a disc and of the partitions of the disc.  When I backup the whole disc, the created image is much bigger than the sum of the images of the single partitions. Any explanations?

---

### Post by HunkirDowne on 2009-02-15
> **Frickler said:**
> Hey thank you. I already know that I can backup the fiirst 512Byte and how. But I am still considering about partimage. What about the "restore mbr from image" function. Partimage only makes a backup of single partitions and I think there is now MBR included.

And there is another question regarding dd:

I tried to make a backup of a disc and of the partitions of the disc.  When I backup the whole disc, the created image is much bigger than the sum of the images of the single partitions. Any explanations?

Possibly.  If you used partimage to backup your partitions your images are likely compressed (unless you told it not to).  OTOH, 'dd' makes an uncompressed image which would include unused blocks so if not compressed would make for an image the size of your hard drive.

My experience:
I did the partimage thing and wound up with (compressed) about 11 GB of images.  I'm doing a compressed 'dd' (with bzip2) and I'm at 19 GB and counting.  Since the total of the data is little over 23 GB, I'm hoping that it's going to be finished soon.  I started this before 10:00 UTC and it's now 17:22 UTC.

---

### Post by indytim on 2009-02-15
I believe that there is a MBR restore option in the GUI Partimage.  Honestly, I haven't "exercised" it yet.

With respect to the resulting size of the Partimage backup file(s), it really depends upon the type of compression you selected when initiating the Partimage backup.  I believe that there would be no compression using the dd thinger.

IndyTim

---

### Post by HunkirDowne on 2009-02-15
> **indytim said:**
> I believe that there would be no compression using the dd thinger.


Normally, yes.  But I am in the (rather long) process of the following command:

dd if=/dev/sda | bzip2 -9 > backup.sda.img

This should pipe the output through bzip2 and into a compressed file.  But this job has been going on for over 12 hours now and I really don't know when it will end.  A complete backup of all partitions created 11 GB worth of data yet this thing is at 24.5 x 10^9 bytes and counting.  There is less actual data than that on both partitions combined so I really don't understand what's going on here unless it doesn't get bzipped until the end (in which case this could take days if I let it, which I won't).

Got any ideas?  How long should this take normally?  The drive is a 250 GB and less than 10% full.


Thanks.

---

