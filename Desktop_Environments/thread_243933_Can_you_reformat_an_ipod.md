---
title: "Can you reformat an ipod?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by codypumper on 2006-08-25
Is it possible to reformat and install firmware on an ipod from ubuntu?

---

### Post by astoltz on 2006-08-25
Sure.  Here's a pretty good link:

[http://pag.csail.mit.edu/~adonovan/hacks/ipod.html]("http://pag.csail.mit.edu/~adonovan/hacks/ipod.html")

---

### Post by codypumper on 2006-08-25
Thank you very much, but is there a way to do it with usb? As far as I can tell there isn't anything about usb.

---

### Post by codypumper on 2006-08-25
Well, is there a way I could mount it in wine, and reformat it with the hp usb reformat tool? Just curious

---

### Post by astoltz on 2006-08-25
I'm not sure what you mean by USB.  Is the the ipod not being recognized when you plug it in?  Ubuntu will treat the ipod just like a USB hard drive: it gets mounted at /media/ipod and there should be an icon on the desktop.  After that, the instructions on that link should make it easy to re-format and re-install the firmware.  I've done it several times myself.

One clarification though.  This is only for a Windows (FAT32) formatted ipod.  I don't know of an easy method to reformat a Mac (HFS+) formatted ipod.

---

### Post by codypumper on 2006-08-26
Okay, thank you very much. Guess I'm quite ignorant.
My whole ipod situation is quite a mess really. My ubuntu install doesn't detect my ipod unless I reboot, and the ipod its self is messed up after an installation of iPod linux messed up the partitions on the ipod, know ubuntu is giving me "mount: i could not determine the filesystem type, and none was specified". Its such a pain...

---

