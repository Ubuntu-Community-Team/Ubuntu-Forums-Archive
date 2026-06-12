---
title: "Incorrect entries in Disks Manager"
date: 2006-06-22
forum: Desktop Environments
---

### Post by LeeM on 2006-06-22
Hi! I have several removable USB drives, both hard and thumb drives. Over time, as I remove and re-connect devices, the "Storage List" on the left side of the Disks Manager starts filling up with /dev/xxx entries that are no longer connected. If I look at the results of "mount", it shows only the expected current drives. Also, there are no entries shown in /media for the "ghost" devices.
How do I clean up "Disks Manager", and where does it get its data?

THanks!

---

### Post by lamego on 2006-06-22
I am not sure but it should get the information from the partition list:
```
sudo fdisk -l
```

---

### Post by LeeM on 2006-06-22
[QUOTE=lamego]I am not sure but it should get the information from the partition list:
```
sudo fdisk -l
```[/QUOTE]

I just checked. ```
sudo fdisk -l
```
just shows the active devices, not the "ghost" ones that were active at one time.

---

