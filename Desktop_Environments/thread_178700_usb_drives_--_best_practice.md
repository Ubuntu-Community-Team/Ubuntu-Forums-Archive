---
title: "usb drives -- best practice?"
date: 2006-05-18
forum: Desktop Environments
---

### Post by linuxNewb on 2006-05-18
Unlike Windows, with Ubuntu I can use all my usb devices (drives) without installing extra software/drivers. I plug in my camera or mp3 player, and Ubuntu mounts it and opens a nautilus window (I love Ubuntu).

My question is: What is the best/safest practice for closing the connection when I'm done? Is it best to physically switch of the external device? Should I 'unmount' the device first? What's the proper way of doing this to avoid problems, or does it not matter?

Thanks in advance.

---

### Post by skirkpatrick on 2006-05-18
You should unmount the device.  This will cause any pending operations that are cached (held in memory) to be written to the drive.  The OS does this for a couple of reasons.  One is that reading and writing to the cache is much faster and two, it will actually extend the life of your flash device as they have a limited number of erase/write cycles (in the millions but still).  With my USB pendrives and camera card devices, performing an unmount will cause the active light to turn off at which point it is safe to remove the device.  This is essentially what Windows XP does when you click on the icon to "safely remove device".

---

