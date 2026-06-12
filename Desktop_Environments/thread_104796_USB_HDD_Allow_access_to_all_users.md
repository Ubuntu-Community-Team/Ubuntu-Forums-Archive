---
title: "USB HDD Allow access to all users"
date: 2005-12-16
forum: Desktop Environments
---

### Post by kshitij on 2005-12-16
How to configure Ubuntu 5.10 to mount external USB HDD (160GB) with read permissions to all users of the system?

Current setup:
Auto Login enabled for user "kshitij".
HDD contains single VFAT partition.
System detects and mounts my HDD under /media/HD-HBU2
The mount point seems to be dynamically created and removed when HDD is plugged and unplugged.

When connected, access permissions for /media/HD-HBU2 are:
-rwx------ with uid and gid set to "kshitij"

So any other user of the system cannot access the data from this disk.

I need to know the configuration changes required to adjust permissions automatically every time HDD is connected.

fstab does not have nay entry for this HDD.
Will it work if an enrty is added in fstab with umask option.

But frankly I don't want to do that. I would rather want to tell hotplug (or corresponding mount) script to set correct permissions while mounting.

any ideas?

Thanks,
-Kshitij

---

### Post by soulestream on 2005-12-16
if you manually put it in fstab it is my understanding that udev should follow whatever you enter. 

of adjust the udev rule


soule

---

