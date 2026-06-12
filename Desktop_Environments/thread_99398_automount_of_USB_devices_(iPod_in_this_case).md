---
title: "automount of USB devices (iPod in this case)"
date: 2005-12-05
forum: Desktop Environments
---

### Post by pnmcosta on 2005-12-05
Hi,

I have an external USB HD, and an iPod. i only connect the ipod sometimes.

I had some problems unmounting the iPod, fortunately doing eject <devname> with sudo i managed to do it succeffully but i have to check everytime witch device the ipod is (running mount). If it ejects with sudo it is a permissions problem. i tought about adding it to the fstab so that i could give my user permissions to unmount the device but how do i know witch device it's going to connect with? if it changes to the next available (i assume). i'm not a newbie with linux, but not a guru either. just trying to get my head into this mounting issues..

thanks you very much for your help.

---

### Post by astoltz on 2005-12-05
From the eject man page:
> eject [-vnrsfqp] [<name>]

The device corresponding to <name> is ejected. The name can be a device file or mount point, either a full path or  with  the  leading  "/dev", "/media"  or  "/mnt" omitted. If no name is specified, the default name "cdrom" is used. So the command I use is just "eject ipod" but you'd have to substitute whatever name your ipod gets mounted as.

As far as permissions, check [this]("http://ubuntuforums.org/showthread.php?t=99358") thread.  No solutions yet but...

---

