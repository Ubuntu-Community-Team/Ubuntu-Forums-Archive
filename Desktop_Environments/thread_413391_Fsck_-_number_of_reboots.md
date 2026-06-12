---
title: "Fsck - number of reboots"
date: 2007-04-19
forum: Desktop Environments
---

### Post by tompot on 2007-04-19
Is it possible to set number of reboots (or disk mounts) after which **fsck** will check filesystem? By default, **fsck** always automatically checks chosen partitions after 30 disk mounts, but I'd like to increase this value.:confused:

---

### Post by yota on 2007-04-19
Hi,

you can use "tune2fs" for that purpose; a quote from it's manual:
> 
-c max-mount-counts
              Adjust the number of mounts after which the filesystem  will  be
              checked  by e2fsck(8).


hope this helps!

---

### Post by tompot on 2007-04-19
> **yota said:**
> Hi,

you can use "tune2fs" for that purpose; a quote from it's manual:


hope this helps!

Thanks for the tip, I'll try it.

---

