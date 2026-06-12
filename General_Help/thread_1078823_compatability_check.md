---
title: "compatability check?"
date: 2009-02-23
forum: General Help
---

### Post by sax_master on 2009-02-23
hey ppl, i have a HP dv6000 laptop with :
2gig RAM
AMD Turion64 mobile processor 1.9 GHz
NVIDIA GeForce 7150M / nForce 630M graphics
Broadcom 802.11b/g WLAN card

will ubuntu work with my lappy?(WiFi and all)
all help will be appreciated ;)

---

### Post by mb_webguy on 2009-02-23
You shouldn't have a problem with anything but the wireless card, which I can tell you with a fair amount of certainty *won't* work out of the box.  Broadcom sucks when it comes to Linux support.  You'll have to use the Windows wireless driver with ndiswrapper.  [Installing the driver]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") is fairly straightforward, though you may need to to some [troubleshooting]("http://ubuntuforums.org/showthread.php?t=885847") to get it working smoothly. You'll need an Ethernet cable to connect to the Internet until you get your wireless card working.

---

