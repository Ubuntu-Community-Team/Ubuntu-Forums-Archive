---
title: "How can i mount windows partition using terminal"
date: 2009-01-22
forum: General Help
---

### Post by arsen13 on 2009-01-22
I'm just starting learning Linux and I was wondering how i can mount a partition of hard drive where i have installed windows using terminal. Also how to mount and unmount usb sticks manually.

Thanks

---

### Post by x33a on 2009-01-22
type sudo fdisk -l

this will list all your partitions

note your windows your windows partition and type

mount /media/windows_partition

to unmount, type

umount /media/windows_partition

---

### Post by jerome1232 on 2009-01-22
Actually you'll need to specify the device path too, and you need to specify a umask if you want to actually be able to write to it. You also have to create the directory.

```
sudo mkdir /media/mountpoint
sudo mount /dev/sdxx /media/mountpoint -o umask=000
```

---

