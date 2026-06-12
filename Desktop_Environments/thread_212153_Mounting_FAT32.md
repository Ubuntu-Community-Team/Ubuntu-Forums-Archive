---
title: "Mounting FAT32"
date: 2006-07-09
forum: Desktop Environments
---

### Post by GoodPanos on 2006-07-09
Can you mount a FAT32 partition as the /home mount?  Does Dapper have the capability to read/write to a fat32 partition without any issues?

Basically I want to have one partition that is sharable between Win XP and Ubuntu without any issues.  How does Ubuntu Dapper do with NTFS partitions?

---

### Post by chajuram on 2006-07-09
Ubuntu can read and write to fat32 (no issues, I do it all the time). Look at ubuntuguide.org for details. It can read NTSF partitions, but not write to them (it can but better not). 

As a results, one standard strategy is to have three partitions. 
[LIST=1]
[*]NTSF for XP
[*]ext3 for Linux
[*]fat32 to transfer files between, or keep frequently accessed files
[/LIST]

I suppose you can mount home to a fat32 partition, but it may not be a good idea (I am not sure why, but I am guessing speed and safety might be issues).

Chajuram.

---

### Post by aysiu on 2006-07-09
Mounting FAT32 as /home is a **really** bad idea. FAT32 doesn't support permissions and Linux is all about permissions. If the permissions in your /home directory are off, you won't even be able to log in.

Don't believe me? Read [this](http://www.ubuntuforums.org/showthread.php?t=211891).

---

### Post by GoodPanos on 2006-07-09
Thanks for the advice.  I think I'll just mount the FAT32 partion within the /home directory.

---

