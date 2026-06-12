---
title: "Generic card reader"
date: 2005-12-25
forum: Desktop Environments
---

### Post by Daandaan on 2005-12-25
Does someone know how to change permissions for my generic card reader. When I view permissions I see that the owner, groups and others **only can read.** How can I change this?:confused: I already tried sudo chmod 777 /media/usbdisk => that's where ubuntu mount's my generic card reader.

---

### Post by sciurus on 2005-12-25
That command only changed the permissions of the directory, not its contents. To change the permissions of the contents of a directory, you would need to use ```
chmod -R a+rwx /media/usbdisk/*
```. However, this is not a good solution, since your cardreader surely uses a FAT filesystem which doesn't support permissions.  If you know what device it is, I would unmount it and remount it with flags such as umask=000. [This thread]("http://ubuntuforums.org/showthread.php?t=105302") might help.

---

