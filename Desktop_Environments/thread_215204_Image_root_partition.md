---
title: "Image root partition"
date: 2006-07-13
forum: Desktop Environments
---

### Post by musther on 2006-07-13
When I've got my machine all set up my root partition only has about 3.5 gigs on it.  I'd love to be able to image this to a DVD and then, in the event that I mess up my setup and don't want to fix it, pop in the DVD and blat the image back onto the root partition.  Is there any software out there which makes this nice and simple, dare I say easy?

---

### Post by HAARP on 2006-07-13
Unmount the root partition. (Obviously, you need to boot from a LiveCD to do that ;))
```
sudo dd if=/dev/hda1 of=/wherever/image.raw
```
Now, simply burn the image to a DVD. To restore the backup, swap hda1 with image.raw.

---

