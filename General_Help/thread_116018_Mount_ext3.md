---
title: "Mount ext3"
date: 2006-01-11
forum: General Help
---

### Post by hove99 on 2006-01-11
Hi

I am not a scilled user of Ubuntu. I am trying to mount an extra ext3 partition (entries in fstab (or mtab?)). I also have an external USB-drive with ext3 on it. How do I mount these partitions and gain read/write access to them?

Thanks, hove99

---

### Post by Mr_Grieves on 2006-01-11
/etc/mtab shows whats currently mounted.
/etc/fstab shows static mounted stuff.

Use this to get the name of the partition:
```

sudo fdisk -l

```

Use this to mount the partition:
```

sudo mount /dev/[name_of_partition] [mount_point_dir] -t ext3

Example:
sudo mount /dev/hdb1 /media/new_disk -t ext3

To unmount:
unmount /media/new_disk

```

Aswell, make sure the directory that you use as a mount point exists :)

---

