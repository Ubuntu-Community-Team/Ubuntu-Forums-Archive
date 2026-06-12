---
title: "ReMount"
date: 2006-09-18
forum: Desktop Environments
---

### Post by ART_Adventures on 2006-09-18
I have a second hard disk which is FAT32 and I mount it to a mount point and it works fine. I do this by typing in the console:

```

sudo mount /dev/sdb1 /mnt/hard_disk_2

```

This hard disk is not remvoable, so is there a way I can get it to do this every time I start ubuntu rather than have to do this every time?

Thanks.

---

### Post by nikhilk on 2006-09-18
Just add the the command you type manually into /etc/fstab file.

---

