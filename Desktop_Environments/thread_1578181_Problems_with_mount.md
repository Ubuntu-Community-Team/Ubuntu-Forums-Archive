---
title: "Problems with mount"
date: 2010-09-20
forum: Desktop Environments
---

### Post by asai on 2010-09-20
Hi,
I have a external disk, which I have mounted to a folder in fstab.
This worked fine for a long time.

Suddenly, I don't know of any changes in the system, it don't mount at boot.
Sometimes I can ```
sudo mount -a
``` and it's fine, but not everytime.

Strange thing.

I have tried with UUID in fstab, but it's the same.
Then with ```
sudo fdisk -l
``` i find that often the disk has the address ```
/dev/sdb1
``` but sometimes it is ```
/dev/sdf1
```

The UUID never changes, but why doesn't this work properly in fstab?

---

