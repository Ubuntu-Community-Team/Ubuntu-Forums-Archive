---
title: "How to compile a driver"
date: 2006-05-13
forum: Desktop Environments
---

### Post by link141 on 2006-05-13
Though very unlikely, I popped in the CD with the drivers for my motherboard to see if it had linux drivers.  To my surprise there was a folder with linux drivers in it!  Finnally a company that supports linux!  The problem is that there wasn't a driver for ubuntu.  It has all of the source files though, but I don't know how to compile the drivers.  Could someone give me instructions or a link on how to compile ubuntu packages?
Thanks

---

### Post by az on 2006-05-13
[QUOTE=link141]Though very unlikely, I popped in the CD with the drivers for my motherboard to see if it had linux drivers.  To my surprise there was a folder with linux drivers in it!  Finnally a company that supports linux!  The problem is that there wasn't a driver for ubuntu.  It has all of the source files though, but I don't know how to compile the drivers.  Could someone give me instructions or a link on how to compile ubuntu packages?
Thanks[/QUOTE]
What hardware specifically?  Those drivers are probably already included in the ubuntu kernel.

---

### Post by link141 on 2006-05-13
My motherboard is an ASUS-P48MX with some weird integrated graphics chip (sorry I don't know the specific name).  I think that it might not be included with the ubuntu kernel, because a certain program that deals with graphics runs slower than on windows.  I could be wrong though, because I'm running Ubuntu of an ancient 10 GB ATA drive and windows of a more recent 80 GB ATA drive.  Is there any way to check if Ubuntu detected the graphics chip though?

---

### Post by vidak on 2006-05-14
[QUOTE=link141]My motherboard is an ASUS-P48MX with some weird integrated graphics chip (sorry I don't know the specific name).  I think that it might not be included with the ubuntu kernel, because a certain program that deals with graphics runs slower than on windows.  I could be wrong though, because I'm running Ubuntu of an ancient 10 GB ATA drive and windows of a more recent 80 GB ATA drive.  Is there any way to check if Ubuntu detected the graphics chip though?[/QUOTE]

I took a quick look on ASUS' website [http://www.asus.com/products2.aspx?l1=3&l2=-1](http://www.asus.com/products2.aspx?l1=3&l2=-1)
and found no motherboards with this specific name, however there were some similar ones, with integrated graphic cards (VIA,Intel, SiS). Those drivers should be integrated in the kernel (I'm not sure about VIA).
You could check the graphic card's type with lspci. Look for the lines
VGA compatible controller
and
Display controller.
After install I checked  my card using armagetron :mrgreen: but you can use any other game using 3D effects...

---

