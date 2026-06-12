---
title: "Reinstalling Grub"
date: 2006-08-01
forum: Desktop Environments
---

### Post by roflcopter_1 on 2006-08-01
I installed Windows and it went Ok, and now I'm trying to reinstall GRUB using a live cd. When I enter ```
sudo grub-install /dev/hda
``` I get: Could not find device for /boot: Not found or not a block device. I found something that said to do "sudo chroot /dev/hda" first, but it says:chroot: cannot change root directory to /dev/hda: Not a directory. What should I do? I thought this'd be a lot simpler.

---

### Post by Jhongy on 2006-08-01
do this to see what hard disks you have in your system:

```
sudo fdisk -l
```

What disks are there? You probably have a SATA drive, which might show as /dev/sda rather than /dev/hda. In which case the command you're looking for is:

```
sudo grub-install /dev/sda
```

J

---

### Post by Jhongy on 2006-08-01
...

---

### Post by roflcopter_1 on 2006-08-02
Its /dev/hda for sure. I'm still getting the same message. I thought all you had to do was sudo grub-install /dev/hda and it would install. What else do I need to do?

---

