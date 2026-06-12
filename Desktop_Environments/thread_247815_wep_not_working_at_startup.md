---
title: "wep not working at startup"
date: 2006-08-31
forum: Desktop Environments
---

### Post by jnsen on 2006-08-31
i configured my wireless card in /etc/network/interfaces to be set up at boot, and everything works except for one thing: i have to reconfigure the encription key
```
iwconfig wlan0 key xxxxxxxxx open
```
after the boot to make it work, otherwise even pinging the gateway will give me a "Host unreachable" error.

i put that line of code in rc.local, so that the wireless is configured automatically anyway, but i would like to know where is the problem to find a cleaner solution. any idea?

here's my /etc/network/interfaces:
```
auto wlan0
iface wlan0 inet static
address 192.168.10.10
netmask 255.255.255.0
network 192.168.10.0
gateway 192.168.10.1
dns-nameserver 130.244.127.161 130.244.127.169
wireless-essid xxxx
wireless-mode ad-hoc
wireless-channel 7
wireless-key xxxxxxxxx open

```

---

