---
title: "Repairing Filesystems"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by ishmaelm on 2007-11-07
Hi,

I get this error when booting our linux mail server:

An automatic file system check of the root filesystem failed. A manual fsck must be perfomed, then the system rebooted. This fsck can be performed in maintenance mode.Please note that the root filesystem is currently mounted read-only.
This fsck should only be performed while the root filesystem is mounted read-only. However, the command to remount it read-write is: 
                # mount –n –o remount,rw / 

Please help as we need to fix this very urgently.
Thanks
Ishmael Motsoeli

---

