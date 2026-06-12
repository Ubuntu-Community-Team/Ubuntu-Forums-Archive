---
title: "re-assemble raid0 array"
date: 2012-08-08
forum: Desktop Environments
---

### Post by BCP1987 on 2012-08-08
Hi
I think this is the right place to ask, but if not i'll move it.

I had a Raid1 (mirror) on four disks for /, my homefolder (/home) was on  the rest of those four disks, and I kept recent backups on my usb  drive.

So after making a new backup i took my pc completely apart to do my  summercleaning, but trying to take a backup of my netbook killed my  backup-drive. I am now left with four drives, that won't boot or  assemble the raid0 array, most likely because they are in the wrong  order.

Is there any way to re-assemble a raid0 array if the disks are no longer  in the correct order, or should i just give up and start over?

```
$ sudo mdadm --assemble --scan
mdadm: Devices UUID-363fed2c:cbf63de4:7bcb8d07:46ef23dd and  UUID-363fed2c:cbf63de4:7bcb8d07:46ef23dd have the same name: /dev/md/0
mdadm: Duplicate MD device names in conf file were found.
```

Edit: Also i can't use the alternative installer as it just freezes up on me at the very start

---

