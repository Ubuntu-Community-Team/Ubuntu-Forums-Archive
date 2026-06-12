---
title: "Hard Drive Questions"
date: 2006-02-23
forum: Desktop Environments
---

### Post by Nategoofs on 2006-02-23
Alright Guys,
      I got into Ubuntu about three weeks ago and Im lovin it, but Im having some issues with my hard disks.  I have 3 HDDs, one for the OS and applications and such and the other two are 200Gb and 350Gb for media and backed up files and things like that.  I was previously running Xp on my comp and all three hard drives formatted using the NTFS file system.  Once I installed Ubunutu using its own partitioner, i left the other drives as they were.  
     ANYWAYS, the problem is that when i try to do things such as add files to my music library or alter image files and save them to those drives.  how am i to add those files to my library or be able to actually access those drives through programs?

---

### Post by Ocxic on 2006-02-23
ubuntu doesn't have any write capabilites for NTFS drives. if your data is on an NTFS partiton the only thing you'l be able to do is read them. the drive will be read-only.

---

### Post by aysiu on 2006-02-23
As ocxic says, NTFS is read-only.

That means if you mount your NTFS partition correctly, you can add files to your music library. You will not, however, be able to alter images.

See the fourth link of my signature for instructions on how to mount your NTFS partition properly.

You may consider, however, making one of your NTFS partitions into a FAT32 partition. FAT32 is read/write for both Windows and Linux. It's a good filesystem for sharing files.

---

