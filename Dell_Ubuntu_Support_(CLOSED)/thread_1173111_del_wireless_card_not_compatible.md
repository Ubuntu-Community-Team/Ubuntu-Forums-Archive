---
title: "del wireless card not compatible?"
date: 2009-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by theo.ew on 2009-05-29
I have a Dell Inpirion 1525 and for some reason the wireless card does not work with ubuntu 8.10. I have Vista installed but occassionally i run ubuntu from the live CD cause i really want to use Ubuntu(i can't however becuase my Wimba online classes don't work with it.) I can get the wireless to work when I plug in an external card(Belkin Wireless G USB Adapter) and then internal wireless card works in Vista. The interal wireless card is a 1395 WLAN Mincard. Any help?

---

### Post by Blue Sassley on 2009-05-29
The Dell branded wireless cards use a Restricted Driver, if I remember right its a Broadcom driver.

Have you thought about installing Ubuntu with the WUBI option? It works really really well:

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)

The other nice thing about it is since it installs inside of windows nothing has to change with your hard drive configuration.

To use WUBI just use your LiveCD and when you are logged into Windows Autoplay the CD and it will bring up the option to install Ubuntu inside of Windows.

If you find you don't like Ubuntu you can just boot into Windows and goto Add/Remove programs and Uninstall Ubuntu like any other program.

Blue

---

### Post by theo.ew on 2009-05-29
i'll try looking at the restricted drivers. I'll also look at the wubi option.

thanks

---

### Post by Blue Sassley on 2009-05-29
You should be able to use the restricted drivers on the LiveCD (I think) but you'll need to have it connected to the wired connection to download them, and the other problem is of course once you reboot everything is gone on a LiveCD.

Blue

---

### Post by Blue Sassley on 2009-05-29
Also if you look a little farther down on the Dell Support forums you'll see this thread, but I think this guy was doing a upgrade from 8.10 not a clean install:

[http://ubuntuforums.org/showpost.php?p=7214509&postcount=1](http://ubuntuforums.org/showpost.php?p=7214509&postcount=1)

Blue

---

### Post by GavCity on 2009-05-29
My 1520 works with B43-fwcutter, you use the following terminal command to get it.

sudo apt-get install b43-fwcutter

You need to enable it in System -> Administration -> Hardware Drivers, and disable any other wireless drivers you have enabled.

---

### Post by coffeeaddict22 on 2009-05-31
Hi,
Just be a bit careful what you install.  My Dell wouldn't work without ndiswrapper in 8.04; the Broadcom drivers were sorted for 8.10.  One of the big improvements in the last 12 months has been wireless, so a lot of the info on the 'net has become out of date.
You're almost certainly running a Broadcom chip.  Because of the mandate to keep Linux free, if the driver isn't open source it's not part of the install CD, and you have to accept the risk involved.  Mainly, that risk is that the manufacturer will stop caring about it's Linux driver, but still...
What that means in practice is that once you've installed/ booted up the Live CD, you'll need to download the Broadcom driver- as mentioned above.

A piece of info your post is missing is the chipset.  Type ```
lspci
``` in a terminal, and it'll tell you which chipset you need a driver for.

Another option instead of wubi is a dual boot.  It's not terribly difficult, and means you get to stop carrying discs around.  Have a look at [this link]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm") for an excellent step-through.

---

