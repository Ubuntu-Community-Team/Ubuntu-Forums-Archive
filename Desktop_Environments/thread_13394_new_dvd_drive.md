---
title: "new dvd drive"
date: 2005-01-31
forum: Desktop Environments
---

### Post by wilhelm on 2005-01-31
i have installed a new dvd-rom, my machine picks it up but doest do the auto mount, like with my cdrw drive. both are Aopen drives, and i am using warty. i had to manually mount the drive to view the files on the dvd i placed in the drive.

any thoughts on how i can get it to work like the cdrw... ?

---

### Post by mendicant on 2005-01-31
I suspect you want an entry in /etc/fstab, which probably already contains one for your cdrom.  You can typically just copy the cdrom entry, changing the device name and the mount point to the correct things--what you used in your manual mount.

---

### Post by wilhelm on 2005-02-02
thanks i will do that tonight, i was just wondering why it didn't do it already, though i might be missing sum files for watry to communicate properly with my dvdrom...

---

