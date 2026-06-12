---
title: "gweather + squid == no forecast?"
date: 2009-11-20
forum: Desktop Environments
---

### Post by emanuel.landeholm on 2009-11-20
Hi!

I'm trying to debug a connection issue with gweather. I'm running squid on my desktop computer, and if I go to System>Administration>Network Proxy and select manual, my weather forecast applet in the panel stops updating.

tcpdump tells me libgweather is not sending anything. No libgweather access in the squid logs.

libgweather is version 2.28-1ubuntu2
squid is 2.7.STABLE6-2ubuntu-2

The funny thing is I have a similar setup on my desktop computer at work, except that the http cache runs on a dedicated server on the LAN. The server is running Ubuntu Server 9.04 and my work desktop is running Karmic. The weather applet is updating OK.

Squid configurations are similar at home and at work. The only difference as far as I can tell is the listen port #. apt, update-manager, synaptics, liferea, google chrome & firefox are working OK with both proxies. I know they hit the cache from browsing access logs.

What gives?
TIA,
Emanuel

---

### Post by emanuel.landeholm on 2009-11-20
I have some more info. tcpdump -v -i lo says:

```

tcpdump: listening on lo, link-type EN10MB (Ethernet), capture size 96 bytes
23:45:58.211876 IP (tos 0x0, ttl 64, id 41823, offset 0, flags [DF], proto TCP (6), length 395)
    localhost.8888 > localhost.37462: Flags [P.], seq 395853013:395853356, ack 398395395, win 769, options [nop,nop,TS val 948662 ecr 934817], length 343
23:45:58.211895 IP (tos 0x0, ttl 64, id 17827, offset 0, flags [DF], proto TCP (6), length 52)
    localhost.37462 > localhost.8888: Flags [.], cksum 0x5805 (correct), ack 343, win 664, options [nop,nop,TS val 948662 ecr 948662], length 0
23:45:58.211930 IP (tos 0x0, ttl 64, id 41824, offset 0, flags [DF], proto TCP (6), length 77)
    localhost.8888 > localhost.37462: Flags [P.], seq 343:368, ack 1, win 769, options [nop,nop,TS val 948662 ecr 948662], length 25
23:45:58.211940 IP (tos 0x0, ttl 64, id 17828, offset 0, flags [DF], proto TCP (6), length 52)
    localhost.37462 > localhost.8888: Flags [.], cksum 0x57ec (correct), ack 368, win 664, options [nop,nop,TS val 948662 ecr 948662], length 0
23:45:58.317932 IP (tos 0x0, ttl 64, id 17829, offset 0, flags [DF], proto TCP (6), length 1428)
    localhost.37462 > localhost.8888: Flags [P.], seq 1:1377, ack 368, win 664, options [nop,nop,TS val 948689 ecr 948662], length 1376
23:45:58.317953 IP (tos 0x0, ttl 64, id 41825, offset 0, flags [DF], proto TCP (6), length 52)
    localhost.8888 > localhost.37462: Flags [.], cksum 0x51ed (correct), ack 1377, win 769, options [nop,nop,TS val 948689 ecr 948689], length 0
^C
6 packets captured
12 packets received by filter
0 packets dropped by kernel

```

8888 is squid's port.

---

