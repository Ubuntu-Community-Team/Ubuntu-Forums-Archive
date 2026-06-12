---
title: "mount"
date: 2006-01-08
forum: General Help
---

### Post by Ocxic on 2006-01-08
when i try to mounts my stoarge drive hda1 i get this message:

mount: /dev/hda1 already mounted or /mnt/120GB_Storage busy

but mount -l says:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

### Post by aysiu on 2006-01-08
Regardless, why don't you try doing this before mounting it? ```
sudo umount /mnt/120GB_Storage
```

---

