---
title: "Strange Problem with USB Key"
date: 2006-08-17
forum: Desktop Environments
---

### Post by tristure on 2006-08-17
Hi,

I use Kubuntu, and so far everything worked quite perfectly. Recently, though, there have been some strange problem : the USB key won't unmount properly. Using the storage media applet it would work, but now, unmounting makes nothing, the key remains mounted until i unplug it.

I have corrupted a filesystem that way, so I try to avoid this...

Any ideas what I could do?

---

### Post by Ziox on 2006-08-17
> **tristure said:**
> Hi,

I use Kubuntu, and so far everything worked quite perfectly. Recently, though, there have been some strange problem : the USB key won't unmount properly. Using the storage media applet it would work, but now, unmounting makes nothing, the key remains mounted until i unplug it.

I have corrupted a filesystem that way, so I try to avoid this...

Any ideas what I could do?

have you tried umount from the command line?

i think the command is umount (the location of where it is mounted)

---

### Post by x64Jimbo on 2006-08-17
Don't forget to sudo that command.
sudo umount /media/sda1

---

### Post by tristure on 2006-08-17
It works, thank you. There seems to be a problem with the "umount" on the storage media applet. Maybe it's related to the key being mounted on "/media/USB KEY", which is quite strange, and with a space in it...

---

### Post by tristure on 2006-08-20
Does anybody know where I can change the USB key mountpoint? I can't find it in fstab. I think the mountpoint "/media/USB KEY" makes some things run wrong...

Thanks for your help

---

### Post by carontis on 2006-08-20
Try to see in mtab file, probably it resides there.

---

