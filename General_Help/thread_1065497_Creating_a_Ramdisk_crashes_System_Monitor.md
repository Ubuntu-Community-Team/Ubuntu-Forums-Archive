---
title: "Creating a Ramdisk crashes System Monitor?"
date: 2009-02-09
forum: General Help
---

### Post by Yashiro on 2009-02-09
Could someone else test this out?
Add the following to your fstab

> #firefox cache
tmpfs                               /mnt/ramdisk            tmpfs           size=129m,nr_inodes=10k,mode=777        0       0

On reboot, open System Monitor. Set your preferences to show all file systems. Click the File systems tab.

Do you also get an instant segfault?

---

### Post by beno1990 on 2009-02-09
Yup, I just made a ramdisk and I'm getting the same problem.

---

