---
title: "Creative Labs Zen Micro."
date: 2005-12-27
forum: General Help
---

### Post by lasermike026 on 2005-12-27
Question:
I've installed gnomad2 and I can see the Zen in /proc/bus/usb/devices but gnomad2 can't find the device.  Anyone have a solution?

Commentary:
I've been on a quest to get an mp3 or ogg player to work on my Ubuntu Breezy workstation.  I've unsuccessfully tried an ipod nano, iriver T10, and creative labs zen micro.  This beginning to look like an issue.  Ipods and other mp3/ogg players revolutionary products.  People are not going to want to run a distro or OS that doesn't support their favorite stuff.

What kills me is this shouldn't be hard.  Music players should be as easy as usb thumb drives.  Copy the files to the device and a small app to make  playlists.

---

### Post by cbudden on 2005-12-27
I have the same problem with my Zen (nothing).
Here is the section in /proc/bus/usb/devices

T:  Bus=04 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=411d Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative Zen
S:  SerialNumber=01052551E4039097
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

---

