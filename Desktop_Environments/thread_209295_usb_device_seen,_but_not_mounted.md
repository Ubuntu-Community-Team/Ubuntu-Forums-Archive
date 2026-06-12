---
title: "usb device seen, but not mounted"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Stephen-I-M on 2006-07-04
I have a usb music player (iRiver iGP-100) that is in /proc/bus/usb/devices under the entry:

T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1006 ProdID=2001 Rev= 1.00
S:  Manufacturer=iRiver
S:  Product=iRiver iGP-100 Series
S:  SerialNumber=000006BACD0C
C:* #Ifs= 1 Cfg#= 2 Atr=c0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

Normally this should get mounted under /dev/sdc1, but there is no /dev/sdc* created. How can I mount this device?

Thanks.

Stephen

---

### Post by alexc_m2k on 2006-07-05
Add your account into the "plugdev" group.

Pls refer to this [http://www.ubuntuforums.org/showthread.php?t=199282]("http://www.ubuntuforums.org/showthread.php?t=199282")

---

