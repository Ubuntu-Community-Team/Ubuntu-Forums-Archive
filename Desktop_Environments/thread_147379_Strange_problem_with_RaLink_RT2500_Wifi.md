---
title: "Strange problem with RaLink RT2500 Wifi"
date: 2006-03-20
forum: Desktop Environments
---

### Post by rklauco on 2006-03-20
I installed RaLink RT2500 WiFi card this weekend.
Everything worked fine.
Using WIKI I managed to get the WPA-PSA encryption working and the card is working correctly.
Anyhow, I bought this card to act like home router - as an wireless AP.
But when I input this line into /etc/network/interfaces:
```
pre-up iwconfig ra0 mode Master
```
I get an error message during
```
ifup ra0
```
stating that set mode parameter unsupported.

Did anyone try to get the AP mode working?

Should I recompile the driver from it's source from rt2x00 project?

---

