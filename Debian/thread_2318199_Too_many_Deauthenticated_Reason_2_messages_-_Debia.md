---
title: "Too many Deauthenticated Reason 2 messages - Debian Jessie - WiFi"
date: 2016-03-23
forum: Debian
---

### Post by jay121 on 2016-03-23
I have a embedded device running Debian Jessie Kernel 3.14.60 and have 2 WiFi chips on it:
[LIST]
[*]wlan0 - Intel 5100 with iwlwifi-5000 driver
[*]wlan1 - RealTek 8812au
[/LIST]


When both the WiFi's are connected to an AP, I am seeing a lot of `wlan0: deauthenticated from 50:17:ff:XX:XX:XX (Reason: 2)` messages. This happens on both the interfaces periodically (every 30mins). When this happens, the device often loses its network connection.


Is there anything I can do so that this doesn't happen?

---

### Post by QIII on 2016-03-23
Moved to Debian

---

