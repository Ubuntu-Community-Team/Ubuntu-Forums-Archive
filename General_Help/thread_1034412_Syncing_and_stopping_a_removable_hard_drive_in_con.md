---
title: "Syncing and stopping a removable hard drive in conjunction with unmounting"
date: 2009-01-08
forum: General Help
---

### Post by jis on 2009-01-08
You can use 
```
/usr/bin/sdparm --command=sync
```
and
```
/usr/bin/sdparm --command=stop
```
commands, but they require use of sudo. Is there a better way to allow syncing and stopping a removable hard drive than to allowing sdparm without password by editing /etc/sudoers?

Does HAL do anything like that?

---

### Post by cariboo on 2009-01-08
What is it that you are trying to do? You can umount an external drive by right clicking and selecting Unmount Volume. The operating system will not umount the drive until all data has been written to it.

Jim

---

