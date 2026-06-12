---
title: "Unable to connect to internet"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Footix on 2006-10-01
I managed to get Dapper installed today, but I can't get it to connect to tbe internet, or even recognize my router. I'm running an Acer Aspire 3000, and a Speedstream 6520 wireless router, with WEP.

---

### Post by drpaul on 2006-10-02
You might get help if you said what you did to try and connect.

Paul

---

### Post by Footix on 2006-10-04
What I tried doing was activating eth1 and typing
```
iwconfig eth1 essid (my network's SSID) key (my WEP key)
```
It goes through only if I put sudo before it, but nothing happens. I've tried pressing the switch for my wireless card (in case it was off), but it still doesn't do anything. The computer doesn't even notice it's connected. I *know* my router is set to broadcast its SSID, and I've got no clue what else to try. Anybody have any ideas?

---

### Post by NetworkGuy on 2006-10-04
List the output from the following commands and we'll see what's up on your PC.

If your wireless card is pci or pcmcia
```
lspci
```

If your wireless card is usb
```
lsusb
```

Regardless which type it is
```
iwconfig
```
```
ifconfig
```

---

### Post by Footix on 2006-10-04
**lspci**
```
(snip)
0000:00:0b.0 Network controller: Broadcom Corporation
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
(snip)
```

**iwconfig**
```
lo no wireless extensions
eth0 no wireless extensions
eth1 IEEE 802.11 b/g ESSID:(my SSID) Nickname:"4318" 
   Mode:Managed Access Point:Invalid Bit Rate=1 Mb/s
   RTS thr:off Fragment thr:off
   Link Quality:0 Signal level:0 Noise level:0
   Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
   Tx excessive retries:0 Invalid misc:0 Missed beacon:0
sit0 no wireless extensions
```

**ifconfig**
```
lo  Link encap:local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:25 errors:0 dropped:0 overruns:0 frame:0
    TX packers:25 errors:0 dropeed:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes: 1656 (1.6 KiB) TX bytes: 1656 (1.6 KiB)
```

---

### Post by calvinthomas on 2006-10-05
Search for the guide on broadcom 4318 on these forums and it'll fix your problem!

Calv

---

