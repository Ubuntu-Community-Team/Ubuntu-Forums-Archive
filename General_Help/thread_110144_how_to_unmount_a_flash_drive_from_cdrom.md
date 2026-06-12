---
title: "how to unmount a flash drive from cdrom"
date: 2005-12-30
forum: General Help
---

### Post by arg on 2005-12-30
did the following for an install

> 
Mount the flash drive to /cdrom using a command such as mount -t vfat /dev/sda1 /cdrom and then switch back to the first virtual console by pressing ""ALT-1"". Continue installing Ubuntu as if you were running from CD. 


how do i unmount it?

thanks
alan.

---

### Post by kaamos on 2005-12-30
If the drive was mounted to /cdrom

```
sudo umount /cdrom
```
This will unmount the sda1 usb-drive completely
```
sudo umount /deb/sda1
```

---

