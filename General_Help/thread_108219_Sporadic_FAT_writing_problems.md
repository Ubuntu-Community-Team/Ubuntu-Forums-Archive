---
title: "Sporadic FAT writing problems"
date: 2005-12-25
forum: General Help
---

### Post by LeSkip on 2005-12-25
How mature is FAT access in Linux? I have an ext3 parition for Ubuntu, an NTFS partition for Windows and a FAT partition that I want to access from both systems. I have the FAT parition mounted as /media/storage in Ubuntu, and read-write access enabled in fstab.

Writing usually works okay after a fresh mount, but after a while it is read only. Also, I tend to need to run chkdsk when i launch Windows after having written data to the parition from Ubuntu.

Does anyone know what's going on here?

Skip

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-25
FAT works quite well in linux. It sounds like your hard drive is having media failures. I would strongly suggest downloading the drive manufacturer's diagnostic tool and letting it run a "comprehensive test" on the drive containing the fat partition you  mention.

---

### Post by LeSkip on 2005-12-27
The physical drive is fine, I'm sure. It is the same drive that holds my ext3 and NTFS partitions, that both work fine. Also, just using the FAT partition in Windows works fine.

One thing though, I seem to need to use iocharset=utf8 as mount parameter in order to get write access, however this gives warnings in my syslog.

Any other ideas?

---

### Post by LeSkip on 2005-12-30
New info. dmesg gives the following:

[4556546.969000] FAT: Filesystem panic (dev hda4)
[4556546.969000]     fat_get_cluster: invalid cluster chain (i_pos 275389)
[4556546.969000]     File system has been set read-only

So at least I know that it was properly forced into read only.

Now I just want to know why!

Skip

---

### Post by aysiu on 2005-12-30
[QUOTE=LeSkip]
One thing though, I seem to need to use iocharset=utf8 as mount parameter in order to get write access, however this gives warnings in my syslog.[/QUOTE] Isn't it just warning you that utf8 is case-sensitive?

---

### Post by LeSkip on 2005-12-30
I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=34162&highlight=FAT%3A+Filesystem+panic") discussing the same problem, and also the solution to it, namely to run dosfsck on it. 

Strangely enough, chkdsk in Windows does not seem to see or fix the problems that Linux stumbles across, so while the disk works perfectly in Windows it does not in Linux. After dosfsck it works perfectly in both systems.

Problem solved.

---

