---
title: "Can't access Windows partitions"
date: 2005-10-15
forum: Desktop Environments
---

### Post by snafoo on 2005-10-15
Hi,

I can not access my Windows partitions which are mounted automatically on boot up. They show up on the desktop, but when double clicking on it, it says I don't have permission for that. When I try to unmount them (right click -> unmount..) I get the message, that only root can do this.

An entry in /etc/fstab looks like this:

/dev/sda1       /media/sda1     ntfs    defaults       0       0


Do you have any suggestions on how to fix that?

Thanks!

---

### Post by RawMustard on 2005-10-15
Try this!
/dev/sda1 /media/sda1 ntfs ro,user,umask=0 0

---

### Post by snafoo on 2005-10-15
Thank you. That worked for me!

---

