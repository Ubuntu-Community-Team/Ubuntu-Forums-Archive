---
title: "Nautilus thinks my external drive is a picture cd..."
date: 2008-11-03
forum: Desktop Environments
---

### Post by LastChildren on 2008-11-03
First off, I'm using Ubuntu 8.10.  For some reason, whenever I connect an external usb hard drive (and I've tried this with two different hard drives) Nautilus seems to think it's a picture CD and asks me if I want to use F-Spot to browse it.  The drives mount and work fine, I'm able to browse/read/write to them, but while I have the browser open, Nautilus insists it's a picture CD.  Anybody know why this is?

---

### Post by messiah89 on 2008-11-04
hey, im also having this problem, i didnt until just now tho, i use to have my external harddrive setup in fstab to force mount because windows always shits it, but i then i plugged a flash drive in and it tried to use sdb1 to mount and it did not like that.
so i removed it from fstab and got them both mounting normally but now my external harddrive appears as a picture cd....

also on a sidenote

im relatively new to ubuntu but i was wondering if when i have a harddrive in fstab to force mount i need to be root is it possible to modify either the drive or my account so it doesnt require root?

---

### Post by dbcoolio on 2008-12-18
Apparently if there is a directory named "pictures" in the first level, Intrepid marks it as a picture CD.  It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936")

---

### Post by ohmyiv on 2009-02-01
I can't have a folder named pictures, that's freaking genius...

Thanks for the info, I hope they fix that soon.  It's yet one more reason I believe Ubuntu is not ready for the masses.

---

### Post by doyouhas on 2009-02-01
Had the same problem, but then deduced it was because of the folder name. This bug needs fixin', if not already done.

---

