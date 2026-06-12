---
title: "Hiding NTFS Partition"
date: 2006-09-07
forum: Desktop Environments
---

### Post by schadfield on 2006-09-07
My WinXP partition appears in Nautilus as an icon labled "System" and mounts read-only when I double click it.

I can prevent mounting by commenting out the corresponding entry in "/etc/fstab" but the icon still appears in Nautilus.

Is there any way that I can remove that icon?

---

### Post by Uluen on 2006-09-07
Can't you just delete it if it's not mounted?
```
$ sudo mount -a
``` after you comment it out in fstab and delete the icon?

---

### Post by cotcot on 2006-09-07
I think it is gnome-volume-manager mounting your ntfs-partition.
I only have a suggestion to try. Maybe it helps by hiding the ntfs partition; I think you can do this with fdisk or with gparted. (unmount the partition before you try to hide it)

---

