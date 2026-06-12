---
title: "Samsung ML-1740 print problem after dapper install."
date: 2006-09-09
forum: Desktop Environments
---

### Post by MiniMe on 2006-09-09
Hello,

I've made a clean install of Dapper. In Breezy, my Samsung ML-1740 worked perfectly with the supplied ML-1710 driver. With Dapper, the printer installation seems to go smoothly, the test page works fine. I can also print from Open Office. However, if I try to print from other applications (I've tried with the text editor (gedit), Firefox, and Adobe Acrobat reader), I just get strange fuzzy horizontal lines on the paper.

I've tried using the ML-1740 driver from samsung.com, as well as the Samsung ML-4500 driver as was suggested by this post: [http://ubuntuforums.org/showthread.php?t=188685](http://ubuntuforums.org/showthread.php?t=188685)

I've also tried with both a USB and parallel port connection.

All with the same result: I can't print with the applications I've tried other than Open Office.

It's not a problem with the printer because it works properly in Windows 2000.

Any suggestions? Help would be greatly appreciated.

---

### Post by MiniMe on 2006-09-16
Arrrg, it's unfortunate. I guess I'll have to suffer like this for a while until hopefully Edgy solves the problem. :frown:

---

### Post by go2dell on 2006-09-16
I have an ML-2250, not a 1740, but since Samsung updated their driver I've had great success in getting it to work.  The same driver package works for all Samsung printers now, so you'll be using the one I'm using.

You should probably take a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=65111"), which seems to have become the unofficial Ubuntu-Samsung Laser Printer Repository of All Present and Disputed Knowledge.

My first suggestion is to make sure to zap all references to the printer in *System > Administration > Printing* before you try to install again.

My second suggestion is to try installing the printer manually after you do the driver installation.  When I attempted to install using the Samsung driver after their initial update, it didn't completely work.  All the parts were installed, but it didn't really complete the process.  Just going into *Printing* after the driver installation and trying to install my printer from there then worked perfectly.  I have noticed the oddity that the printer is configured as a Network Printer (CUPS IPP) with URI usb://Samsung/ML-2250.  I initially enabled full CUPS web interface administration, but some people have reported that's no longer necessary.  Since I first installed, Samsung has made some minor driver updates, so it may work better for you.

---

### Post by MiniMe on 2006-09-16
Thanks for the reply. After following your advice and using some tips in that thread you mentioned, I managed to get the printer working properly with a Samsung ML-1710 driver after installing the software from samsung.com. For some reason when I tried to select the ML-1740 driver in System -> Administration -> Printing, the "Forward" button was not clickable. So I resorted to the ML-1710 driver everything works well now.

Thanks again.

---

