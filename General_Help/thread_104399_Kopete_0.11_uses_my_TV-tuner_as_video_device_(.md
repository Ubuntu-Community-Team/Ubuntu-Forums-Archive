---
title: "Kopete 0.11 uses my TV-tuner as video device :("
date: 2005-12-16
forum: General Help
---

### Post by daller on 2005-12-16
Hi There,

I'm using the new kopete 0.11 (from KDE3.5) - and it's nice!

I have one problem though!

Under "Settings -> Devices -> Device -> Device" I can choose between my tv-tuner and my webcam!

Choosing my webcam works, just until i leave the settings - Then it's back to the tv-tuner! :D

...When activating the webcam-conversation, a window with the TV-tuner is show on my machine, but not on my laptop (The one I'm talking with :)) - Is this related to the tv-tuner-issue, or an issue itself?

Here's my lsusb on my webcam:

```

Bus 001 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0870 QuickCam Express
  bcdDevice            1.00
  iManufacturer           0
  iProduct                1
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16


```

---

### Post by daller on 2005-12-16
This seems to be a bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=20421](https://bugzilla.ubuntu.com/show_bug.cgi?id=20421)

...Where is the config-file for kopete, so that I can make it use the webcam? (It important!)

---

### Post by mlomker on 2005-12-16
[QUOTE=daller]I can make it use the webcam? (It important!)[/QUOTE]

I thought most people only used webcams for being naughty.  ;)

Seriously, though, it's a beta.  I think you're expecting too much at this point.  I use the betas of amaroK and sometimes things don't work and if you wait a few days they will fix things...

---

### Post by daller on 2005-12-16
[QUOTE=mlomker]I thought most people only used webcams for being naughty.  ;)

Seriously, though, it's a beta.  I think you're expecting too much at this point.  I use the betas of amaroK and sometimes things don't work and if you wait a few days they will fix things...[/QUOTE]

Well, It's important the way, that I'm configuring a pc for my littlesister for christmas. (The use of the webcam is probably less important!)

This seems like a really small bug, so I can't see why it's not fixed... (The bug has been known for about 2 weeks, or more...)

What bugs me the most, is getting the TV-tuner working properly with tvtime: (I've given up on mythtv!)

[http://ubuntuforums.org/showthread.php?t=84972](http://ubuntuforums.org/showthread.php?t=84972)

---

### Post by DoeRayMe on 2005-12-16
Kopete does'nt save much information really, i dont like the search bit, choose toolbars and i get rid, when i restart, its back :|

---

