---
title: "[SOLVED] automount vfat partition on startup through fstab"
date: 2008-11-04
forum: Desktop Environments
---

### Post by larsdk on 2008-11-04
with both read and write permissions... I used to have this configuration, but now I cannot remember how I did it - anyone?

---

### Post by taurus on 2008-11-04
You can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add an entry in there for your fat32 partition, assuming it's /dev/sda1.

```
/dev/sda1 /media/windows vfat iocharset=utf8,umask=000 0 0
```
Save it and now create a new mount point for it.

```
sudo mkdir /media/windows
```
Mount it and see if you can write to it, /media/windows.

```
sudo mount -a
df -h
```

---

