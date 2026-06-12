---
title: "Cannot write from HDD to USB after restore ?"
date: 2017-08-19
forum: Desktop Environments
---

### Post by oygle on 2017-08-19
Desktop computer (Kubuntu 16.04.1)- all files were backed up onto an external drive
Laptop computer (Kubuntu 16.04.1) - all files restored from the external drive to the HDD

Then all paths on the Laptop were chowned as follows ..

```

sudo chown -R username:username /home/username/Downloads/

```

and I can access the files okay, view,etc. However, when I try to copy the files to a USB, the copy fails with a 'cannot write' message.

The username and group name are the same, and I even made sure the files were 644. Is it UUID or something ? I was able to copy to this USB from the Desktop; have been for months, but try and copy any 'restored files' and it fails. If I try and copy from files that were previously on the laptop (e.g. like _before_ the restore), the copy is okay.

```

ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Aug 20 10:22 9B7D-F8D4 -> ../../sdc1

```

Here is the mount command for the USB

```

/dev/sdc1 on /media/username/STORE N GO type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

---

### Post by oygle on 2017-08-19
Have also seen CPU load up to 100% on 2 of the 4 processors when copying to the USB, using a different port. The graphs  on System Monitor show extremely high CPU ??

Can I check anything in the logs ?

**edit** - Later - the copy actually worked on another usb port. I was trying to use a USB that was 2.0 specifications in a USB 3.0 port.

---

### Post by oygle on 2017-08-20
Finally found out that the problem was trying to use a USB device that was 2.0 specifications in a USB 3.0 port.  Most USB's have it inscribed on the usb case, but this one didn't. Here is how to find out whether the USB device (i.e not the port on your computer) is 2.0 or 3.0

Place the USB in the usb port ..

```

$ **lsusb**
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0c45:670b Microdia 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 008: ID 18a5:0243 Verbatim, Ltd 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The usb device in this example is "Verbatim, Ltd", and the bus and device number is Bus 001 Device 008

Next, use the bus/device number as follows

```

$ **lsusb -D /dev/bus/usb/001/008**

Device: ID 18a5:0243 Verbatim, Ltd 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x18a5 Verbatim, Ltd
  idProduct          0x0243 
  bcdDevice            1.10
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
    bmAttributes         0x80                                                                                                                                                                   
      (Bus Powered)                                                                                                                                                                             
    MaxPower              498mA                                                                                                                                                                 
    Interface Descriptor:                                                                                                                                                                       
      bLength                 9                                                                                                                                                                 
      bDescriptorType         4                                                                                                                                                                 
      bInterfaceNumber        0                                                                                                                                                                 
      bAlternateSetting       0                                                                                                                                                                 
      bNumEndpoints           2                                                                                                                                                                 
      bInterfaceClass         8 Mass Storage                                                                                                                                                    
      bInterfaceSubClass      6 SCSI                                                                                                                                                            
      bInterfaceProtocol     80 Bulk-Only                                                                                                                                                       
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

Look for the **bcdUSB** - in this example it is 2.10

---

