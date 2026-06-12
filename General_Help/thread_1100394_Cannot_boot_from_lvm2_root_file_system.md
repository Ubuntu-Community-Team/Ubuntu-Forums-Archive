---
title: "Cannot boot from lvm2 root file system"
date: 2009-03-19
forum: General Help
---

### Post by tabtab on 2009-03-19
Hi, 

after the latest update I cannot boot up my lvm2 root filesystem.
The kernel says that it is waiting for that but after few minutes I get a (initramfs) prompt. From that initramfs I cannot see the lvm2 filesystems: neither vgscan nor lvscan can find any lvm partitions. I ran the 'modprobe dm-mod' and tried again but it has the same result. The /dev/mapper directory exists but I cannot find the ls command, so I could not make any further inspections. 

I tried to boot up from Live cd, and mount the lvm partitions, and everything seemed to be ok: I could chroot, and run 'apt-get install lvm2' on the root file system but it doesn't solved the issue... after booting from the hard drive it has the sameresult again...

I have Hardy on my pc.

Any tips?

Thanks:
   Bence

---

