---
title: "mount NTFS with write or format to FAT32"
date: 2006-06-21
forum: Desktop Environments
---

### Post by 1002285 on 2006-06-21
I asked the computer shop to make me a documents partition in FAT32, but for some reason it's actually in NTFS.
It is important for me to get this partition working with write support and it is my documents partition, so I want it to be very secure.
Should I try to reformat it into FAT32? How to do it without too much risk?
At the moment there is 17,1 Gb of files and 17,1 Gb of free space in it (I don't know if this is a coincidence or not, but I asked them to make me a 35 Gb partition).

---

### Post by Kouya on 2006-06-21
are u dualing booting between xp and ubuntu? if so it's better to have a FAT32 partition to act as a go-between since NTFS is read only.

However if u format from NTFS to FAT32, you'll lose all your stuff so better backup in another drive or an external one.

---

### Post by 1002285 on 2006-06-21
Yes, between XP and Ubuntu.
But I can't backup anywhere else. I only have  about the same amount of free space on the NTFS partition than used space.  And I have a couple of Gb-s additional free space outside that partition. Maybe I can use these spaces?

---

### Post by x64Jimbo on 2006-06-21
By nature, FAT32 is insecure. It does not support filesystem encryption like NTFS does, and when NTFS is encrypted, Linux can't access it. You'd be better off just using a filesystem that is native to Linux. If you need access to the files in Linux and in Windows, I'd suggest making a fileserver that you can map to with security credentials.

---

### Post by 1002285 on 2006-06-21
So:
I have an 34,18 Gb NTFS-partition for documents of which 17,1 Gb is free. Plus there is 4,13 Gb-s unallocated space.
But it seems that ntfs doesn't let me do anything with itself. Can I change this from Windows?

---

### Post by Kouya on 2006-06-21
eh I'm a noob at linux, having first touched it 2 days ago. I do not really understand what x64Jimbo is saying about a fileserver. Probably is some pro method to work around your situation. 

For me, I have 3 drives that are NTFS which are my main drives when i use XP. I have another that is FAT32. These 4 are mounted when I boot ubuntu. So the FAT32 drive acts as my go between when i switch between XP and Ubuntu. 

This is a very noobie method but since I just use the comp for basic stuff, it serves me fine.

Hmm mayb u shld partition a FAT32 space in the free space u have.

---

