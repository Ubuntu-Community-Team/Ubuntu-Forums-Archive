---
title: "how do i extend a partition in gparted?"
date: 2008-12-12
forum: General Help
---

### Post by ultratek on 2008-12-12
i do not see an option for extending a partition in gparted
how can i?

---

### Post by neu2buntu on 2008-12-12
i think you will have to shrink a partition first i.e make free space.......this will become unallocated then you can extend any partition to have this extra space

---

### Post by geirha on 2008-12-12
Make sure all the partitions on the drive are unmounted. Gparted will mark the partitions that are mounted with a lock icon. Once all partitions are unmounted, the options to resize should be available. 

To unmount a partition, run ```
sudo umount */dev/sdb1*
``` replacing /dev/sdb1 with the actual partition.

---

### Post by ultratek on 2008-12-12
well i ran the cmds

but stilll no extend partition option...
i need to keep c: intact for vista

---

### Post by geirha on 2008-12-12
Ah, you want to create an extended partition? I thought you meant extending (resizing) a partition. How many partitions does it have already?. 

What does fdisk list? (assuming the drive is /dev/sdb)
```
sudo fdisk -l */dev/sdb*
```

---

### Post by mkvnmtr on 2008-12-12
If you want to just make an empty extended partition I don't know. But when I installed my third distro I made a large free space and gparted made the extended partitions that I need to install. So it can do the job.

---

