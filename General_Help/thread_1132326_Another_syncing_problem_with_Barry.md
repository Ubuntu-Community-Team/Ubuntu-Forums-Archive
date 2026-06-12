---
title: "Another syncing problem with Barry"
date: 2009-04-21
forum: General Help
---

### Post by lagisforeplay on 2009-04-21
This may seem like another barry problem but I believe I have looked every where and I am still stuck. Also if this is not in the correct section, mods please fell free to move this. Here is the situation and I just want to say thank you: 
phone: 8330 (verizon)
OS: Ubuntu Intrepid 8.10 I believe

When I plug in my BB and I select the "yes I want to turn on mass media..."
 I get a pop up of "select how to open 512M" and it thinks I have inserted a digital audo player.  If I select NO, no pop occurs, any way I installed berry and the required opensync evolution plugins and dependencies (or so I hope to believe). And when I try to run berrybackup with BB connected via USB it cannot find any blackberry devices.
when I "lsusb" I get the RIM device
```
jerrod@jerrod-laptop:~$ lsusb
Bus 003 Device 009: ID 0fca:8004 Research In Motion, Ltd. 
Bus 003 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 0424:2514 Standard Microsystems Corp. 
Bus 003 Device 002: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```and lsusb -v

```
Bus 003 Device 006: ID 0fca:8004 Research In Motion, Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0fca Research In Motion, Ltd.
  idProduct          0x8004 
  bcdDevice            2.01
  iManufacturer           1 Research In Motion
  iProduct                5 RIM Composite Device
  iSerial                 3 xxxxxxxxxxxxxxx
  bNumConfigurations      1
```And btool -l and btool -B -N
```
 jerrod@jerrod-laptop:~$ btool -B 3 -N 9
Blackberry devices found:
No device selected
jerrod@jerrod-laptop:~$ btool -l
Blackberry devices found:
jerrod@jerrod-laptop:~$ 

```Forgot to add that I know the device ID is different from my two codes and that the phone charges when connected via USB

What am I doing wrong? I am grateful for any help thank you in advance!

---

### Post by lagisforeplay on 2009-04-22
bump, please help

---

### Post by lagisforeplay on 2009-04-24
bump

---

### Post by pvicc on 2009-08-12
As for as I know, When you turn on Mass storage media Btool will not work. Try plugin again and select No to turn on Mass storage media. I think now btool will recognize and respond

---

### Post by billdotson on 2009-08-17
bump

---

