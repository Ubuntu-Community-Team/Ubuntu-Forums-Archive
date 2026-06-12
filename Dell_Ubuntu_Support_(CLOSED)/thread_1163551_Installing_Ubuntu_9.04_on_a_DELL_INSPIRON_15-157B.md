---
title: "Installing Ubuntu 9.04 on a DELL INSPIRON 15-157B"
date: 2009-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dutch_Kuykendall on 2009-05-18
I need to install Ubuntu on a friends DELL Inspiron 15-157B  Laptop, but this is the 1st. time I have had to deal with two partitions (a utility and a re-install partition) in FRONT of the Vista partition.

I have used Gparted to resize the Vista NTFS partition, so it now has the following partitions:
    1. Fat23 Dell Utility partition
    2. NTFS Re-Install partition
    3. FAT32 Data partition so that Windows and Linus can share data
    4. Logical partition that holds the EXT3 partition & the swap partition

  I could use a hint as to where to put the mount point, I normally use the root partition (/), but the 2 extra partitions in front of Vista has me guessing, and I don't want to mess up a friends computer.  Help!

---

### Post by coffeeaddict22 on 2009-05-21
What I did with mine was leave the Dell and Windows partitions where they are.  Create three partitions for the Linux install; one for the OS of about 20GB, a partition for my data that mounts at /home, and a swap.  I think so long as the Windows partitions are in front of the Linux ones they won't complain (or notice).  Haven't had any boot problems.

The advantage of keeping the OS and /home partitions separate is reinstalling the OS won't wipe your data.

---

