---
title: "Partitioning Windows NTFS after Ubuntu install?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by inteja on 2006-09-20
I installed Ubuntu dapper on my notebook. As expected, it resized the existing Windows NTFS partition to make space for itself, which worked great. 

However, now I'd like to make a new partition by resizing the Windows partition again. This new partition I'd like to be accessible to both Windows and Ubuntu. I tried QTParted but the only drive it found was the external USB drive.

I assume that because Ubuntu successfully resized the partition on installation, I should be able to do the same manually.

Any ideas?

---

### Post by wieman01 on 2006-09-20
Yes, will be possible. Have you tried **GParted**? It's preinstalled but can also be found in the repositories. Great tool and fairly intuitive.

---

### Post by inteja on 2006-09-20
Thanks.

I'm new to Ubuntu and didn't know about GParted, nor could I find it in my install, but after reading the forums I realized it's only on the LiveCD (but why?).

Anyway, the resize worked great. Thanks again.

---

### Post by inteja on 2006-09-20
Actually, now I have another related question.

Using GParted (or disk manager in WinXP) I can't allocate my new unallocated space because I already have 4 primary partitions, like so:

/dev/hda1   39Gb  NTFS
/dev/hda2    2Gb  EXTENDED
___/dev/hda5  1Gb  FAT32 
___/dev/hda6  1Gb  LINUX-SWAP
/dev/hda3    5Gb  FAT32 hidden, lba
/dev/hda4   26Gb  EXT3 Ubuntu

I started with a clean WinXP Home system, so Ubuntu must have created the other partitions on install.

Question is I don't know what I can do to allocate my unallocated space. Is it safe to delete one of those smaller partitions or something?

---

### Post by wieman01 on 2006-09-20
Ok, now it gets a bit complicated but we can resolve it step by step. Could you highlight which of the partitions you'd like to keep and which you don't? Also where is the unallocated space?

Please point those out and I'll show what we can do about it.

BTW: GParted is also in the repositories... You can install it using Synaptic.

---

### Post by inteja on 2006-09-21
Thanks for the help, but I decided to start clean, repartition how I want, install WinXp and then install Ubuntu in unallocated space. Given I've a new system with no personal files as yet, this seems like the best way to go about it. :p

---

