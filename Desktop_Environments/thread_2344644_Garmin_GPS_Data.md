---
title: "Garmin GPS Data"
date: 2016-11-27
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-11-27
Folks,

I have an older Garmin Forerunner 305 - USB connection only.

Trying to get this to extract data on Ubuntu 16:04 and am having difficulty.

lsusb shows ```
Bus 003 Device 003: ID 091e:0003 Garmin International GPS (various models)
```

lsusb -D /dev/bus/usb/003/003 gives the following output;

```
Device: ID 091e:0003 Garmin International GPS (various models)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x091e Garmin International
  idProduct          0x0003 GPS (various models)
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
Device Status:     0x0001
  Self Powered


```

I've installed garmin-forerunner-tools but can find very little information how to use it, seems there are just two commands;

garmin_dump and garmin_save_runs, the former just returns me to the command line with no information, the latter gives the following output;

```
geoff@satellite:~$ sudo garmin_save_runs 
Segmentation fault (core dumped)


```

Checked directories for some kind of output but cannot find anything.

Installed Garmin Communicator - Fake  plugin. Version 0.3.27 and it shows in Firefox as enabled but following instructions it does not show my device to be able to upload any data.

I get the impression my device should show as a 'mass storage' device but it isn't.

Can anyone throw any light on this?

Geoff

---

### Post by meijer.o on 2016-11-30
Dear Geoff_Lane,

With the use of Gebbabel, you should be able to extract gpx data from your device. Perhaps root privileges are needed. You can install it with "sudo apt-get install gebabbel"

Best regards,

O. Meijer

---

### Post by Geoff_Lane on 2016-11-30
> **meijer.o said:**
> Dear Geoff_Lane,

With the use of Gebbabel, you should be able to extract gpx data from your device. Perhaps root privileges are needed. You can install it with "sudo apt-get install gebabbel"

Best regards,

O. Meijer

Thanks for suggestion, that downloaded a gpx file, now I need to figure out how to make that usable.

Geffers

---

### Post by meijer.o on 2016-11-30
You can open it with google earth, or in a website like gpsies.com.

Best regards,

Otto

---

### Post by TheFu on 2017-01-22
There are lots of tools for gpx data on Linux.
* **gpsBabel** - convert from/to almost any formats you need/have
* **gpsPhoto** - geotag photos using timestamp matching between gpx tracks and photo timestamps; 
* **Viking** - visualize your tracks without using privacy sucking "cloud" services.  I like to show my hiking tracks as the first photos in an epic hike album. An overview of the day.

Google Maps used to display KML data from 3rd party URLs (like my personal GPX server), but that support ended sometime. This forced me to discover viking.

---

### Post by Geoff_Lane on 2017-01-22
Thank you meijer.o

Geffers

---

### Post by Geoff_Lane on 2017-01-22
Cheers TheFu

Geffers

---

