---
title: "Shell Scripts and removable devices"
date: 2005-09-15
forum: Desktop Environments
---

### Post by sameat on 2005-09-15
I run a couple of shell scripts that compress and move some files to my usb thumb drive(s) as a cheap/dirty backup.  I have been manually mounting the usb drive(s) as follows:

mount /dev/sdc1 /mnt/usb -t vfat -o umask=000

I would prefer to use gnome-volume-manager to automatically mount any usb drive that I plug in to /mnt/usb.  I regularly swap multiple drives in and out, and they get mounted just fine, but they mount under /media/xxx.

Is there any way to restrict the mount point that gnome-volume-manager uses to /mnt/usb for all devices?

I'm running a server install with XFCE as the desktop environment.

thanks

---

### Post by xmastree on 2005-09-15
This might help. I recently screwed up the partitioning of my Sony Microvault. In the end I went into Windows and reformatted it, labeling it as Microvault.

Now it **always** mounts as /media/MICROVAULT whereas before it would be /media/usbsomething, or 1 or 2.

So, label it and it might just work like you want it to. It'll probably still be under /media rather than /mnt but that shouldn't be a problem I think, so long as it's always the same.

---

