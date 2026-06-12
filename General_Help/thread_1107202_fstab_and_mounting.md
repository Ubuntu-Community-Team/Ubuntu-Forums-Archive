---
title: "fstab and mounting"
date: 2009-03-26
forum: General Help
---

### Post by c-m on 2009-03-26
I have a drive that i use for all my media. I have set it up in fstab to mount at /media/media and have created the necessary directory.

The problem is that when i load my computer the drive get automatically mounted at /media/disk-1 This messes up any programs that need access to the drive.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ff338fe-60e2-4fb0-89c5-14c3d81a974a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1943cb5d-ad7c-4b42-8547-a1a846c3dc1e /home           ext3    relatime        0       2

# /dev/sda3 /media/media           ext3    defaults        0       0

# /dev/sda4
UUID=19bce4ae-8557-43cf-ab18-757a03b1ebb1 none            swap    sw              0       0
```

Can you see any reason why the drive wouldn't mount where i set it to?

I am using Ubuntu UMPC 8.10

---

### Post by evilaim on 2009-03-26
# /dev/sda3 /media/media           ext3    defaults     0      0???

Well, we could start with you have commented out the line you're looking to use.  In the file you can't have # infront of a line or else it will be excluded.

************************** Try this, copy all below this line and paste into your fstab***************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ff338fe-60e2-4fb0-89c5-14c3d81a974a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1943cb5d-ad7c-4b42-8547-a1a846c3dc1e /home           ext3    relatime        0       2

/dev/sda3 /media/media           ext3    defaults        0       0

# /dev/sda4
UUID=19bce4ae-8557-43cf-ab18-757a03b1ebb1 none            swap    sw              0       0

---

