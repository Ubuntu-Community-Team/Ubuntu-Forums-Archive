---
title: "4 partition limit"
date: 2006-07-28
forum: Desktop Environments
---

### Post by dolphin_1 on 2006-07-28
My new Dell E310 came with four partitions.
sda1, FAT16 at 32MB total (7 MB used)  
sda2, ntfs at 22 GB total (XP lives here)
sda3, ntfs at 137 GB  (will put Ubuntu here)
sda4, FAT32 at 4.9 GB (4.8 GB used)

I want an additional partition for my Linux files but am limited to four.  What is on the FAT16 and the FAT32 partitions and can I safely free up that space while maintaining my ability to boot into windows?

thanks

---

### Post by crashtest on 2006-07-28
The 32MB FAT16 contains Dell hardware diagnostics - this can be downloaded from the Dell support site and burned to a CD.  The 4.9 GB FAT32 is a restore partition that can be used to restore Windows.  Dell will sell you a CD for about $10 if you want, and then you can get rid of that partition.

---

