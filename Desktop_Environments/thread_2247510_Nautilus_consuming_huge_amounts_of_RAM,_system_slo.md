---
title: "Nautilus consuming huge amounts of RAM, system slow"
date: 2014-10-08
forum: Desktop Environments
---

### Post by jimerman on 2014-10-08
I have 14.04 on an old HP desktop (1.2GB RAM), but it has been running fine.  Last week, we had some storms come through, the power kept going up and down, so it got powered off a couple times before I shut it down.

I have noticed now, that it was so sluggish it was unusable.  When I run System Monitor, Nautilus is using 850 MB of RAM (that's right, almost a gigabyte).  Normally it uses about 8.  Is there a memory leak?  I assume the reboot ran FSCK and would have fixed any file system issues, after a reboot it seems to work fine.

Thanks for your suggestions.

---

### Post by tgalati4 on 2014-10-08
Look in your log files (/var/log/syslog) for errors.  It's possible that your disk drive is having issues.

What are the SMART parameters of the drive?  Open a terminal:

```
sudo smartctl -a /dev/sda
```

---

### Post by ajgreeny on 2014-10-08
You should also run a disk check which you can do either from a live system, making sure the Ubuntu partitions are unmounted and then running ```
sudo e2fsck /dev/sdx#
``` where sdx# is your Ubuntu root partition, or you can use command ```
sudo touch /forcefsck
``` in your booted Ubuntu system terminal which will run fsck next time you boot or reboot.

---

