---
title: "USB floppy mounts, but file manager thinks it's unmounted"
date: 2006-01-27
forum: Desktop Environments
---

### Post by DaneM on 2006-01-27
Hello, everybody.

I have an external USB floppy drive which I can mount in three ways:

1) pmount /dev/sda /media/floppy
2) sudo mount /dev/sda /media/floppy [after creating the directory]
3) [double-click on it in Nautilus]

...but regardless of how I mount it, it takes a REALLY long time to mount, and then when I double-click on it agoin in Nautilus (it won't actually open it the first time I double-click it) it gives me this error:

**Unable to mount the selected volume.**

The error messages in details reveal:

[B]Error: device /dev/sda is already mounted to /media/floppy
Error: could not execute pmount[/B]

Regardless of how I mount it, I can read the files in the console, but not in the file manager, unless I navigate through the filesystem to the mount point.

It really seems to be oblivious to the fact that the volume is already mounted.

Any help would be well-appreciated.

--Dane

---

