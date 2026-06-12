---
title: "Network - Requesting a WiFi network address for 'MyHotspot' - Fails"
date: 2022-09-17
forum: Desktop Environments
---

### Post by ukkid35 on 2022-09-17
I have been able to create a working hotspot successfully using this VivoBook E203MA previously

However it now has a fresh install of 22.04.1 LTS, so I had to recreate the connection using the GUI

When the network is created it reports 'Connection established', but from then on the status is - Requesting a WiFi network address for 'MyHotspot'

I can connect to it from another device, although the hotspot is hidden, and the other device reports - Failed to obtain IP address

I have also tried creating the connection using a command line - ```
nmcli device wifi hotspot ifname wlo1 ssid MyHotspot2 password "PASSWORD"

```

However the same issue occurs

Here is the ifconfig wlo1

```
wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>mtu 1500
inet 10.42.0.1 netmask 255.255.255.0 broadcast 10.42.0.255
inet6 2a02:810b:169f:edde::1 prefixlen 64 scopeid 0x0
inet6 fe80::fdb7:e1c6:aa71:fd55 prefixlen 64 scopeid 0x20
ether 84:c5:a6:76:c5:37 txqueuelen 1000 (Ethernet)
RX packets 155056 bytes 208321248 (208.3 MB)
RX errors 0 dropped 4 overruns 0 frame 0
TX packets 61828 bytes 9059940 (9.0 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

```

I have also tested with a LIVE USB of Ubuntu 20.04.5, and the same issue occurs

I will try to test on another LAN, just in case that makes a difference

Any suggestions very welcome

---

### Post by ukkid35 on 2022-09-22
I've tried on a different LAN where I have been able to create a hotspot before, and the same issue occurs

---

