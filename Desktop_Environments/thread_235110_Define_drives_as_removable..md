---
title: "Define drives as removable."
date: 2006-08-12
forum: Desktop Environments
---

### Post by computx on 2006-08-12
I have a laptop with a pcmcia media reader. when I insert a card it is detected as an ide drive and assigned to /dev/hde1
The problem is that Ubuntu doesn't recognize this as being a removeable drive and therefore doesn't auto mount it like it does usb removable drives.
I added an entry to fstab for it and can mount it by hand but would like for ubuntu to do this for me.

What config file do I need to edit to make ubuntu treat it as a removeable drive?

---

### Post by computx on 2006-08-15
I found a solution to this and thought I would share in case anyone else needs to know. read the solution at [http://computx.us/blog/index.php?/archives/4-How-to-fight-a-pcmcia-mediar-reader-and-win.html](http://computx.us/blog/index.php?/archives/4-How-to-fight-a-pcmcia-mediar-reader-and-win.html)

---

