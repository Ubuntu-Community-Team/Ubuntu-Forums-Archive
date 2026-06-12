---
title: "Dell 2110 WiFi unstable in 10.10"
date: 2010-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bdhook on 2010-11-28
The wifi card in the Dell 2110 n-Series netbook did not work right with an initial install of Ubuntu 10.10. The proprietary drivers had been installed, and as of a week ago a fully up-to-date system was still suffering from unusable WiFi. I could get FAR better performance over a Bluetooth DUN connection via my Cell Phone, and that is what I used to do yet another update. I just wanted to let folks know that this issue seems to be fixed with a fully updated 10.10 install as of today, with the proprietary drivers enabled.

The symptoms before the update were extremely long times to associate with a WiFi network, and then about a 95% packet loss rate after connection. Only on a few rare occassions was it even possible to load Google's home page, let alone anything with heavy content.

Right now, I can get the following performance:

$ sudo ping -i 0 -s 1400 -n -c 10000 -q 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 1400(1428) bytes of data.

--- 192.168.1.1 ping statistics ---
10000 packets transmitted, 10000 received, 0% packet loss, time 32447ms
rtt min/avg/max/mdev = 1.636/12.318/198.115/34.519 ms, pipe 17, ipg/ewma 3.245/30.873 ms

---

