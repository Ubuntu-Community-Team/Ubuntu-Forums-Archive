---
title: "Fat32 bad sectors"
date: 2006-05-22
forum: Desktop Environments
---

### Post by ampop on 2006-05-22
My disk have some bad sectors on a fat32 hda1 patition. I have Ubuntu on hda3.
With MS scandisk it takes a long time to fix. I have allways to confirm fix mesage, it really sucks, 3 hours, just 2% disk checked. So I quit MS scandisk.
I tried the fsck and I have this:

ampop@portatil:~$ sudo fsck.vfat -a /dev/hda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/hda1: 0 files, 111/1150529 clusters

It says "Not automatically fixing this", what I should do to fix this?
Any one knows any tool to fix this partition?

Thank you.

---

### Post by Kethinov on 2006-05-23
Well, I can tell you one thing. If you've got bad sectors on your disk it's a hardware problem, not a software problem. Reformatting is not going to help. The best thing you can do is use a filesystem that will see bad sectors and declare them off limits to the filesystem, which is something I don't know much about. I'm not sure how Windows claims to "repair" a bad sector, but it is a physical flaw on your disk, not a software problem. I highly suggest replacing it.

---

### Post by ampop on 2006-05-23
[QUOTE=Kethinov]Well, I can tell you one thing. If you've got bad sectors on your disk it's a hardware problem, not a software problem. Reformatting is not going to help. The best thing you can do is use a filesystem that will see bad sectors and declare them off limits to the filesystem, which is something I don't know much about. I'm not sure how Windows claims to "repair" a bad sector, but it is a physical flaw on your disk, not a software problem. I highly suggest replacing it.[/QUOTE]

Yes, it's a hardware problem. The scandisk "says" to the system that the bad sectors can't be used, and the problem it is minimized.
I want to do the same but using some easier and quickly tool.
Thank you for your opinion. ;)

---

### Post by mevan on 2006-05-23
Just an opinion.. Try using "scandisk /surface /autofix"!!! 
And leave it alone it may take some time but, if drive can be fixed (i.e. bad blocks reallocated), it will do the job.

---

### Post by ampop on 2006-05-23
[QUOTE=mevan]Just an opinion.. Try using "scandisk /surface /autofix"!!! 
And leave it alone it may take some time but, if drive can be fixed (i.e. bad blocks reallocated), it will do the job.[/QUOTE]

That's it.
Thank you very much.

---

### Post by jaja23bd on 2006-05-27
[QUOTE=mevan]Just an opinion.. Try using "scandisk /surface /autofix"!!! 
And leave it alone it may take some time but, if drive can be fixed (i.e. bad blocks reallocated), it will do the job.[/QUOTE]
thanks mate..

---

