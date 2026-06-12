---
title: "dvb-t usb"
date: 2006-08-13
forum: Desktop Environments
---

### Post by peterthewolf on 2006-08-13
I have one of these and it works fine on XP but no joy on ubuntu 6.06

lsusb -v gives this display

Bus 004 Device 005: ID 05e1:0480 Syntek Semiconductor Co., Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x05e1 Syntek Semiconductor Co., Ltd
  idProduct          0x0480
  bcdDevice            0.05
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

I have found out from the site below:

[http://www.tradekey.com/selloffer_view/id/134112.htm](http://www.tradekey.com/selloffer_view/id/134112.htm)

Specification:
--USB2.0 Controller : Syntek’s STK1130
--2K and 8K COFDM demodulator: Philips’ TDA10046AHT
--Silicon Tuner: Philips’ TDA8275A

Any thoughts on what to do next most welcome.

---

