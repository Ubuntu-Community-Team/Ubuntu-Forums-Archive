---
title: "Force a usb drive to mount to the same directory"
date: 2006-02-26
forum: Desktop Environments
---

### Post by sameat on 2006-02-26
I'd like to force my usb drives to mount in the same place every time.  

If I'm not mistaken, gnome volume manager does this by mounting special devices in /media/"device volume name".  For instance, if I have a flash drive with the volume name "flashdrive", it automatically mounts to /media/flashdrive.

In Kubuntu, it appears that my special devices are mounted differently.  Correct me if I am wrong, but it appears that the first partition on the first special device gets mounted to /media/sda1, and so on.

The problem is, I may have connected my special devices in a different order, which means that a given device isn't always mounted in the same location.

Is there any way to force this?  I need it for some scripts that I run.

Thanks

---

