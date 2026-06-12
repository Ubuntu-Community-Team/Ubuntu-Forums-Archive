---
title: "Broadcom wireless problems in Lucid"
date: 2010-06-01
forum: Desktop Environments
---

### Post by awacs on 2010-06-01
Have a Dell laptop, with a Broadcom wireless card:
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

which doesn't work (won't associate) with b43/ssb. So, under Karmic, I blacklisted b43/ssb, and loaded ndiswrapper: 

bcmwl5 : driver installed
	device (14E4:4318 ) present (alternate driver: ssb)

which worked nicely, until I upgraded to Lucid. Now, I get wlan0, but it won't associate:

wlan0   IEEE 802.11g  ESSID: off/any  
        Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
        Bit Rate:54 Mb/s   Tx-Power:32 dBm   
        RTS thr:2347 B   Fragment thr:2346 B   
        Encryption key:<removed>               Security mode:restricted
        Power Management: off
        Link Quality:0  Signal level:0  Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any help or suggestions would be welcome.

Thanks!

---

### Post by awacs on 2010-06-01
F/up: I happened to go into the BIOS, and happened to see that the wireless was set to 'off.' So, I turned it on, and now it works, but I'm still scratching my head about a) how it turned itself off, and b) why it worked until I upgraded to Lucid. Whatever ...

---

