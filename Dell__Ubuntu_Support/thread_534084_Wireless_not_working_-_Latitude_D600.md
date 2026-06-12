---
title: "Wireless not working - Latitude D600"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by ruddy on 2007-08-24
I've installed Ubuntu 7.04, and everything went smoothly except for the usual wireless network problem. I am able to configure the wireless network, set the SSID and the WEP password, but it doesn't "see" my wireless access point.

I've looked for other threads, so here's more info:

Output from lspci (edited to show what's pertinent to the wireless card):

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce          One 54g] 802.11g Wireless LAN Controller (rev 02)

Output from iwconfig:

eth1      IEEE 802.11b/g  ESSID:"n"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What now?

TIA,

---

### Post by angryfirelord on 2007-08-24
Post this:
> iwlist eth1 scan

---

### Post by ruddy on 2007-08-24
Result from executing "iwlist eth1 scan":

eth1      No scan results

What do you think it is?

TIA

---

### Post by ruddy on 2007-08-25
I found the answer over in the Networking & Wireless forum:

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

THANK YOU!

---

