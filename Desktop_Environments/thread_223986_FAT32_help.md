---
title: "FAT32 help"
date: 2006-07-27
forum: Desktop Environments
---

### Post by poingjam on 2006-07-27
I'm about to install Ubuntu with Windows XP as a dual boot setup on a 150 gigabyte hard drive.  I've got a secondary 250 gigabyte hard drive that I'm using purely for file storage, no OS.  I'd like to be able to write to it using both Windows and Ubuntu, but apparently FAT32 doesn't support drives larger than something like 120 gigs.

I read somewhere that it actually supports up to 2 terrabytes as long as Microsoft Scandisk isn't needed, but I don't know if Microsoft Scandisk will or will not be needed or how to determine that.

So what can I do if I want to use the entirety of my 250 gigabyte drive?  And what's all this about Microsoft Scandisk?  I thought that was just the thing that corrected disk errors in case of malfunction.

---

### Post by Saltydog17 on 2006-07-27
I think your best solution would be just to split the 250GB drive in half.  This way you can use FAT32 and ScanDisk will work as well (in case you do ever want to use it).  I have a 250GB that I split 200GB - FAT32 and 50GB - ext3 (for larger files and backups).  I haven't had any trouble using the larger FAT32 partition dual booting XP/Ubuntu.

---

