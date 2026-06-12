---
title: "Help setting up wireless Ad-hoc Internet sharing with DWL-650+"
date: 2006-02-25
forum: Desktop Environments
---

### Post by TomaszD on 2006-02-25
I would like to share my *wired* Internet access using a *wireless* interface. The Internet would be shared with a Sony Playstation Portable.
 
After a few hours of reading I've decided to buy a PCMCIA D-Link DWL-650+, because many people reported success with it, though no-one has tried Ad-hoc AFAIR.
 
After fondling around:
```

ifconfig wlan0 192.168.0.10 netmask 255.255.255.0 up
iwconfig wlan0 rybacka rybacka36 mode ad-hoc channel 6 key off rate 22M

```
I came to this:
```

wlan0     IEEE 802.11b+  ESSID:"rybacka36"  Nickname:"acx100 v0.2.0pre8"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 42:11:44:4A:11:58
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Firestarter is also set up sanely.
Unfortunately, my PSP does not detect this network. For the record, it does detect about 3 other networks without problems (so the problem is with me, because I don't believe it's a software or hardware issue). 
 
What additional steps would I need to take in order to share my Internet access with the PSP? 
 
I don't have a router, but intending to buy one. However it disturbs me that Ad-hoc doesn't work as expected and that normal managed mode might not work as well, or maybe I won't be able to set it up correctly. I don't need security for now. Just a basic connection would suit me fine. Help?

---

