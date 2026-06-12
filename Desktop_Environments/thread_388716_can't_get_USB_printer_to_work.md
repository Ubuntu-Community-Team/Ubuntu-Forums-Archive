---
title: "can't get USB printer to work"
date: 2007-03-19
forum: Desktop Environments
---

### Post by bcrowell on 2007-03-19
I'm trying to get a USB laser printer (Brother HL-1440) to work on Breezy. I went to System>Administration>Printing>New Printer in GNOME, and set it up as USB Printer #1, using the default driver. However, when I try to print, the printer properties dialog say "Printing: Printer not connected, we'll retry in 30 seconds." The printer is connected to a usb port, and is powered on. /var/log/messages seems to show that USB is enabled. (My mobo has a VIA VT8235 controller.) The usbview utility complains that the /proc/bus/usb/devices directory doesn't exist. I tried doing a "mount -t usbfs none /proc/bus/usb". After I do this, a "mount" with no arguments gives "none on /proc/bus/usb type usbfs (rw)", but the /proc/bus/usb directory still doesn't have a devices subdirectory in it, and the lsusb command gives no output. Any suggestions on where to go from here? TIA!

---

### Post by Dave54 on 2007-03-19
I'd recommend looking at:
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother)
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser)

On the first link, your printer has the following description:
> Set up needs to be done manually (parallel port, haven't tested usb), but works brilliantly with supplied ppd file included in ubuntu install. MichaelRHead - I have two of these. They both work great, though they have a smallish print area (roughly half-inch margins on each edge)

In case you want to look for additional information, this is how I got those links.
1. go to [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
2. under "Connecting and Configuring Hardware" click Printers
Both links are on that page.


Here's the drivers (debian) from the brother site if you need them
[http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/hl1440lpr-1.1.2-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/hl1440lpr-1.1.2-1.i386.deb)


> set it up as USB Printer #1, using the default driver.
I hate to ask a stupid question, but are you sure when you installed it that you selected the correct printer from the list?

---

### Post by bcrowell on 2007-03-19
Hi Dave54,

Thanks for your suggestions! 

>I hate to ask a stupid question, but are you sure when you installed it that you selected the correct printer from the list?
Pretty sure :-) I picked the model number I had, and it defaulted to installing a driver for a different model number, which I assume is supposed to be compatible.

But since you pointed me to the other link where it shows that Brother actually provides GPL'd linux drivers (!), I tried modifying the instructions at [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser) as follows:

ln -s /etc/init.d/cupsys /etc/init.d/cups
ln -s /etc/init.d/cupsys /etc/init.d/lpd
dpkg -i hl1440lpr-1.1.2-1.i386.deb
dpkg -i --force-overwrite cupswrapperHL1440-1.0.2-1.i386.deb

This seemed to happily install the driver, and the printer was listed properly under System>Administration>Printing. However, printing still didn't work. I tried this first using a parallel cable, since the page at [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersBrother) says that's what has been tested. That didn't work. One thing I noticed was that when I clicked on the printer's properties, it was listed as being on USB; I told it parallel instead, but the change in the GUI didn't seem to work -- later when I opened the GUI again, it was back to USB.

After that, I also tried hooking it up with a USB cable and using the connection via USB that the drivers default to. Still no luck.

At this point, I'm thinking this might be more of a problem with USB than with printing. I'm still not seeing any signs that USB is even working. (I'd be just as happy to use parallel, but it seems like the GUI may not be letting me do that.)

Ah, I see Brother actually tells you step by step what to do: [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html) . What they say seems to be exactly what I did above. The web interface at [http://localhost:631/printers](http://localhost:631/printers) does show the printer. It just won't print!

---

### Post by bcrowell on 2007-03-20
OK, I figured it out. In my BIOS settings, I had the USB controller disabled. Once I enabled it, everything automagically worked!

Thanks, Dave54, for your help!

---

### Post by flossgeek on 2007-03-20
bcrowell, remember breezy has now came to the end of life, so you might want to install the dapper version to ensure you get security updates.

---

