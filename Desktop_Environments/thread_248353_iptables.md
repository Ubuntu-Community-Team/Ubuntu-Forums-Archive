---
title: "iptables"
date: 2006-09-01
forum: Desktop Environments
---

### Post by fakie_flip on 2006-09-01
No homework is getting done on this computer. It is being used for playing instead. I would like to block instant messenger and myspace. Is there any better way to block websites than using iptables? I would like to block all website's on the myspace server. I'd also like to block all instant messaging chatting from this computer. This computer is also running windows in VMware server, so I'd like to block myspace from being used from it too. If I use iptables to block myspace, it will block it from any web browser even if the web browser is IE6 running in VMware Server right? I got this ip using ping. How can I block all of it sending and coming to this computer using iptables or something better?

```
ubuntu@ubuntu:~$ ping www.myspace.com
PING www.myspace.com (216.178.32.51) 56(84) bytes of data.
64 bytes from 216.178.32.51: icmp_seq=1 ttl=244 time=115 ms
64 bytes from 216.178.32.51: icmp_seq=2 ttl=244 time=156 ms

--- www.myspace.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1005ms
rtt min/avg/max/mdev = 115.457/136.140/156.823/20.683 ms
ubuntu@ubuntu:~$

```

---

### Post by aysiu on 2006-09-01
Can't you just not visit MySpace?

---

### Post by fakie_flip on 2006-09-01
What should I put in /etc/hosts.deny to block websites? Please try your suggestion before telling me because the ones I've been trying haven't been working.

---

