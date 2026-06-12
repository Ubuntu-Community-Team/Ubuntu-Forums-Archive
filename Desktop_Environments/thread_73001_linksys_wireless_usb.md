---
title: "linksys wireless usb?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by paperdiesel on 2005-10-07
I just installed ubuntu 5.10, and I'm trying to get my wireless usb card to work.  It's a linksys 2.4G usb device, version 4.  I read the docs about using ndiswrapper to use the windows drivers, but I can't get it to work.  I can install the drivers, and I verify with ndiswrapper -l that the driver is installed and the hardware is detected.  But when I run modprobe, the system hangs.  If I put the ndiswrapper line in my /etc/modules file, the system hangs on boot.  The only way to get it back is to unplug the usb device.  Has anyone configured their linksys wireless usb device correctly?  Help!

---

### Post by mlomker on 2005-10-07
If you are running Hoary then you'll probably have to download and install the latest ndiswrapper rather than the one that comes with Hoary.  [Here's a post]("http://www.ubuntuforums.org/showpost.php?p=386509&postcount=4") regarding the card.

---

