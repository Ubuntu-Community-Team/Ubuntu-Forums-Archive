---
title: "Blacklisting USB devices"
date: 2006-08-27
forum: Desktop Environments
---

### Post by m68k on 2006-08-27
My PC has a built in Flash Card Reader that always shows up in Nautilus. Very annoying, I didn't use it in the three years i own this computer.

cat /proc/bus/usb/devices returns:

```

...
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0db0 ProdID=6982 Rev= 3.0a
S:  Manufacturer=MEDION
S:  Product=Medion Flash XL V3.0A
S:  SerialNumber=2003-02
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
...

```

The driver is "usb-storage", but it seems that this is the standard driver for usb mass storage devices as it also shows up for usb sticks and hard drives. Adding this module to /etc/modprobe.d/blacklist would also disable these other devices.

Is it possible to blacklist usb devices dependent on their vendor/product ids?

---

### Post by m68k on 2006-08-30
Come on, guys! Give me a tip. That can't be so hard. It took me two clicks in windows device manager to disable a specific usb device, so this has to be possible with linux.

---

