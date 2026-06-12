---
title: "trying to get linux wifi drivers to work"
date: 2006-02-13
forum: Desktop Environments
---

### Post by corosus on 2006-02-13
hi

i own a usb wifi stick based on the AR 5523  chipset (the device itself is a edimax EW-7315Ug)
it always worked fine under windows but i'm trying to make the switch , and it came with linux drivers in rpm format. 

how can i get these drivers to work under kubuntu???



thanks

---

### Post by FlakJacket on 2006-02-13
you can try using alien.

```
alien -iv **filename**
```

alien usually works but sometimes has dependency issues.

Flak

---

### Post by corosus on 2006-02-14
[QUOTE=FlakJacket]you can try using alien.

```
alien -iv **filename**
```

alien usually works but sometimes has dependency issues.

Flak[/QUOTE]


i did that but the deb file i get does not seem to work (well it installs but there is no result)

is there anny way to fix these dependancys???

---

### Post by FlakJacket on 2006-02-17
What do you mean there is no result?

Flak

---

### Post by alangp00 on 2006-02-18
I installed the rpm in FC3. Here are the files in the package (AtherosLinuxUsb2.6):
/lib/modules/2.6.9-1.667/kernel/drivers/usb/athusbfw.ko
/lib/modules/2.6.9-1.667/kernel/drivers/usb/athusbwlan.ko
/usr/local/bin/wpa_cli
/usr/local/bin/wpa_passphrase
/usr/local/bin/wpa_supplicant

I guess the first two are drivers but I can not make it run either (my plan is to install the
driver under FC first and then migrate it to Ubuntu). No readme file avaiable. No ideas how to play with those five files.
the package infomation by runing   rpm -ql AtherosLinuxUsb2.6
Name        : AtherosLinuxUsb2.6           Relocations: (not relocatable)
Version     : 1.3                               Vendor: (none)
Release     : 4                             Build Date: Sun 13 Feb 2005 12:11:50 PM CST
Install Date: Fri 17 Feb 2006 10:51:14 PM CST      Build Host: ip93-0.atheros.com
Group       : System Enviroment/Base        Source RPM: AtherosLinuxUsb2.6-1.3-4.src.rpm
Size        : 5839454                          License: GPL
Signature   : (none)
Summary     : Atheros Wlan Usb Driver

By the way, my usb adapter is Airnet AWU108 and based on the same atheros super g chipset. But only Edimax privides linux dirver (although not working yet in my case).
Maybe we can ask help from Edimax or Atheros on how to install the linux driver for the usb adapter. As far as I know, Madwifi do not support usb adapter yet.

---

