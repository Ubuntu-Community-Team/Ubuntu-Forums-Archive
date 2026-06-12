---
title: "Nautilus doesn't open,either some commands don't work"
date: 2014-10-19
forum: Desktop Environments
---

### Post by zeusys on 2014-10-19
Hi.
I need to establish a vpn connection to multiple servers in my company' network.VPN connection types are different, some of them are pptp and others are connecting to a Kerio.I realized that sometimes after establishing vpn connection, nautilus doesn't open.In this situation I can't use command such as df.By chance I notices that this situation is somehow related to routing table after establishing a vpn connection.So sometimes I can fix this issue bu adding one static route :
```
ip route add 192.168.0.0/16 via 192.168.102.254
```
192.168.102.254 is our network gateway.
But sometimes this doesn't work.I couldn't understand the reason behind this situation and why using file browser(nautilus) or some commands such as "df" are related to vpn connection or routing table?

Please guide me a bit .or provide a solution.
Thanks

```
Ubunut 14.04 LTS x86_64
```

---

