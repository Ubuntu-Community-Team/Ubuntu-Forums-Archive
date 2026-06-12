---
title: "Strange Behavoir (help)"
date: 2006-07-20
forum: Desktop Environments
---

### Post by meph on 2006-07-20
Im new at this and im just trying to learn things about linux in gerenral. My coworkers pointed me to UBUNTU and i finaly installed a copy of desktop and put a LAMP components on it. Anyway it was working fine untill last night. I intalled Automatix on my computer cause i wanted to get the NViDIA drivers and a few other goodies but now seems like my internet is acting up. I use the latest version of Firefox and everytime i go to a page it times out.
Lets take for example the very popular myspace.com if i try to go to it, the computer takes about 10 min to load just a few links and no graphics. all other pages that i try fail including google.com

Can anyone tell me what the problem is?

this is ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:0D:87:54:52:DF
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe54:52df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:15 txqueuelen:1000
          RX bytes:10784321 (10.2 MiB)  TX bytes:552224 (539.2 KiB)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22852 (22.3 KiB)  TX bytes:22852 (22.3 KiB)

```

ping google.com

```
ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from google.com (64.233.187.99): icmp_seq=1 ttl=246 time=115 ms
64 bytes from google.com (64.233.187.99): icmp_seq=2 ttl=246 time=114 ms
64 bytes from google.com (64.233.187.99): icmp_seq=3 ttl=246 time=115 ms
64 bytes from google.com (64.233.187.99): icmp_seq=4 ttl=246 time=114 ms
64 bytes from google.com (64.233.187.99): icmp_seq=5 ttl=246 time=121 ms
64 bytes from google.com (64.233.187.99): icmp_seq=6 ttl=246 time=115 ms
64 bytes from google.com (64.233.187.99): icmp_seq=7 ttl=246 time=115 ms
64 bytes from google.com (64.233.187.99): icmp_seq=8 ttl=246 time=114 ms
64 bytes from google.com (64.233.187.99): icmp_seq=9 ttl=246 time=114 ms
64 bytes from google.com (64.233.187.99): icmp_seq=10 ttl=246 time=115 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9009ms
rtt min/avg/max/mdev = 114.378/115.670/121.192/1.877 ms
```


ping myspace.com

```
ping myspace.com
PING myspace.com (63.208.226.43) 56(84) bytes of data.
64 bytes from myspace.com (63.208.226.43): icmp_seq=1 ttl=242 time=93.2 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=2 ttl=242 time=92.5 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=3 ttl=242 time=92.4 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=4 ttl=242 time=92.2 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=5 ttl=242 time=91.9 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=6 ttl=242 time=93.4 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=7 ttl=242 time=92.6 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=8 ttl=242 time=92.8 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=9 ttl=242 time=92.0 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=10 ttl=242 time=91.8 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=11 ttl=242 time=92.0 ms
64 bytes from myspace.com (63.208.226.43): icmp_seq=12 ttl=242 time=93.0 ms

--- myspace.com ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 10998ms
rtt min/avg/max/mdev = 91.891/92.549/93.479/0.569 ms

```

I don't know how but the support forums loaded up slow but just fine.

---

### Post by kingmonkey on 2006-07-20
Those ifconfigs and pings look correct to me.

Some people report that switching IPv6 off speeds up their internet because of incompatibilities with their router. Try searching the fourm for IPv6.

---

