---
title: "ACM help/Moto4lin"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Glass_Onion on 2006-06-18
I'm having trouble setting up an ACM device for my moto4lin installation since it doesn't seem to make one itself. I've tried to follow the instructions [here](http://moto4lin.sourceforge.net/wiki/System_Configuration) on the moto4lin wiki but with no luck. It just says to plonk the following into a rules file without actually specifying one; 

```
KERNEL=="ttyACM[0-9]*"			NAME="ttyACM%n", GROUP="usb", MODE="0660"
```

First I tried it in 40-permissions.rules but with no luck. I then tried it in a couple of others deleting it if it didn't work. Can anybody who's installed this program and got it working give me any help with it? My mobile's a Motorola SLVR L7 which acording to the Wiki works without any issues.

Sorry if their's a lack of any real information for anybody. I'm using the plain Dapper i386 processor build of Ubuntu.

---

### Post by Glass_Onion on 2006-06-19
*bump*

---

### Post by rasgward on 2006-08-29
Hey Y'all,
 Moto4lin looks great, but I don't think it supports my phone motorola v323. I have searched and haven't seen it listed. Anyway, if anyone has any thoughts...here is the output of the device file under proc/bus/usb/devices

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 20 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(comm.) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=22b8 ProdID=2a22 Rev= 0.01
S:  Manufacturer=Motorola, Inc.
S:  Product=Motorola A41x/V32x
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=32ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=8a(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=0b(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

Thanks. -Greg

---

### Post by patmalcolm91 on 2007-08-09
i also have a motorola v323, and can't get it to work, from the wiki, it seems that it isn't yet compatible, does anyone have ANY way that i could connect to this phone free (and preferrably w/ linux, not windows). MPT costs money, so that's out. anyone?!?!?

---

