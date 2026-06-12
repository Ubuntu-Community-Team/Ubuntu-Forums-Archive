---
title: "upgrading print drivers to gutenprint?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by silex88 on 2006-01-27
Hi,

I have an Epson Stylus CX3810 which isn't supported in ubuntu 5.10. Apparently, there is support for it in the latest version of gimp-print (now gutenprint 5.0 I think), but that package doesn't exist in any of the breezy repositories (or, at least, I couldn't find it there).

First I tried downloading the gutenprint source, and it took me a while to get it to compile but I eventually succeeded, but then when I go to the printer configuration from the gnome menu the printer drivers haven't changed (still missing anything that will work with CX3810).

So, next I found the gutenprint package by searching google but it is for the experimental 6.10 ubuntu "dapper", and when I try to install it there are a bunch of unresolved dependencies. Then I made the mistake of attempting to upgrade the distribution first using apt-get dist-upgrade then from a downloaded iso of dapper, and both gave me a system with a misconfigured X that I couldn't fix with dpkg reconfigure-package xserver-xorg.

Now I'm back to breezy but I don't want to give up on getting the printer working. Any recommendations?

Cheers

---

### Post by bikeman on 2006-01-27
Wow, talk about a coincidence!  I just had to configure my Epson as well (C86 though).  From what I can see gutenprint is still in the release candidate stage, so it is not the current stable release.  On the same [page,]("http://gimp-print.sourceforge.net/") I would suggest that you download [gimp-print 4.2.7]("http://prdownloads.sourceforge.net/gimp-print/gimp-print-4.2.7.tar.gz?download").  It indicates that the CX3200 is fully operational, so hopefully it will also work with the CX3210.

Delete the printer from System-Administration-Printing.  Then compile gimp-print.  Please note that when I first compiled with ./configure, I got a ton of errors, because there were at least 10 packages missing.  I simply used sudo apt-get install *package* for each of the ones noted as not found.  Not all were in the repositories (at least the ones in my setup), but I was able to get enough to successfully ./configure, make, and make install.  Then I went back to System-Administration-Printing, added the printer (you may need to choose the closest one if yours is not on the list).  Gimp-print should appear as the recommended driver, don't click install driver, just click to continue.  Gimp-print will be used as the driver, which will hopefully work for you.  Then try to print a test page.  It worked for me.  Good luck.

---

### Post by silex88 on 2006-01-28
Well, my problem is it's the CX3810, and for that I think I need gutenprint 5.0?

---

### Post by silex88 on 2006-01-28
update: got it working by downloading and installing the latest gutenprint5.0-rc2, then decompressing the ppd file for the epson cx3810 found in the src/cups/ppd directory and manually pointing to it in the printer configuration from system->admin->printers

---

### Post by Wulfrunner on 2006-01-29
I have an Epson Stylus CX3200; the printer was recognized by Ubuntu, although I had to make sure it was connected and turned on when booting the computer (restarting cupsys did not work) in order for it to be autodetected. I was under the impression that gimp-print 4.2.7 was installed by defalt with the foomatic-db-gimp-print package? Although the CX3200 is supposedly fully supported, I have had problems with the print margins (the top margin is cut off and the bottom margin is too large). 

To correct this (hopefully), I have installed gutenprint-5.0.0-rc2 by compiling it from source. I needed libcupsys2-dev, libcupsimage2-dev,  and some other packages (basically most of the cups development packages). After restarting /etc/init.d/cupsys and removing the Stylus from GNOME Printer Administration, I was able to add the printer again using the Gutenprint drivers. Unfortunately, it did not install in English (I did not have the character sets to display some of the text), and there were about a dozen "Standard" drivers listed for the printer with nothing to differentiate them. Furthermore, installing Gutenprint did not solve my problem with the page margins and I am still stuck.

---

### Post by brucetan on 2006-02-13
dear silex88,

I have an epson stylus cx4100 (all-in-1) usb printer which is not listed in the vanila ubuntu's printer list.

I would like to try gutenprint and saw your thread --
> update: got it working by downloading and installing the latest gutenprint5.0-rc2, then decompressing the ppd file for the epson cx3810 found in the src/cups/ppd directory and manually pointing to it in the printer configuration from system->admin->printers

Can you share with me where did you download gutenprint 5.0 and the detail steps to installing as I am very new to Linux or ubuntu?

Many thanks in advance.

---

### Post by brucetan on 2006-02-14
After installed gutenprint, I am able to use my Epson Stylus CX4100 printer now.

FYI: I followed the following how-to thread to install gutenprint.
[http://ubuntuforums.org/showthread.php?t=119595]("http://ubuntuforums.org/showthread.php?t=119595")

Because CX4100 is a all-in-1 printer,i.e. it has a built-in scanner, I want to use the scanning function but I don't how.  Anyone has any idea to go about doing scanning with CX4100?

---

