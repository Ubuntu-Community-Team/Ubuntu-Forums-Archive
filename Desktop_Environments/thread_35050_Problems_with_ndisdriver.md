---
title: "Problems with ndisdriver"
date: 2005-05-17
forum: Desktop Environments
---

### Post by KriC on 2005-05-17
hi guys
i got some problems with loading ndisdriver at boot
typing dmesg on my konsole i found the error:

ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'.

i digited loadndisdriver and my computer see the driver on my kernel, but at boot it can't load the drivers

hoping someone can help me

bye


KriC

---

### Post by littlepr on 2005-05-17
Kric, 

First, did you install the driver? If yes, did you modprobe ndiswrapper to see if it  sees your driver installed? What interface are you trying to get running? Wifi or NIC card? Also make sure that the ndiswrapper is in the /etc/modules.d/ ... conf file. To do so, make sure the driver needed is installed by ndiswrapper -i /driverxxx.inf. Then modprobe ndiswrapper, and then ndiswrapper -l to see if driver is loaded. If correct driver is loaded you should get no errors. If it's for wifi your wifi enabled light should turn on on laptop (this is a laptop I hope?). Once all this is done then type ndiswrapper -m to add ndiswrapper to the /etc/modules.d/. Then reboot and see if it is now working.

I hope this all helps.

---

### Post by KriC on 2005-05-20
thank u for your tips, but my laptop suddenly crashed up :-#  :-# 
now i'm just tryin' to fix it  ](*,)  ](*,)  ](*,) 
bye

KriC

---

### Post by littlepr on 2005-05-20
Cool. I hope you get it back up and running. Then follow the steps I sugested.  If you still have issues getting ndiswrapper to detect drivers, search the forum for ndiswrapper howto.

---

### Post by maspro on 2005-05-20
[Click: Howto Ndiswrapper 1](http://www.ubuntuforums.org/showthread.php?t=31926)
[Click: Howto Ndiswrapper 2](http://www.ubuntuforums.org/showthread.php?t=25683)

Just check which one works best for you!  :)

---

### Post by phantom on 2005-05-20
[QUOTE=KriC]hi guys
i got some problems with loading ndisdriver at boot
typing dmesg on my konsole i found the error:

ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'.

i digited loadndisdriver and my computer see the driver on my kernel, but at boot it can't load the drivers

hoping someone can help me

bye


KriC[/QUOTE]
 You wouldn't be running an AMD64 cpu ?

I had some trouble also and it appears to be the NX protection codes for the AMD64 cpu's which is stopping the driver to call the hardware directly.

I had to recompile my kernel with PentiumPRO settings instead of AMD64/OPTERON to get rid of the NX codes.

This counts only for an AMD64 on a 32bit os, on the 64bit os this problem isn't showing up.

---

### Post by phantom on 2005-05-20
[QUOTE=phantom]You wouldn't be running an AMD64 cpu ?

I had some trouble also and it appears to be the NX protection codes for the AMD64 cpu's which is stopping the driver to call the hardware directly.

I had to recompile my kernel with PentiumPRO settings instead of AMD64/OPTERON to get rid of the NX codes.

This counts only for an AMD64 on a 32bit os, on the 64bit os this problem isn't showing up.[/QUOTE]
 Have a look here: [http://archives.mandrakelinux.com/cooker/2005-03/msg06918.php](http://archives.mandrakelinux.com/cooker/2005-03/msg06918.php)

---

### Post by maspro on 2005-05-20
[QUOTE=phantom]You wouldn't be running an AMD64 cpu ?

I had some trouble also and it appears to be the NX protection codes for the AMD64 cpu's which is stopping the driver to call the hardware directly.

I had to recompile my kernel with PentiumPRO settings instead of AMD64/OPTERON to get rid of the NX codes.

This counts only for an AMD64 on a 32bit os, on the 64bit os this problem isn't showing up.[/QUOTE]
I'm have a AMD64 in my Acer laptop and are running Ubuntu v5.04 32-bit and I have absolutely no problems getting ndiswrapper to works correctly. It installs good, it loads correctly and it's auto-loaded during boot-up without any problems.

---

### Post by phantom on 2005-05-20
Well, that is promising for me tommorow.

On my actual install (MDV2005LE) I had nothing but trouble getting it to work.

BTW: I have an Acer Ferrari 3200 AMD64 ;)

---

### Post by maspro on 2005-05-20
[QUOTE=phantom]
BTW: I have an Acer Ferrari 3200 AMD64 ;)[/QUOTE]
I have the same laptop, so you're going to be OKE!  :grin:

This guide should work for you: [ Click for Wifi guide](http://www.ubuntuforums.org/showthread.php?t=31926)

---

