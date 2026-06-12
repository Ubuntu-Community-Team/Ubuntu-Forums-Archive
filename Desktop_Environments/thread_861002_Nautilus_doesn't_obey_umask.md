---
title: "Nautilus doesn't obey umask"
date: 2008-07-16
forum: Desktop Environments
---

### Post by ad_267 on 2008-07-16
I have a shared directory that can be accessed by all users in the "family" group and has the sgid bit set. I edited /etc/profile and changed umask to 002 instead of 022 but new directories created by nautilus don't have group write permission. Directories created using mkdir do have the correct permission.

Anyone know how I can set default file permissions for nautilus?

Thanks,
Adam

Edit: Found this [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/242618](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/242618), guess I just have to put up with it until the patch is applied.

---

