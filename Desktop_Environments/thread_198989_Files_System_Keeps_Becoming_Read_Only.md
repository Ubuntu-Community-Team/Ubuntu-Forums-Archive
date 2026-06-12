---
title: "Files System Keeps Becoming Read Only"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Johnsie on 2006-06-18
My whole file system keeps becoming read-only every so often. This normally fixes when I reboot the computer but I dont want to have to do that because it's a webserver and needs to be able to write 24/7

Anyone have any ideas on how to fix it?

Thanks in advance if anyone can help,

John

---

### Post by Johnsie on 2006-06-18
bump

---

### Post by mlind on 2006-06-18
/etc/fstab mounts root partition using **errors=remount-ro**, which means
it will mount partition as read-only if kernel encounters (necessary amount of)
errors on the partition.

You should probably check you partitions using fsck

---

### Post by mlind on 2006-06-18
You should review system logs, especially /var/log/messages and dmesg output
about what causes filesystem(s) to mount read-only.

You can force filesystem check using tune2fs. Use -C paratemeter to set
mount-count one less than maximum mount-count is. You can get the maximum
mount count of a partition by doing 
```

sudo tune2fs -l /dev/xxx

```

where /dev/xxx is the device of the root partition.

---

