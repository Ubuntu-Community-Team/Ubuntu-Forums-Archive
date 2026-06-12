---
title: "vinagre don't work..."
date: 2009-02-25
forum: General Help
---

### Post by Uhuabin on 2009-02-25
Hi. I want to connect to my desktop via my laptop. Both are online. The ping results are as follows.
```
PING 192.168.0.190 (192.168.0.190) 56(84) bytes of data.
64 bytes from 192.168.0.190: icmp_seq=1 ttl=64 time=1.88 ms
64 bytes from 192.168.0.190: icmp_seq=2 ttl=64 time=0.311 ms
64 bytes from 192.168.0.190: icmp_seq=3 ttl=64 time=0.298 ms
64 bytes from 192.168.0.190: icmp_seq=4 ttl=64 time=0.300 ms
64 bytes from 192.168.0.190: icmp_seq=5 ttl=64 time=0.308 ms
64 bytes from 192.168.0.190: icmp_seq=6 ttl=64 time=0.353 ms
64 bytes from 192.168.0.190: icmp_seq=7 ttl=64 time=0.276 ms
64 bytes from 192.168.0.190: icmp_seq=8 ttl=64 time=0.309 ms
64 bytes from 192.168.0.190: icmp_seq=9 ttl=64 time=0.276 ms
64 bytes from 192.168.0.190: icmp_seq=10 ttl=64 time=0.272 ms

--- 192.168.1.190 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9009ms
rtt min/avg/max/mdev = 0.272/0.458/1.886/0.477 ms
```

where the ip address is my desktop's. I can connect to localhost on both computer and the option 'Only allow local connections' is surely unchecked. But when I type: vinagre 192.168.0.190 on my laptop, I got a message like this:

```
** (vinagre:15676): WARNING **: Resolving failed: Timeout reached
```

Another time I tried: vinagre <desktop>:0, and got a pop-up window telling me: Connection to host <desktop>:5900 was closed. 

I don't know what's wrong here so please help me. Thanks a lot.

---

### Post by Uhuabin on 2009-02-26
Solved. I set a firewall on the desktop and forgot to open port 5900. Thanks.

---

