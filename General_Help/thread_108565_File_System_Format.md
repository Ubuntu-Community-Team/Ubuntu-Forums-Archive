---
title: "File System Format"
date: 2005-12-26
forum: General Help
---

### Post by Shadow6363 on 2005-12-26
Alright, so I'm building a new computer that has a 74 GB as its main hard drive and two 120 GB in raid as secondarys.  On the main hard drive, I plan on triple booting between Windows Vista 64-bit, Windows XP 32-bit, and Ubuntu 5.10 64-bit.  On the raid, I plan on storing all my music and movies that I have and just about any other multimedia such as game backups.  Anyways, I was wondering what people would recommend I format the two 120 GB as.  I would like to be readable/writable under both Windows XP and Ubuntu; howver, I can not think of any formats that would allow me to do this.  NTFS is not writeable under Ubuntu, FAT32 has a 4 GB file size limit, and the two main linux file systems I'm considering (ext3, ReiserFS) need a program to be read under Windows XP.  If anyone knows any other file systems that would allow me to do what I want without necessarily opening the files through a certain program everytime or some setting I could set that would allow me to read/write in either os, please let me know.  Basically any solutions would be nice as I'm sure you guys will have better ideas on how to solve this than I do.  Thanks in advance.

---

### Post by Dgurion on 2005-12-26
Actually FAT32 is 32gb I think.. But that still doesnt help you much...

---

### Post by Shadow6363 on 2005-12-26
Hmm, If I remember correctly, the maximum size you can format the drive is 32 GB, but the maximum file size is 4 GB.

---

### Post by pharcyde on 2005-12-26
Personally I would format the drive using a file format for the O/S you will be primarily using.  I wouldn't do FAT32 since it is not a journaling file system and it is very prone to data corruption.

---

