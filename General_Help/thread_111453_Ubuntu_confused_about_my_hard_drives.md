---
title: "Ubuntu confused about my hard drives"
date: 2006-01-02
forum: General Help
---

### Post by Mazin on 2006-01-02
It's really weird, but Ubuntu seems to be confused about my hard drives.  My fstab file is correct, but when I check the place the non-Linux drives are supposed to be mounted, I see nothing.

The Disks program in the System menu shows absolutely nothing where it usually shows the hard drives in my system.  Even stranger, GParted tells me that both my Windows hard drive and my FAT32 partition for personal files are mounted as / and that the partition that Linux is running on isn't even in use!  I think Linux may be improperly mounting them when it starts.

---

### Post by plors on 2006-01-02
could you please send us the contents of :
/proc/mounts
/etc/mtab

thanks!

---

