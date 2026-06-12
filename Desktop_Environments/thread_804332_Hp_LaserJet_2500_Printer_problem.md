---
title: "Hp LaserJet 2500 Printer problem"
date: 2008-05-23
forum: Desktop Environments
---

### Post by rafttrip on 2008-05-23
I am having trouble with an HP color LaserJet 2500 printer. I have try ed to install it on my desktop as well as my laptop and am having similar problems.

The printer appears to install correctly but will not print.

I get a message after a short wait that says "Printer may not be connected?"

I'm pretty sure it is connected because I printed with it just 5 minutes ago when I booted Vista to see if there was an issue there.

Any help would be greatly appreciated.

---

### Post by chandra on 2008-05-23
Take a look at:

[http://hplip.sourceforge.net/models/color_laserjet/hp_color_laserjet_2500.html](http://hplip.sourceforge.net/models/color_laserjet/hp_color_laserjet_2500.html)

which says that your printer is supported by HPLIP in Ubuntu 8.04 (last row of table).

It might help to file a bug in Launchpad under HPLIP at

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

and proceed from there.

---

### Post by rafttrip on 2008-05-30
I'm not sure how I go about doing that. Is there an error file I can send or something? I don't know what the error is all it dose is send the file to the printer and it just stays in the printer cue indefinitely:confused:.

---

### Post by rafttrip on 2008-05-30
administrator@administrator-desktop:~$ lsusb
Bus 005 Device 007: ID 0718:0111 Imation Corp. 
Bus 005 Device 006: ID 04a9:2212 Canon, Inc. CanoScan 5000F
Bus 005 Device 003: ID 058f:6377 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:0717 Hewlett-Packard 
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000  
administrator@administrator-desktop:~$ 


dose this help?

---

### Post by rafttrip on 2008-05-30
I filed a bug report.

---

### Post by iainv on 2008-07-24
I'm having the same problem.

Eventually I managed to get it to work with my desktop by uninstalling the drivers and then randomly plugging it in and reinstalling things until it somehow worked, but it comes up as "unknown" and I have to plug it in after the machine boots or it won't detect it.

Unfortunately a similar random approach isn't working with my laptop.

lsusb also detects it as for yours.

Iain

---

### Post by iainv on 2008-07-25
I've got it working.

The Device URI that is selected when the printer is autodetected is hp://usb/hp_color_LaserJet%202500?serial= and then a long number.

Replacing this URI with:

hal:///org/freedesktop/Hal/devices/usb_device_3f0_717_999999996434_if0_printer_noserial

makes the printer function perfectly.
I found the above URI by randomly installing and uninstalling anything I could to get it to work originally, and this was one setting that came up.

With a plain install of Hardy on my laptop, letting the computer detect the printer and then just changing the URI to the one I discovered on my desktop, it worked first time.

Iain

---

### Post by rafttrip on 2008-07-28
I' not sure how I go about changing the URI, can you let me know how to do that?

Thanks

---

### Post by iainv on 2008-08-01
If you go to System > Administration > Printing and click on whatever your system has recognised as the HP 2500, one of the boxes that comes up is "Device URI".

Simply cut and paste what i've written above into the box and see if it works.

For more info on what it is, have a look at the HAL bit on freedesktop.org

Iain

ps - when cutting and pasting make sure the URI ends in "noserial" - for some reason a space is inserted above that makes it look like "noseri al" but it shouldn't do.

---

