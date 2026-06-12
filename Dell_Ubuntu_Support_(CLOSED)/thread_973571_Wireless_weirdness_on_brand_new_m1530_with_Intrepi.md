---
title: "Wireless weirdness on brand new m1530 with Intrepid"
date: 2008-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by c0bra on 2008-11-06
Okay this is my first attempt at any linux distro (much less Ubuntu) as a desktop OS, so please bear with me.

The laptop is currently using the broadcom STA driver. I *can* get it working but it requires monkeying around with iwconfig:

I can associate with an essid after boot, when the interface (eth1) is in Ad-Hoc mode. After associating I can sometimes switch the mode to managed, sometimes not. I haven't quite figured out a pattern there. The *main* thing I have discovered is that it takes doing

```
iwconfig eth1 essid off
```

In order to get the interface properly associated with the AP so that I can get an ip.

Any idea why this would be happening? "essid off" doesn't actually turn off the essid, it mostly gets it into managed mode on that essid. This being the case I cannot get any of the automated desktop utils to connect to wifi, which is a pain.

---

