---
title: "Xbox 360 Controller not working in 13.10"
date: 2014-02-08
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2014-02-08
Very weird. I just installed Xubuntu 13.10 on this new haswell rig i just built and games like You Still Won't Make it and Intrusion 2 my afterglow xbox 360 wired usb controller doesn't work. It worked fine in Xubuntu 12.04.3. It works in most steam games and I set it up within big picture mode. I know for a fact it works with those 2 games using the default xpad driver in Xubuntu 12.04.3 so there should be no reason I should have to install xboxdrv or whatever that userspace controller driver is named. It should work with xpad just as it did with Xubuntu 12.04.3. Any suggestions on where to begin to troubleshoot?

lsusb -v
```

Bus 003 Device 004: ID 0e6f:0213 Logic3 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x0e6f Logic3
  idProduct          0x0213 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          153
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  11 21 10 01 01 25 81 14 03 03 03 04 13 02 08 03 03
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      3 
      iInterface              0 
      ** UNRECOGNIZED:  1b 21 10 01 01 01 83 40 01 04 20 16 85 00 00 00 00 00 00 16 05 00 00 00 00 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              64
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 01 22 86 07 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    253 
      bInterfaceProtocol     19 
      iInterface              4 
      ** UNRECOGNIZED:  06 41 00 01 01 03

```

ls -la /dev/input/by-id/
```

drwxr-xr-x 2 root root 140 Feb  6 19:17 .
drwxr-xr-x 4 root root 560 Feb  6 19:17 ..
lrwxrwxrwx 1 root root  10 Feb  6 19:17 usb-046d_081a_13339CA0-event-if00 -> ../event20
lrwxrwxrwx 1 root root   9 Feb  6 19:17 usb-Logitech_USB_Optical_Mouse-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 Feb  6 19:17 usb-Logitech_USB_Optical_Mouse-mouse -> ../mouse0
lrwxrwxrwx 1 root root   9 Feb  6 19:17 usb-Performance_Designed_Products_Afterglow_Gamepad_for_Xbox_360_05F79686-event-joystick -> ../event3
lrwxrwxrwx 1 root root   6 Feb  6 19:17 usb-Performance_Designed_Products_Afterglow_Gamepad_for_Xbox_360_05F79686-joystick -> ../js0

```

---

