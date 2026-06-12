---
title: "backtrack 3"
date: 2009-04-21
forum: General Help
---

### Post by hezy00 on 2009-04-21
Hello,
I've just bought today wifi usb adapter; edimax ew-7318usg , I restart the BT in live mode from cd and it seems that it doesn't recognize the device (at least not outomatically). I got a cd with drivers for linux with it, only I don't know how to install it since there are drivers for several linux versions and the files names are unfamiliar to me at that point. I realy like to have your advice for the next steps have be done. Thanks,
Hezy.

---

### Post by StuartN on 2009-04-21
Apparently your dongle has a chipset that requires an RT73 driver ([http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)) but it should be detected and loaded automaticaly. Type lsusb in a terminal and search for the id for specific details.

---

