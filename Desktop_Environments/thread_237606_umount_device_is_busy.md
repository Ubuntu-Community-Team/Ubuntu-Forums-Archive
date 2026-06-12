---
title: "umount: device is busy"
date: 2006-08-16
forum: Desktop Environments
---

### Post by anodizer on 2006-08-16
I'm getting this error every time I try to unmount a ntfs partition which is mounted on boot through fstab. I just want to mount it sometimes with ntfs-3g (no, I don't want it permanently mounted with ntfs-3g driver).
Maybe the mounted partition is used by some applications, is any workaround for this?

---

### Post by Ramses de Norre on 2006-08-16
```
sudo fuser -m /dev/hda1
```
Will show you all processes accessing hda1, you can then kill those processes and unmount the device.

---

### Post by anodizer on 2006-08-16
I'm getting nothing with this command.

---

