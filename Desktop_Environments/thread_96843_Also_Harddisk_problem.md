---
title: "Also Harddisk problem"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Blaauw01 on 2005-11-29
thanks to all, i am now able to mount my harddrive.

But i have a other problem, i have no access to the harddrive only root. Also when i run /etc/fstab i cannot detect my mounted harddrive

does anyone have suggestions

:confused:

---

### Post by dcstar on 2005-11-29
[QUOTE=Blaauw01]thanks to all, i am now able to mount my harddrive.

But i have a other problem, i have no access to the harddrive only root. Also when i run /etc/fstab i cannot detect my mounted harddrive

does anyone have suggestions

:confused:[/QUOTE]
You have to have a "mount point" on your filesystem, that (a directory you create) is a logical place on your system where you access the filesystem of your physical device.

If you set the correct permissions on the mount point, and have the right permissions in your /etc/fstab, then it should work for you.

Post your /etc/fstab data here so we can see if it is ok.

---

