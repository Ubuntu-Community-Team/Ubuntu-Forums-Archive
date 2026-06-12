---
title: "Adding mount point to desktop"
date: 2009-01-14
forum: Desktop Environments
---

### Post by c0rv1d on 2009-01-14
Hi All!

I' mounting an iso file: 
```
sudo mount -o loop -t iso9660 isofile.iso "/media/isoimage"
```

which works - I can see the contents in /media/isoimage.

But is there a way for the mount point to show up as a removable drive (ie desktop icon that pops up when mounted and disappears when unmounted) and which can also be unmounted from within thunar?

I want to add it to fstab and have a custom action in thunar to right click on an iso file and mount it. :)

Thanks

Derek

---

### Post by c0rv1d on 2009-01-14
Anyone? :confused:

---

### Post by randcoop on 2009-01-15
I don't see how it can be done.  You're mounting using sudo mount, which is fine, but then Thunar won't be able to unmount it.  And getting an icon to pop up when it's mounted would have to be done through a script (mount the drive, create a desktop launcher, unmount the drive, delete the desktop launcher).  I haven't heard of anything like that being done anywhere.

---

