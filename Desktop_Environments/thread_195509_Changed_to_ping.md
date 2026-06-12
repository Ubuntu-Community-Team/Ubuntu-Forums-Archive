---
title: "Changed to ping?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by guice on 2006-06-12
Was there a change to ping in the Dapper upgrade? Take a look at this:
```
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=238 time=47.9 ms
64 bytes from 64.233.187.99: icmp_seq=2 ttl=238 time=46.9 ms
64 bytes from 64.233.187.99: icmp_seq=3 ttl=238 time=72.1 ms
64 bytes from 64.233.187.99: icmp_seq=4 ttl=238 time=58.2 ms
64 bytes from 64.233.187.99: icmp_seq=5 ttl=238 time=73.6 ms
64 bytes from 64.233.187.99: icmp_seq=6 ttl=238 time=47.3 ms

--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 25602ms
rtt min/avg/max/mdev = 46.978/57.721/73.616/11.387 ms
```
Check out the ping times and then check out the total time. Every packet is getting sent out extremely slow. Now, the only thing I can think of is that the ping's delay time between packet gets has been increased, greatly increased.

Is this the case?

It's been bugging me, since I (very) often have to use ping to test out my connectivity (my ISP is the worst on the planet..).

---

### Post by costoa on 2006-06-13
The numbers don't seem that far off. Could you post a tracepath dump to the outside world? That will tell me were to go next.

---

### Post by esisa on 2006-06-13
I sort of have the same problem. However, it is the other way around. Pinging my new Dapper computer is very slow. I have tried pinging it from several computers. Pinging from Dapper and out is ok. I attach output from ping and tracepath from pinging topex to lilja2. And lilja2 to topex. Topex is a Dapper upgraded from Breezy. lilja2 is a clean install of Dapper.

lilja2 is a dual-boot and pinging the Windows machine is no problem, so the network card seems to be ok. 

From topex to lilja2:

```

espen@topex:~$ ping lilja2
PING lilja2.statkart.no (159.162.84.158) 56(84) bytes of data.
64 bytes from 159.162.84.158: icmp_seq=1 ttl=64 time=81.7 ms
64 bytes from 159.162.84.158: icmp_seq=2 ttl=64 time=102 ms
64 bytes from 159.162.84.158: icmp_seq=3 ttl=64 time=24.5 ms
64 bytes from 159.162.84.158: icmp_seq=4 ttl=64 time=47.6 ms



espen@topex:~$ tracepath lilja2
 1:  159.162.84.139 (159.162.84.139)                        0.175ms pmtu 1500
 1:  159.162.84.158 (159.162.84.158)                        0.831ms reached
     Resume: pmtu 1500 hops 1 back 1

```

From lilja2 to topex:

```


bente@lilja2:~$ ping topex
PING topex.statkart.no (159.162.84.139) 56(84) bytes of data.
64 bytes from 159.162.84.139: icmp_seq=1 ttl=64 time=0.748 ms
64 bytes from 159.162.84.139: icmp_seq=2 ttl=64 time=0.307 ms
64 bytes from 159.162.84.139: icmp_seq=3 ttl=64 time=0.734 ms
64 bytes from 159.162.84.139: icmp_seq=4 ttl=64 time=0.612 ms

--- topex.statkart.no ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.307/0.600/0.748/0.178 ms
bente@lilja2:~$
bente@lilja2:~$
bente@lilja2:~$
bente@lilja2:~$ tracepath topex
 1:  159.162.84.158 (159.162.84.158)                        0.159ms pmtu 1500
 1:  159.162.84.139 (159.162.84.139)                        0.894ms reached
     Resume: pmtu 1500 hops 1 back 1
bente@lilja2:~$


```

---

