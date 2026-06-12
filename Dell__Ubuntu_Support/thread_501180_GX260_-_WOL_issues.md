---
title: "GX260 - WOL issues"
date: 2007-07-14
forum: Dell  Ubuntu Support
---

### Post by castor troy on 2007-07-14
Hi All, I have an Optiplex GX260 with Ubuntu Server 6.06LTS installed. I cannot get WOL to work through the onboard nic (or any nic). I have followed the guide on [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588) but the system still does not seem to wake.
Details below;
Bios - Updated to A09 Settings - Low Power mode set to Disable, WOL set to ON
ethtool eth0 shows;
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Full Port:
Twisted Pair PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: umbg
Wake-on: g
Current message level: 0x00000007 (7)
Link detected: yes

I have tried 5 different WOL programs, but nothing seems to work. When the system is shut down through halt script, orange light on nic stays on, and switch shows connectivity. I would really appreciate any suggestions or help.

Cheers, Ben

---

