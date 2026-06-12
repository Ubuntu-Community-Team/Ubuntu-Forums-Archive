---
title: "Removing Dell Recovery partiton"
date: 2009-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by topspin11 on 2009-12-22
Hi - I'm a Mac user trying to hackintosh a Vostro a90 which came with Dell Ubuntu pre-installed. I used Gparted on a boot cd to partition the 8GB SSD but I can only get a 7.15GB partition. I'm thinking that there is a hidden recovery partition or file..

Fdisk shows /dev/hda has 7682MB 

How can I use fdisk or gparted to delete this hidden partition ?


Thanks.

---

### Post by blur xc on 2009-12-22
Uh- I just installed Ubuntu on a few laptops and netbooks w/ recovery partitions, and there wasn't anything hidden.  I don't think there is a way to "hide" a partition from a tool like fdisk or gparted.

Now, what you may be seeing is a product of misleading marketing.  8000mb != 8gb.  Computers count in powers of 2, 1gb = 1024mb, so a *real* 8 gig hdd would have 8192mb or 8,388,608kb.  That, and some part of it's actual storage space is for the file allocation tables, so actual storage is a lot less than what's adertised.  For example, my 500gig hdd actually only have 450gigs of storage space.

BM

---

### Post by topspin11 on 2009-12-22
Thanks for your post. After formatting the SSD to GUID, I have 6.8GB left to install in. Does this sound right ? 
disk Utility shows a blue fill in the backgound after partitioning, which means data of some kind is still there.

TP

---

### Post by blur xc on 2009-12-23
> **topspin11 said:**
> Thanks for your post. After formatting the SSD to GUID, I have 6.8GB left to install in. Does this sound right ? 
disk Utility shows a blue fill in the backgound after partitioning, which means data of some kind is still there.

TP

I don't now for sure (not an expert, never dealt w/ SSDs) but it sounds reasonable to me.  I think all empty formatted disks have some space taken up by the file allocation tables.  The bigger the disk, the more space it takes...

BM

---

### Post by reiki on 2009-12-23
If this is an ext4 formatted filesystem then I believe there's a reserved space at the beginning of the drive for journaling. I could be wrong on that, but I have a small reserved space at teh beginning of a fresh Karmic install as well.

---

### Post by blur xc on 2009-12-23
> **reiki said:**
> If this is an ext4 formatted filesystem then I believe there's a reserved space at the beginning of the drive for journaling. I could be wrong on that, but I have a small reserved space at teh beginning of a fresh Karmic install as well.

That's probably what it is...  ext3 is also a journaling file system, and I think ntfs is too, just not as good :P

BM

---

### Post by topspin11 on 2009-12-23
Thanks for all the input. 6.8GB usable out of an "8GB" drive still seems strange.

How can I format the whole SSD to the state before Dell installed stuff on it ?

Perhaps some PTEDIT32.EXE  kind of program on a bootable cd ??

---

