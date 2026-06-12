---
title: "new ntfs driver with kde"
date: 2006-07-16
forum: Desktop Environments
---

### Post by conexion200 on 2006-07-16
Hello!
Yesterday I have downloaded new ntfs-3g kernel module and I have compiled it. This is great, it allows me to write on ntfs partitions. But I have problem with kde. This driver uses FUSE so fstab looks like this:


```
/dev/hda1               /mnt/system     ntfs-3g         rw,umask=000,user      0 0
```

and mtab after mounting:

```
/dev/fuse /mnt/system fuse rw,nosuid,nodev,noexec,noatime,default_permissions,allow_other,user=yacek 0 0
```

So for kde it is too complicated, in fstab it is /dev/hda1 and in mtab it is /dev/fuse. So in konqueror system:/media and hda1 it shows nothing. Is there any solution to this?

---

