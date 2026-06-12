---
title: "HDD sowing as full when there is space"
date: 2008-12-29
forum: General Help
---

### Post by roundhay on 2008-12-29
I have a 500GB HDD installed on my system and noticed a few days ago that I could not copy files to the disk as it was full. I went through the drive and deleted over 10GB of files but I still cannot copy files to the drive and it still shows as full in properties. 

Any ideas why this has happened and how I can fix it?
:confused:

---

### Post by Seks on 2008-12-29
Maybe your drive is dieing? What does it look like in gparted and the sys monitor's file systems tab?

---

### Post by impact on 2008-12-29
Check the easy things first - when was the last time you emptied the trash? Is it possible that some deleted files are still in there?

---

### Post by fooman on 2008-12-29
the disc usage analyzer will give you a good idea of where the build up is occurring.  go to applications > accessories > disc usage analyzer

try running a scan with that.

---

### Post by Peter09 on 2008-12-29
The terminal command 

```
df -h
```
will also show usage on hard disks.

---

### Post by roundhay on 2008-12-29
I should have included this info in my initial post....

The drive looks OK in gparted, you can see the free space and the amount of free space increase when you delete files.

It also looks OK in  system monitor, showing 85% free

---

### Post by Peter09 on 2008-12-29
Still, its worth posting the output of df -h so that we can see all the filesystems.

---

