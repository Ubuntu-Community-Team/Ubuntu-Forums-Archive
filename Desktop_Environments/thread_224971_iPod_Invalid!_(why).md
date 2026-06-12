---
title: "iPod Invalid! (why?)"
date: 2006-07-28
forum: Desktop Environments
---

### Post by gmatt on 2006-07-28
I have two ipods nano and one is a 1gb the other is a 4gb. The 1gb is recognized as a "proper" ipod under linux while the 4gb one gets the message:


** Message: Device Added: /org/freedesktop/Hal/devices/volume_uuid_4DEE_8700
glibtop: This machine has 1 CPUs, 1 are being monitored.
  Not a Valid iPod! Try Rebooting the iPod

while the working one gets a spit out of :

** Message: Device Added: /org/freedesktop/Hal/devices/volume_uuid_39A4_3D1APath Info
   Device Path:      /dev/sdb2
   Mount Point:      /media/ipod
   Control Path:     /media/ipod/iPod_Control/
   HAL ID:           /org/freedesktop/Hal/devices/volume_uuid_39A4_3D1ADevice Info
   Model Number:     MA352
   Device Model:     Unknown
   iPod Generation:  Unknown
   Adv. Capacity:    0 MB
   Is New:           YES
   Writeable:        YES
   Serial Number:    5U6176UZUPR
   Firmware Version: 5.1.1
Volume Info
   Volume Size:      937681920
   Volume Used:      715146240
   Available         222535680
   UUID:             39A4-3D1A
   Label             IPOD
User-Provided Info
   Device Name:      (null)
   User Name:        (null)
   Host Name:        (null)


So now I am wondering why that is so. It seems contradictory for one ipod to work while the other one doesn't. 

Here is the print out for the 4gb  cat /proc/bus/usb/devices


T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 23 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  2
P:  Vendor=05ac ProdID=120a Rev= 0.02
S:  Manufacturer=Apple
S:  Product=iPod
S:  SerialNumber=000A270018517A4A
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
C:  #Ifs= 3 Cfg#= 2 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=
E:  Ad=81(I) Atr=01(Isoc) MxPS= 192 Ivl=1ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=
E:  Ad=82(I) Atr=03(Int.) MxPS=  64 Ivl=125us

Here is the print out for the 1gb ipod:

T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 24 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  2
P:  Vendor=05ac ProdID=120a Rev= 0.01
S:  Manufacturer=Apple
S:  Product=iPod
S:  SerialNumber=000A2700181A9CC8
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
C:  #Ifs= 1 Cfg#= 2 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=
E:  Ad=82(I) Atr=03(Int.) MxPS=  64 Ivl=125us

I am no expert but there seems to be a big difference between the two just when you look at the size.

I was wondering if anybody had any ideas or previous experience on how to fix this. I can still sync the 4gb iPod just like the 1gb iPod under gtkPod but I can't get it to sync in Banshee because its incorrectly not detected.  Also I tried restoring/updating the 4gb iPod to the latest firmware. Mmmm might be that I need to downgrade its firmware?

---

### Post by gmatt on 2006-07-28
Problem solved. I had to downgrade the firmware on my ipod from 1.2 to 1.1 or any firmware release before June 2006. I do not know why but iPod stuff is proprietory so I don't think many people know.

---

