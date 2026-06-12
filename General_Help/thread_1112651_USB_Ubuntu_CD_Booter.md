---
title: "USB Ubuntu CD Booter"
date: 2009-03-31
forum: General Help
---

### Post by xr4v3nx on 2009-03-31
Any tried running Ubuntu using a CD Booter and an Ubuntu OS in an USB? Because my BIOS doesn't show any USB on the disk priority when I tried to look at it. My PC is COMPAQ Presario S6200CL made in 2003. Older PCs such as those made before 2001 are those who are not USB enabled yet. So why can't I see a USB Drive on the disk priority of my BIOS so I can directly boot on the USB without the use of a CD Booter. Thanks in advance!

---

### Post by SnickerSnack on 2009-03-31
If USB is not an option available, then it is not possible to boot from a usb drive with the computer as it is now.  You may be able to get a bios update from the manufacturer.

Edit: Try this: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=&cc=us&product=390423&lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=&cc=us&product=390423&lang=)

---

### Post by xr4v3nx on 2009-04-01
i spoke with an HP representative but she said that there are no updates for the BIOS of my PC. Well...

---

### Post by dandnsmith on 2009-04-01
Have a look at [the pendrive site](http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/) which seems to contain what you want - there are a number of different pages which might help there. You should look at the pages for making boot CDs as well.

So far, I've only used this stuff to run a live install on USB stick, but the full thing is my next aim.

---

### Post by xr4v3nx on 2009-04-01
i tried the steps on the pendrive site..but it wont work... T_T

---

### Post by SnickerSnack on 2009-04-02
> **xr4v3nx said:**
> i spoke with an HP representative but she said that there are no updates for the BIOS of my PC. Well...

The link I gave has the current bios update.  Did you try it?  Or is it the one you already have?

---

### Post by xr4v3nx on 2009-04-03
The website that you gave me has updates on the BIOS of my PC but there are no enhancements/improvements such as USB Booting. The only new thing that they added is "Fixed some logo issues". WTF! How lame that update is. I'm getting frustrated right now. I desperately need to run Ubuntu in my USB. I don't want to repartition.

---

### Post by SnickerSnack on 2009-04-03
Wow, that is a lame update.  It sounds like there isn't anything you can do.

What boot options are available?  Just a though which probably won't work: if the serial port is listed, maybe you can get some kind of adapter to connect the usb drive via the serial port.

Also, I believe that with 8.10 intrepid you can install ubuntu on the windows partition.  Also, this might help: [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by xr4v3nx on 2009-04-03
nice..lemme try that wubi thing. by the way..does daemon tools affect something about scsi? because i also tried SLAX in usb through CD booting and it cant boot. it mentioned something about a problem with my scsi...

---

