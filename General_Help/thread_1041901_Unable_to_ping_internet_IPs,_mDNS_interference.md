---
title: "Unable to ping internet IPs, mDNS interference?"
date: 2009-01-17
forum: General Help
---

### Post by Superkuh on 2009-01-17
I am having trouble pinging anything beyond my router. **Other computers on the network do not have this problem**. It is an issue with my install of ubuntu 8.04 and my mis-configuration. I can ping anything on the LAN by IP. But when I try to ping, say, [www.google.com](www.google.com) (or one of google's IPs), the domain is resolved to the proper IP (and dig works fine) but ping still reports errors. 

*Background information*
```
#/etc/network/interfaces
...
auto eth0
iface eth0 inet static
address 10.13.37.192
netmask 255.255.255.0
gateway 10.13.37.1
```

```
# /etc/nsswitch.conf
...
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
...
```

> #router
superkuh@epimetheus:~/$ ping 10.13.37.1
PING 10.13.37.1 (10.13.37.1) 56(84) bytes of data.
64 bytes from 10.13.37.1: icmp_seq=1 ttl=64 time=0.889 ms
...
#google
superkuh@epimetheus:~/$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (74.125.95.104) 56(84) bytes of data.
From epimetheus.local (10.13.37.192) icmp_seq=1 Destination Port Unreachable
...
#google IP
superkuh@epimetheus:~/$ ping 74.125.95.104
PING 74.125.95.104 (74.125.95.104) 56(84) bytes of data.
From 10.13.37.192 icmp_seq=1 Destination Port Unreachable
...

I used wireshark to watch the ping process in more detail which can be viewed at [http://pastebin.ca/1310670](http://pastebin.ca/1310670). In the packet dump I noted that issues began after an MDNS exchange, but I don't know where to go from here. I haven't noticed networking issues with anything else (besides amule). Any ideas of what I might test to further narrow down the problem such that I can ping internet IPs again? I realize this is all very vauge. :\

---

### Post by neur0 on 2009-01-17
Try the traceroute to the outside IP with:
```
tracepath -n <address>
```

And make sure there are no iptables rules set up with:
```
sudo iptables -L
```

---

