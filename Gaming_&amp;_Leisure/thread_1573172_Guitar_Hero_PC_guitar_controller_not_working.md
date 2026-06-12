---
title: "Guitar Hero PC guitar controller not working"
date: 2010-09-12
forum: Gaming &amp; Leisure
---

### Post by fgomes on 2010-09-12
Hello

I'm trying to use a Guitar Hero Guitar controller that I have bundled with a Guitar Hero Game for PC and it isn't working. Here is what I have in dmesg:

[592549.720896] usb 1-5.3: new full speed USB device using ehci_hcd and address 21
[592549.815833] usb 1-5.3: configuration #1 chosen from 1 choice
[592549.820603] input: Berway Technology Ltd. as /devices/pci0000:00/0000:00:04.1/usb1/1-5/1-5.3/1-5.3:1.0/input/input8
[592549.821324] generic-usb 0003:1430:474C.0005: input,hidraw2: USB HID v1.10 Gamepad [Berway Technology Ltd.] on usb-0000:00:04.1-5.3/input0
[592549.892887] usb 1-5.4: new full speed USB device using ehci_hcd and address 22
[592549.964865] usb 1-5.4: device descriptor read/64, error -32
[592550.140845] usb 1-5.4: device descriptor read/64, error -32
[592550.316824] usb 1-5.4: new full speed USB device using ehci_hcd and address 23
[592550.388817] usb 1-5.4: device descriptor read/64, error -32
[592550.564789] usb 1-5.4: device descriptor read/64, error -32
[592550.740770] usb 1-5.4: new full speed USB device using ehci_hcd and address 24
[592551.148527] usb 1-5.4: device not accepting address 24, error -32
[592551.220715] usb 1-5.4: new full speed USB device using ehci_hcd and address 25
[592551.628027] usb 1-5.4: device not accepting address 25, error -32
[592551.628174] hub 1-5:1.0: unable to enumerate USB device on port 4

The lsusb -v for this controller gives the following result:

Bus 001 Device 021: ID 1430:474c RedOctane
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x1430 RedOctane
  idProduct          0x474c
  bcdDevice            1.08
  iManufacturer           1 Berway Technology Ltd.
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     137
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

I'm running Ubuntu 10.04 on a NVIDIA ION motherboard with a Atom N270 CPU, the kernel is the following:

Linux home-server 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Any tips on how to solve this problem? I tried on different ports, on a hub, and the result is the same.

Thanks in advance

Fernando

---

