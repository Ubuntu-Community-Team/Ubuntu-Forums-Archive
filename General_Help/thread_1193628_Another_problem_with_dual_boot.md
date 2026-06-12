---
title: "Another problem with dual boot"
date: 2009-06-21
forum: General Help
---

### Post by bushtangu on 2009-06-21
ok i spend all my afternoon to install grud and finally i made it everything works fine. the grud boot menu is showing and ubuntu boot correctly but th eproblem is with windows now. It show me the error : invalid boot.ini file and later broken hal.dll file !!!
any help please, because i'm really tired about all this now. thank you

---

### Post by Gen2ly on 2009-06-21
Yeah, hmm.  The boot loader (grub) is running ok so it looks like the problem is with Windows.  The boot.ini file used to be a file that had boot information.  I say used to because Vista doesn't use it anymore.  This is very likely not an Ubuntu problem and more likely has to do with windows.  Might be best to ask in a Windows forum as it would be more likely be able find someone that knows about this.

---

### Post by zelhar on 2009-06-21
> **bushtangu said:**
> ok i spend all my afternoon to install grud and finally i made it everything works fine. the grud boot menu is showing and ubuntu boot correctly but th eproblem is with windows now. It show me the error : invalid boot.ini file and later broken hal.dll file !!!
any help please, because i'm really tired about all this now. thank you

What version of windows do you use ?

---

### Post by zelhar on 2009-06-21
OK, if you use windows >= vista, then restore the master boot sector with the Vista CD:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

and then install in Vista "Easy BCD":
[http://neosmart.net/gallery/v/neosmart/EasyBCD/1_70/](http://neosmart.net/gallery/v/neosmart/EasyBCD/1_70/)

Using this free application you can set your boot menu from Vista.

The catch is- you would then need to reinstall grub to the partition where Ubuntu is installed, or anywhere other than the master boot.

---

### Post by bushtangu on 2009-06-21
sorry i forgot to tell that i use XP

---

### Post by merlinus on 2009-06-21
You could try supergrub:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by zelhar on 2009-06-21
EasyBCD should also support XP, but you can also try to reinstall grub cause it can dual boot just fine with XP.

---

