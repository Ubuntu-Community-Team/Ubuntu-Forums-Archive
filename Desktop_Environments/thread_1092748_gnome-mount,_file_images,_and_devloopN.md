---
title: "gnome-mount, file images, and /dev/loopN"
date: 2009-03-10
forum: Desktop Environments
---

### Post by mutantgn0me on 2009-03-10
Hey folks.  I've been trying to figure out some way to get gnome-mount to mount a file like a regular disk.  What I've got are a number of small files that are encrypted containers (using LUKS).  My plan is to write a script that calls gnome-mount to mount the file (once the encrypted container is opened).  My only problem is that passing the UUID of the file/image to gnome-mount doesn't work:

```
user@hostname:~$ vol_id --uuid /dev/mapper/luks_file
49A8-8055
user@hostname:~$ gnome-mount -v -h /org/freedesktop/Hal/devices/volume_uuid_49A8_8055
gnome-mount 0.8
X display not available - using text-based operation.
** Message: Given device '/org/freedesktop/Hal/devices/volume_uuid_49A8_8055' is not a volume or a drive.
```

I've tried just passing the hex number as well, but that doesn't seem to work.  Now, I know it's not really a volume or a drive, but I can mount it like one.  Is gnome-mount just not capable of dealing? Or (more likely) is there a magic syntax I haven't figured out yet? I'm not entirely convinced that the HAL string (/org/freedesktop/etc) is actually correct for a file image, but days of searching the interwebs haven't suggested anything better.

Any thoughts/ideas/words of warning? Thanks much!

---

