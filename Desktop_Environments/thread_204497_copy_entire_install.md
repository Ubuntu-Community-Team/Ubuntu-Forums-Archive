---
title: "copy entire install?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by kabanta on 2006-06-27
What is a straight-forward way to copy an entire install from one place to another? For example: copy *everything* on the LiveCD to a USB drive -- or a working install from one USB drive to another?

I have Dapper installed on a partition of an external USB drive and am trying to copy it to another directory, "tmp-ubuntu." I tried using "cp -rL" so that symlinks would be preserved, but this didn't quite work. Also there are other errors that occur:

```
cp: **cannot create special file** `tmp-ubuntu/lib/udev/devices/stderr': Operation not permitted

cp: **cannot open** `/media/usbdisk/lib/udev/devices/core' for reading: Operation not permitted

cp: **setting permissions** for `tmp-ubuntu/lib/dhcp3-client/call-dhclient-script': Operation not permitted
```

Any suggestions for additional flags to "cp" -- or an alternative way to create a complete copy?

---

### Post by aysiu on 2006-06-27
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) may help.

---

### Post by kabanta on 2006-06-27
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) may help.[/QUOTE]
Great tip, thanks! PartImage is very useful. However, in my case, it behaves in an undesirable way. Namely, although it creates an image that takes up only the amount of space *used* on the source partition, it fails if we try to restore the image to another partition that is smaller than the original *partition.*

In other words, if I have:

Original:         2gb  partition --  600mb usage
PartImage image file from above: 600mb
Destination:   1gb partition

PartImage will complain with a segmentation fault when it attempts to restore the 600mb image file it created to the new 1gb partition.

Any other tips? I would imagine there is some standard command-line utility would do this. But searching on "copy" just brings up too much stuff.

---

### Post by Gustav on 2006-06-27
Use the -a flag (or at least the -p flag (it preserves permissions))

---

### Post by kabanta on 2006-06-27
[QUOTE=Gustav]Use the -a flag (or at least the -p flag (it preserves permissions))[/QUOTE]
Ah, ok, that feels like it should work. However, I had some trouble initially -- getting the same errors about permissions, etc. The origin directory is owned by root, so then I tried to copy as "su" to a test destination directory (on internal drive) also owned by root. That copy worked successfully.

However, if I try to do this then with the destination as an external drive, that external drive mounts as owned by a regular user (me). I've tried changing ownership of source directory (and all subdirectories) and tried to change the ownership of the mounted external destination drive. So far, nothing I have tried has worked.

Any tips for solving this? Is there a way to specify that an external drive be mounted as owned by root? Or ...?

---

