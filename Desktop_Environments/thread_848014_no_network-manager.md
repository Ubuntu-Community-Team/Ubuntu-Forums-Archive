---
title: "no network-manager"
date: 2008-07-03
forum: Desktop Environments
---

### Post by mathfeel on 2008-07-03
I just installed ubuntu Hardy on an Dell Inspiron 700m (the wireless device is ipw2200). And to my surprise (I installed Ubuntu on a few computers the same day, and all of them have it), I cannot find the icon for Network-Manager on the task bar where I can select the wireless network I want to connect to. Instead I only get an icon that when I click it says "Manual Configuration...".

I can connect to the encrypted network no problem with Manual Configuration (same as in Administrator->Network), but it is very annoying to use when I carry the laptop around.

Is is possible that this is due to the wireless interface being identified as eth1 (ethernet) instead of ath0 or wlan0? Out of curiosity, how does one set these anyway? They seem to differ from distro. to distro.

Thanks.

---

### Post by CheeseEatingBulldog on 2008-07-03
Sounds like your wireless card isn't being recognised, try using ndiswrapper and the windows driver for your card, that should get you the network manager. I have a toshiba satellite and had the same issue, but after installing the driver with ndiswrapper I get the option to browse wireless networks and such.

---

### Post by mathfeel on 2008-07-03
I can connect to wireless network no problem with MANUAL configuration. Besides why use ndiswrapper with some binary blob when the open source ipw2200 driver is available and (mostly) working?

---

