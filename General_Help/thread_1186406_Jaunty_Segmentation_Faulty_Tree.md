---
title: "Jaunty Segmentation Faulty Tree"
date: 2009-06-13
forum: General Help
---

### Post by tsav87 on 2009-06-13
I can't open synaptic package manager, can't open update manager, and if I try to install anything from the terminal I get it returns this "segmentation fault".

I can run sudo apt-get update just fine, but if I run sudo apt-get upgrade, it returns this: Segmentation faulty tree...50%

How do I fix this?

---

### Post by quixote on 2009-06-15
Segmentation faults are bad.  It's probably not a good idea to keep running your system without dealing with it, because one of these days it'll overwrite a critical area and you'll be facing data loss and/or a reinstall.

The fact that you can't run the graphical updates, but can run it from the command line, implies that gksudo isn't working.  Possibly it's one of the things already hit by the segfault.

Next time you boot, don't let it go the normal way.  Choose recovery console.  Once you're there, type ```
fdisk -l
``` and see what the designation of your boot drive is.  It'll have an * next to it, and look something like /dev/sda1.  For the examples below, I'll use that, but substitute whatever yours really is.

First, to be safe, explicitly unmount it: ```
umount /dev/sda1
``` It'll probably tell you it's not mounted.

Then run ```
fsck -y /dev/sda1
``` That's "filesystem-check" and the -y says to answer all questions with "yes".  Unless you really know what you're doing, that's what you wind up doing anyway.  You may find no filesystem errors, or thousands, in which case it's nice to have the system just deal with it.

Then to get out of recovery console, I think you can type ```
reboot
``` but if that doesn't work, try ```
halt now
```

When you boot normally, if the whole process helped, you shouldn't be seeing segfaults!

---

