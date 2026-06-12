---
title: "how do I restart the DHCP server/client?"
date: 2006-09-22
forum: Desktop Environments
---

### Post by pmark on 2006-09-22
I have two Ethernet ports onboard. Linux recognises both:

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:8E:E5:23
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:11:D8:8E:ED:05
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe8e:ed05/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:100645442 (95.9 MiB)  TX bytes:5182122 (4.9 MiB)
          Interrupt:74
```

but I can only use one of them. Windows recognises the other one. So, when I am on Linux I need to plug eth0 and when on Windows I need to plug eth1. If I happen to reboot Linux and not change the Ethernet cable to the other port beafore Linux tries to detect hard, I need to restart Linux. Additionally, if no ports is pluged on the rooter, I also need to restart Linux.

There must be some way to restart the DHCP client/server that Linux runs without rebooting. How do I do it?

*PS: what's the correct term, DHCP client or server?*

---

### Post by PriceChild on 2006-09-22
erm....
```
sudo /etc/init.d/networking restart
```

---

### Post by cronholio on 2006-09-22
> PS: what's the correct term, DHCP client or server?

Client.

You don't need to restart it though. This will do:

```
sudo dhclient
```

---

### Post by pmark on 2006-09-24
Thank you. Both of the methods worked.

It takes some time to detect the connection. Is there a faster way?  Even if there is not, I am ok with this one.

---

