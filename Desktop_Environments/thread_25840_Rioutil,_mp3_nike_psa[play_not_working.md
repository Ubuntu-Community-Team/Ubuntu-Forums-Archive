---
title: "Rioutil, mp3 nike psa[play not working"
date: 2005-04-11
forum: Desktop Environments
---

### Post by leonv on 2005-04-11
Hi 

I have a Nike Rio psa[play mp3 player. As soon as I plug the device into a USB slot 'usbview' sees the devices (although it does come up as a red line, this correct) however rioutil is not able to communicate with the device.

What am I missing here?

In include some output from certain commands

lsmod | grep hcd
uhci_hcd               32800  0

dmesg | tail
usb 2-2: new full speed USB device using uhci_hcd and address 2

rioutil output:
Attempting to open Rio and retrieve song list....
Device not found.
library tried to use method: libusb

usbview output:
nike  psa[play  digital  audio  player  
Manufacturer: Diamond Multimedia
Speed: 12Mb/s (full)
USB Version:  1.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 16
Number of Configurations: 1
Vendor Id: 045a
Product Id: 5003
Revision Number:  1.00

Config Number: 1
 Number of Interfaces: 1
 Attributes: 40
 MaxPower Needed:   0mA

 Interface Number: 0
  Name: (none)
  Alternate Number: 0
  Class: 00(>ifc ) 
  Sub Class: 0
  Protocol: 0
  Number of Endpoints: 2

   Endpoint Address: 82
   Direction: in
   Attribute: 2
   Type: Bulk
   Max Packet Size: 64
   Interval: 0ms

   Endpoint Address: 02
   Direction: out
   Attribute: 2
   Type: Bulk
   Max Packet Size: 64
   Interval: 0ms

Many thanks 

Leon

---

### Post by lore on 2005-04-19
Have you tried running it as root? I had the same problem as you and the extra privileges seemed to get it up and running.

---

### Post by v-gudmk on 2005-12-18
I have the same exact problem.  sudo doesn't work either.
Rioutil works for a rio player on the same system.

---

### Post by josephmc on 2007-02-08
i've got the same problem but then again i can't even use it with windows. i think it has to do with windows media player. i'm thinking about downgrading to 10 and seeing if it still works. i use a video ipod now so i haven't used my psa in years but i want to get it working for my gf. anybody got this working?

---

### Post by josephmc on 2007-02-08
I can use it under root (sudo)

---

