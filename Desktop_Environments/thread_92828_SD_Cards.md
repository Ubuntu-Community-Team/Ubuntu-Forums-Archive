---
title: "SD Cards"
date: 2005-11-20
forum: Desktop Environments
---

### Post by vav on 2005-11-20
I have a Dell Inspiron 9300 running breezy. It has a built in SD card reader and firewire port, both from ricoh co. The SD card reader at least works in WinXP, but not in Linux. I dont know about firewire but I dont believe ricoh has linux drivers ?

Thanks,
--Vav

---

### Post by Ampersand on 2005-11-20
Try running
```
dmesg | tail
```
in a terminal a few seconds after inserting an SD card, this should give you an indication as to whether it's working, and if so what the device name is.

Also, try looking in the hardware manager (in system - administration, I think. Not in Gnome at the moment). This should show whether it's been detected.

If you find the device location (starts with /dev/), you can use the mount command:

```

sudo mkdir /media/sd
sudo mount -t vfat /dev/sda1 /media/sd
```

(replace /dev/sda1 with whatever the device location is if it's different).

---

### Post by vav on 2005-11-30
I checked dmesg and it doesnt show the sd card. neither does device manager in gnome.

--Vav

---

### Post by anil_robo on 2005-12-21
I'm using Dell Inspiron 6000 and I face the same problem. SD card not detected at all! :(

---

### Post by rado_london on 2005-12-22
I think that there is no kernel modules for card readers. I have 6 in 1 card reader on my HP Pavilion dv4145ea but it is dead under linux.

---

### Post by anil_robo on 2005-12-22
[quote=rado_london]I think that there is no kernel modules for card readers. I have 6 in 1 card reader on my HP Pavilion dv4145ea but it is dead under linux.[/quote]
Yes, SD card (and indeed any other device) could work only when the kernel supports it. Sometimes one has to recompile the kernel for some devices, like I did for my Logitech Quickcam for Notebooks. That's why new kernel releases are important - they provide essential support for new hardware!
Also see [this.]("http://www.ubuntuforums.org/showthread.php?t=84114")

---

### Post by anil_robo on 2005-12-23
OKay, it's official now. I called up the manufacturers of both my laptop (Dell) and SD memory card (Sandisk). Both said the same thing:
**"We're sorry, we don't support Linux"!**

---

### Post by Michael Steinberg on 2005-12-23
There should be nothing inherently unreadable about SD cards--they follow the USB mass storage device protocol. And reader citcuitry isn't that problematic. Perhaps it's the interface/bus that the internal card reader is connnected to? I have no problem with an external 6-in-1 USB card reader and an SD card with a Dell Inspiron 1150 -- the Sandisk  card shows up with a nifty SD-card-shaped icon, too. And my EZ-Buddie PC, which has a built-in card reader, also has no problem reading & displaying SD cards (no custom icon, alas). So some internal readers "just work"

Michael Steinberg

---

### Post by Fred v. J. on 2006-01-04
My Laptop has an internal SD card reader, too. But I had no chance to get it working on Breezy.

The solution for me was:

Spending less then 10 Euros at my local hardware dealer getting the hama usb 2.0 card reader:

[IMG]http://picnic.ciao.com/de/4840322.jpg[/IMG]


The rest was something for "idiots" ;)

- Plugging in the reader
- Waiting for a few seconds
- Inserting the SD Card into the reader
- Access!

End of the thrill. ;)

---

### Post by rado_london on 2006-01-16
This gadget is really nice. But still it is quite silly to have built in 6 in 1 card reader and not having the chanse to use it.

I have a question. Is there a Card reader support in the upcomming Dapper?

Thanks in advance!

---

### Post by tombeharrell on 2006-02-10
It's working!!
Inspiron 6000 internal SD/MMC card reader.

For the first time I noticed a new icon beside my DVDRW in the toolbar, and it provided access to an MMC card I'd left in there, waiting for the day it appeared.

I think it must be the latest kernel in Dapper I installed yesterday, it's 2.6.15-15-686.

Tom.\\:D/

---

### Post by anil_robo on 2006-03-12
My 512MB SD card from Sandisk never worked in Breezy. I upgraded to Dapper recently, and I'm glad that the SD card works out-of-the-box in Dapper! It gets mounted automatically when I insert it, and an icon appears on the desktop!

What else could one wish for? :mrgreen:

---

