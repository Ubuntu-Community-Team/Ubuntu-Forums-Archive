---
title: "ip listing"
date: 2009-01-28
forum: General Help
---

### Post by malanco on 2009-01-28
hi guys, ill like to make a listing of the used ips on my network, how can i get a listing of all used ips?

thanks!!

---

### Post by -ovid- on 2009-01-28
> **malanco said:**
> hi guys, ill like to make a listing of the used ips on my network, how can i get a listing of all used ips?

thanks!!

This depends on the hosts (if they are firewalled and such) or what device you are querying from. Do you have a switch? Routers in between your network addresses?

But sending traffic from your Ubuntu system may help - you can check with nmap sweeps, or arp or fping...

Keep in mind: Network querying is totally dependent upon allowed/permitted traffic.

NMAP Ping Scan
```
nmap -sP x.x.x.x/24
```

ARP query
```
arp -a
```
(will not send traffic but checks the MAC address table for already communicated with systems)

FPING
```
fping -g x.x.x.x/24
```

note: you may need to install the apps "nmap" or "fping" first...
```
apt-get install nmap
```
```
apt-get install fping
```

---

