---
title: "Something hidden on my hard drive!"
date: 2008-01-12
forum: Dell  Ubuntu Support
---

### Post by natehall on 2008-01-12
Here's the output of fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c7e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / 
Solaris

I figure thats about 3 gigabytes for the swap drive  and 77 for the Linux partition. The disk analzer shows 70.5 gigs . Where's the missing 6.5? I figure if I had a Dell Media direct partition hidden on there somewhere it would have wiped when I did a fresh install with Gutsy. Am I wrong?

---

### Post by natehall on 2008-01-12
I'm thinking maybe one uses the binary gigabyte which is a little bigger than a decimal gigabyte.

---

### Post by jdelaros1 on 2008-01-13
What file system do you have? Don't forget that you will always have some overhead with file systems, where inodes and other items are stored. You usually lose about 6-7 % of your disk space with ext3 file systems. And like you said, some tools use binary output and other decimal.

---

### Post by Omnios on 2008-01-13
Um could possiblybe some free space on the drive, had that problem on a scavanged drive from before. 
 
 Found it when looking at the drive with qparted.

---

### Post by Golden Phoenix on 2008-01-15
I don't think you have hidden files because it looks like Dell set up two partitions as primary partitions.

Often when that happens, you have some unused space left in the drive that has not been applied to any particular partitions.  I would think booting up via a live CD that has partitioning software (Gparted seems to be the current darling) would let you see if there are indeed clusters floating around unused.

---

### Post by natehall on 2008-01-15
I assume I have ext3 . What's a good command to find out?

---

### Post by natehall on 2008-01-15
A binary gigabyte is about 1.07 decimal gigabytes. Is this why you lose 6 to 7 percent when using ext3 files?

---

### Post by gbrainin on 2008-01-15
No, they're separate issues.  Any file system has to use some of the storage space for keeping track of the files.  In ext3 (and most unix-like filesystems), this area has what are known as "inodes."  Different filesystems will accomplish this task differently, and may use slightly differing percentages of the drive, but all of them use some of the drive.

---

### Post by natehall on 2008-01-16
> **gbrainin said:**
> No, they're separate issues.  Any file system has to use some of the storage space for keeping track of the files.  In ext3 (and most unix-like filesystems), this area has what are known as "inodes."  Different filesystems will accomplish this task differently, and may use slightly differing percentages of the drive, but all of them use some of the drive.
Are you saying that when the computer calculates the amount of room left on your hard drive it automaticly deducts that part of the drive ext3  
files are going to need for the inodes?

---

### Post by saru411 on 2008-01-16
system monitor has a list of partitions, their sizes, and what type of extension they have(ex ext3).

---

### Post by gbrainin on 2008-01-16
> **natehall said:**
> Are you saying that when the computer calculates the amount of room left on your hard drive it automaticly deducts that part of the drive ext3  
files are going to need for the inodes?

Oops.  I forgot that you were getting your data from fdisk, which reports the size of the entire partition, rather than from, for example, the df command, which reports available data space.

---

### Post by exoren22 on 2008-01-16
Your hard drive, as reported by dell, is an 80GB drive, correct? 
That's 80 000 000 000 bytes. 
one Gibibyte (commonly referred to as a gigabyte, abbreviated as GiB) is 1 024*1 024*1 024 =1 073 741 824 bytes. So 80 000 00 000 / 1 073 741 824 = 74.51gb. Allowing 3GiB (3 221 225 472 bytes) = 71.51 GiB. This is what's reported, right?

---

### Post by natehall on 2008-01-17
> **exoren22 said:**
> Your hard drive, as reported by dell, is an 80GB drive, correct? 
That's 80 000 000 000 bytes. 
one Gibibyte (commonly referred to as a gigabyte, abbreviated as GiB) is 1 024*1 024*1 024 =1 073 741 824 bytes. So 80 000 00 000 / 1 073 741 824 = 74.51gb. Allowing 3GiB (3 221 225 472 bytes) = 71.51 GiB. This is what's reported, right?
Right.

---

### Post by Golden Phoenix on 2008-01-18
I don't know if Dell still does this, but I know they used to take any l computer from their factory and have two primary partitions, with the second being diagnostic utility software that couldn't be accessed except through booting to it via their BIOS screen.

Normally, that would be less then 100MB, though, so I am not sure this has been taken into account.

---

### Post by natehall on 2008-01-19
> **Golden Phoenix said:**
> I don't know if Dell still does this, but I know they used to take any l computer from their factory and have two primary partitions,....
Mine originally came with a recovery partiton. Very useful when you are just learning about Linux. I've since done a fresh Install with Gutsy., but it was done with a Dell DVD.

---

