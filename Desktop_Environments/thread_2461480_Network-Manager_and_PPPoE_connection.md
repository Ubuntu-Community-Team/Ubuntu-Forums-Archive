---
title: "Network-Manager and PPPoE connection"
date: 2021-05-01
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-05-01
Folks,

In order to check out some network issues I have set my TP-Link modem/router to Bridge mode (acting as just a modem), status page shows as connected.

On Network-Manager I have set up a new connection under DSL/PPPoE - all pretty straight forward, select parent interface, username and password. 

My problem is, when I connect the modem to my ethernet connection I do not get any option in Network-Manager to connect.  I've tried various command line options, appear to get a successful connection, ifconfig shows extra interface ppp0 and an IP address but browser or ping command are unsuccessful.

```
ifconfig
ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1492
        inet 213.31.249.51  netmask 255.255.255.255  destination 172.16.11.162
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 29  bytes 1126 (1.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 493  bytes 28474 (28.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Any ideas what I may be missing?

Geoff

---

### Post by Geoff_Lane on 2021-05-01
As is often the case with computers it is now working :confused:

Created a second DSL-Connection and it showed up on Network Manager and connected.  Not sure what was different other than parent interface on the successful one is shows as blank whereas the original non working entry had it as enp1s0 which is what the connection obviously comes in on.

Geoff

---

