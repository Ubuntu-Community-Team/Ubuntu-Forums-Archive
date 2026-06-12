---
title: "Cups not printing, no errors shown"
date: 2008-12-16
forum: General Help
---

### Post by blink0 on 2008-12-16
Hello all!
I just can't understand what's wrong here... I send test pages to print, I print with lp, I print from a network pc, all looks successful on the web interface of cups, the job stays some seconds on Processing, then it is shown as done. There are no errors on error_log (also with level debug), no problem at all... But nothing comes out of the printer!
The printer is an HP 1018 connected by USB to the pc (which then shares it via cups to some network pc's).
I have tried restarting cups, restart the whole pc, re-connecting the usb cable, turning off/on the printer itself... Nothing solves it!
Here goes the hopefully useful information:

Ubuntu 8.10 Intrepid

lsusb:

Bus 005 Device 002: ID 03f0:4117 Hewlett-Packard Printing Support
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x4117 Printing Support
  bcdDevice            1.00
  iManufacturer           1 Hewlett-Packard
  iProduct                2 HP LaserJet 1018
  iSerial                 3 KP35WTX
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

lpinfo -v:
(...)
direct hp:/usb/HP_LaserJet_1018?serial=KP35WTX

error_log (cleaned it before printing a test page):
[http://code.bulix.org/0hdhvf-69261](http://code.bulix.org/0hdhvf-69261)

cupsd.conf:
[http://code.bulix.org/f6ir1p-69262](http://code.bulix.org/f6ir1p-69262)

If anyone could give me some insight, I would gladly appreciate it, since I don't know what to do, and people need this printer working!

Thanks in advance,
Daniel

---

### Post by marpola on 2008-12-16
This question comes up periodically. Search ¨Laserjet 1018¨ and you will get the other threads. The HP driver does not work in linux.

I sent the steps needed to install a driver that works, 3 days ago.

No one has yet answered. 

Let me know what happens. I would like to help someone.

Marty

---

