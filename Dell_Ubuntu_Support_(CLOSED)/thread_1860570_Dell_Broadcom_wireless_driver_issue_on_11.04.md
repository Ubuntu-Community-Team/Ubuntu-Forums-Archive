---
title: "Dell Broadcom wireless driver issue on 11.04"
date: 2011-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DangeRoss on 2011-10-14
I'm brand new to the forum and to Ubuntu as well.  I just installed 11.04 on a Dell Inspiron E1405.  I have no access to wireless.  The wireless card I am using is as follows.  

                                  lspci -nn | grep 0280 
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
 $ lspci -nnk | grep -iA2 net 
 02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
     Subsystem: Dell Inspiron E1405 [1028:01d8] 
     Kernel driver in use: b44 
 -- 
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
     Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007] 
     Kernel driver in use: b43-pci-bridge




What should my next steps be to get this driver going?


Thanks for any and all help.

---

### Post by dFlyer on 2011-10-14
You need to hardwire yourself to the network and use additional drivers to install the correct driver, or download the driver and install it manually.

---

### Post by misterbert on 2011-11-27
Hello, I'm not sure if this is a dead thread or not, but I've followed your steps, and used a physical wire to connect to the internet, but the wire isn't being noticed either. Would you happen to have any tips on that?

---

### Post by linuxaddix on 2011-11-28
here you go:
[http://ubuntuforums.org/showthread.php?t=1876738](http://ubuntuforums.org/showthread.php?t=1876738)

---

