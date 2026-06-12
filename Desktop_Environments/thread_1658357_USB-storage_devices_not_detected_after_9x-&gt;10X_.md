---
title: "USB-storage devices not detected after 9x-&gt;10X upgrade"
date: 2011-01-02
forum: Desktop Environments
---

### Post by =X= on 2011-01-02
Hello everyone first post here.  I've search the forums and cannot find a similar situation here but I'm hopping somebody can help.

My USB devices are being detected when I run the 'lsusb' command.  However there is no driver that is set to the device

Below is what shows up.

> /:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 4: Dev 17, If 0, Class=stor., **Driver=,** 480M
    |__ Port 4: Dev 17, If 1, Class=vend., Driver=, 480M
There is also no device (sbX, or mmsdXXX) created for them.

USB devices is wokring on my PC, I do have two USB devices that are not mass storage that work.  One is a mouse the other is a WIFI device.  For the WIFI I did have to install the Window Wireless network drivers.


As an aside:

I've also upgraded my laptop from 7x->10x and the device works there just fine.  This is what lsusb sees on the laptop.

> /:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 4: Dev 17, If 0, Class=stor., **Driver=usb-storage,** 480M
    |__ Port 4: Dev 17, If 1, Class=vend., Driver=, 480M
Also the /dev/sdX device is created so there is a mount point

Thank you in advance.
 =X=

---

### Post by =X= on 2011-01-06
[BUMP] Does anybody have any ideay how to get the USB-Storage device to work?

Thanks in advance.
=X=

---

