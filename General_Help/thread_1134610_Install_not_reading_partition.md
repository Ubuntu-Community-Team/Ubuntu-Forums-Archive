---
title: "Install not reading partition"
date: 2009-04-23
forum: General Help
---

### Post by Andrew852 on 2009-04-23
Hello, It's Andrew again, if anyone saw my last post: The reason I'm reinstalling is because I decided to do it on another Hard drive.

Here is the problem:  I want to install Ubuntu on a partition I made on my SATA USB external drive.  The partitions File System is NTFS (3.1)  and its a.. I think called a logical drive (Im almost sure thats what windows XP called it when I created the partition). 

When I goto install on the Ubuntu Live disk, when I arrive at the partition editor, it doesnt show my partition for my external HDD.  Please help me solve this mystery.

Thanks for reading,
~Andrew.

---

### Post by Andrew852 on 2009-04-24
Sorry for double posting but, does anyone think making the partition have a different file system would help?  If so what type of file system should I pick for it to work.  ATM its a NTFS file system.

---

### Post by jsowoc on 2009-04-24
The partition editor shows only one physical device at a time. There is a box somewhere that lets you pick between /dev/sda, /dev/sdb etc. Keep changing this until you see a drive whose contents look like the one that it should be. The partition editor doesn't care what is on the drive (ntfs, logical, etc.), as long as it has a valid partition table (like a table of contents, where information about logical etc. is stored).

One word of caution, that you should install onto a partition formatted with a filesystem that supports POSIX permissions. Ones that do include "ext2" "ext3" "ext4" "xfs" "reiserfs". Ones that don't include "fat/vfat", "ntfs". I suggest "ext4" if it's available, or "ext3" otherwise. Gparted should be able to format the partition, but you lose any data you had.


Aside: if you are ever curious about all the tables of contents of all the attached drives, the command to type into a terminal is :
sudo fdisk -l
(where "l" is the lowercase "L").

---

### Post by WatchingThePain on 2009-04-25
Hi,
You can't install Ubuntu on an NTFS file system afaik.
I use ext3. 
Hope this helps.

---

