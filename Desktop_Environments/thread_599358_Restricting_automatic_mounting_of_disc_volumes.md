---
title: "Restricting automatic mounting of disc volumes"
date: 2007-11-01
forum: Desktop Environments
---

### Post by habrys on 2007-11-01
I have several volumes auto-mounted (visible as disks on the desktop). A few FAT32, one NTFS and one ext3 (the old feisty volume). All works great, even ntfs is read-write now.

Now to my question: I want restrict access to some volumes to some users.
Example:
user A has read-write access to all volumes,
user B has read-only access to some and read-write to other volumes,
user C has no access at all to some of the volumes (ideally they won't show on his desktop at all after login).

What would be the best way to achieve that?

---

### Post by habrys on 2007-11-02
Anybody? I'm especially interested how to achieve, that mounted disks, which appear automatically on desktop, depend on user, which is currently logged in. Is it possible?

I cannot simply delete or comment lines in /etc/fstab, because I want to have the disks mounted as one user and not mounted (or not visible on the desktop at least) as another user.

---

### Post by habrys on 2007-11-02
Here is what I did to solve the problem - maybe it'll help someone...

Goal: all autoamagically detected volumes from fstab should be visible on the Desktop of userA and not visible on the Desktop of userB.

So, no changes for userA.

1. For vfat and ntfs volumes the default gid in ftstab is 42 (plugdev). So I just removed the userB from this group:

```
sudo gpasswd -d userB plugdev
```

2. For ext3 volume it was enough to change permissions and group of the mount point /media/hda2:

```
sudo chgrp plugdev /media/hda2
sudo chmod 770 /media/hda2
```

Before:
```
drwxr-xr-x 22 root root  4096 2007-10-18 18:55 hda2
```

After:
```
drwxrwx--- 22 root plugdev  4096 2007-10-18 18:55 hda2
```


This way the userB has no read access to /media/hda2 (hence no more in plugdev group) and the disk doesn't appear on his Desktop.


Maybe removing a user from the plugdev group wasn't such a good idea. I've read somewhere, that this group is also used fro dynamically mounting of hotplug devices like usb sticks, external drives etc. So probably userB probably cannot hotplug now...
Maybe it would be better to create a new group for this, like "mounts" for example and use it everywhere, including fstab entries for vfat and ntfs volumes? I'll test it someday...

---

