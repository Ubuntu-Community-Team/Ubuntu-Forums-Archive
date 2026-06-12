---
title: "ndiswrapper"
date: 2006-07-26
forum: Desktop Environments
---

### Post by jimmymac on 2006-07-26
Hi guys,

Having set up ndiswrapper on my old 5.10 system with no problems I figured it wouldn't be a problem if I formatted my hdd and installed 6.06.....

However it don't seem to work!
iwconfig reveals:

jimmy@jamelinux:/etc/apt$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"galaxy"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

which would seem to imply that there is a fault with my access point.  I haven't changed anything on the router, and have set up ndiswrapper exactly the same as last time.  So I'm a bit confused now!!

Any ideas?

TIA

Jimmy

---

