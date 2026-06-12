---
title: "can only use half of flash drive"
date: 2009-05-05
forum: General Help
---

### Post by aaronm111 on 2009-05-05
My 16GB microcenter usb drive became disconnected during a file transfer, after which it would not mount. I tried reformatting using Gparted and terminal but could only create an 8GB partion. Any ideas or should I get a new drive?

---

### Post by lensman3 on 2009-05-05
Mount the thumb drive as usual and use "dosfsck" without the quotes.  You will probably have to do something like "dosfsck /media/thumbdrive" at a command screen.  To get the name of the drive do the "du" command and the mounted thumb-drive will show.  "dosfsck" looks like it will reclaim lost clusters which you can later delete.  Do a "man dosfsck" to see all of the options for this program at a command prompt.

Hope this helps.

---

