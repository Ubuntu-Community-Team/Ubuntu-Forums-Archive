---
title: "Copy Corrupted Disk"
date: 2022-06-22
forum: Desktop Environments
---

### Post by Geoff_Lane on 2022-06-22
I want to experiment with a disk that was accidentally reformatted, want to try and recover data using testdisk, the original partition table included Windows 10 and three Linux systems so recovery may be complicated so I'd like to option of being able to start again.

The reformatted disk is out of the machine and has GPT partition table, it shows space unallocated.  If I use dd to copy data would this work if I messed up recovery and wanted to start again from scratch?   If so what might be the best bs option for dd to speed up the copy?   I normally use bs=1M

Geoff

---

### Post by TheFu on 2022-06-22
Use ddrescue, which will continue after failures that stop dd.
ddrescue will perform multiple passes trying to retrieve the data in the unreadable areas.  

```
$ sudo  ddrescue  /dev/sdZ  /media/some/mounted/location/not/on/sdZ.img  /tmp/important.log
```

Always, always use a log file with ddrescue.  This contains process information that can be used to know where the issue are and how far along the byte-for-byte cloning has gone.

dd is fine for quick stuff, but when it is about data recovery, use ddrescue or gddrescue.

---

### Post by Geoff_Lane on 2022-06-28
> **TheFu said:**
> Use ddrescue, which will continue after failures that stop dd.
ddrescue will perform multiple passes trying to retrieve the data in the unreadable areas.  

```
$ sudo  ddrescue  /dev/sdZ  /media/some/mounted/location/not/on/sdZ.img  /tmp/important.log
```

Always, always use a log file with ddrescue.  This contains process information that can be used to know where the issue are and how far along the byte-for-byte cloning has gone.

dd is fine for quick stuff, but when it is about data recovery, use ddrescue or gddrescue.

Thanks for that tip.  I use dd often, occasionally had a problem but usually very convenient.   Shall definitely try that.

I've got a new HD so switch over soon, reinstall Ubuntu then maybe experiment with old disk.

Geoff

---

### Post by ActionParsnip on 2022-06-29
ddrescure keeps going if a sector is not readable :)

---

