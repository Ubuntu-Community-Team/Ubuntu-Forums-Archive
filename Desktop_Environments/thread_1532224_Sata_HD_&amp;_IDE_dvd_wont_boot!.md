---
title: "Sata HD &amp; IDE dvd wont boot!"
date: 2010-07-16
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-07-16
Just built a new machine, 500gb SATA hard disk and IDE DVD writer, all installed fine, did the updates, then on reboot the system hangs on detecting the IDE optical, wont boot unless I select safe mode. If I choose safe mode all works fine. If I unplug the optical drive everything works perfectly. I've changed everything in BIOS I can think of, Ive even tried putting another IDE device in and juggling master & slave on the IDE channel, no joy. I'm thinking the only way round this is to fit a SATA optical drive. It seems its getting confused when detecting the IDE device which device to boot from & ignoring SATA 0. In the post it detects the SATA devices, front panel USB's and SD card slots, then does a dercond detect for IDE devices where it hangs. Any ideas guys?
Steve

---

### Post by mister_p_1998 on 2010-07-16
Hmm on further examination, I unplugged one of the front panel USB plugs and it seems to be working ok, although I've lost two USB ports. I had this problem on a windows machine when installing with these front panel usb ports, they grabbed device letters and when I installed XP it went to the first free drive letter which was H: This caused problems with specialised educational software which insisted on installing to drive C: We fixed this in the end by pulling out the usb plugs, installing XP then plugging back in after the install and the system gave the USB ports the next free letters after C & D. Please dont tell me I've got to do this with Lucid! I thought  Linux was a better OS than XP!

Steve

---

