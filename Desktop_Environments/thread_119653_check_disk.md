---
title: "check disk"
date: 2006-01-19
forum: Desktop Environments
---

### Post by ArcadePride on 2006-01-19
I was resizing my inux partition in partionmagics bootable cd and it noticed some errors with the partition. Normaly in windows XP I would just go and type in chkdsk /f or use scandisk in windows 98. so my question is, what is the linux equivilent of that? how to i have it check and fix the disk?

Thanks
-Travis

---

### Post by bernardfrancois on 2006-01-24
**fsck** is what you need.
Use **man fsck** for more information.
If you want to reboot and check the filesystems (including the root filesystem) you can use **sudo shutdown -Fr**

---

