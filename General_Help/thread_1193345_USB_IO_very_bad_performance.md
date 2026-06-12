---
title: "USB I/O very bad performance"
date: 2009-06-21
forum: General Help
---

### Post by DrSpirograph on 2009-06-21
Hi,
I'm on Ubuntu Jaunty and reading large files from USB is absolutely killing desktop performance.

I've tried it with two different USB devices, one is formatted ext3, one is HFS+.

On the HFS+ I tried copying a 1GB file.
On the ext3 I tried scanning my music collection with a new music player.

The desktop grinds to a halt.

htop show my CPU doesn't go over 25%, yet even scrolling down in a firefox window while this I/O is going on takes 10 seconds or more to complete.

Any ideas what may be causing this?

I've googled but not really found anything.

It doesn't seem to matter if I use the GUI for the copy or if I use rsync, or cp.

Here's the lsusb for the Maxtor drive with the ext3 filesystem on it.
```
Bus 001 Device 007: ID 0d49:7310 Maxtor
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0d49 Maxtor
  idProduct          0x7310
  bcdDevice            1.25
  iManufacturer           1
  iProduct                2
  iSerial                 3
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
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
     iInterface              0
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
```

---

### Post by Mighty_Joe on 2009-06-22
The [Linux USB FAQ]("http://www.linux-usb.org/FAQ.html#i5") suggests increasing max_sectors:
> In general, increasing max_sectors will improve throughput since it means that larger amounts of data can be transferred in a single command with no need for being split up among multiple commands. Of course this is subject to diminishing returns when max_sectors is very big. More importantly, it's true only up to a point. Many devices have limits on the amount of data they can transfer, and if you try to exceed that limit you will most likely crash the device.

---

