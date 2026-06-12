---
title: "Broadband Internet as slow as 56K in Dapper, fine in Windows"
date: 2006-07-06
forum: Desktop Environments
---

### Post by rock_lobster on 2006-07-06
Okay, my Internet connection was fine up until a few days ago...  I don't know what happened, it just slowed down and I almost thought I was on dial-up again.

Here is what I got with Ubuntu when I pinged Google:

```
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=241 time=121 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=241 time=128 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=241 time=38.3 ms
64 bytes from 72.14.207.99: icmp_seq=4 ttl=241 time=105 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15266ms
rtt min/avg/max/mdev = 38.385/98.328/128.499/35.614 ms

```

This is what ifconfig says:

```
eth0      Link encap:Ethernet  HWaddr 00:30:18:96:7C:89
          inet addr:[edited]  Bcast:[edited]  Mask:255.255.224.0
          inet6 addr: fe80::230:18ff:fe96:7c89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:331471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1508 txqueuelen:1000
          RX bytes:42433184 (40.4 MiB)  TX bytes:22676925 (21.6 MiB)
          Interrupt:185 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1576 (1.5 KiB)  TX bytes:1576 (1.5 KiB)

```

Please help me.  This is beyond frustrating.  I'm seriously considering using Windows as my primary OS...

---

### Post by jvictor on 2006-07-06
Try disabling IPV6 ..it may help

---

### Post by rock_lobster on 2006-07-07
> **jvictor said:**
> Try disabling IPV6 ..it may help

I've already done that in Firefox, but I don't know how to do it for my entire system.

---

### Post by flipkick on 2006-07-08
disabling ipv6 helped me at this point. but it's still not as fast as on a windows station. maybe I should fix myself with a linux-router instead of this crappy shit here "Netgear mrb14 v3".

Thanks for the firefox tipp here. I already disabled it linuxwide, so firefox was the last thing i had to do.
 :idea:

---

### Post by rock_lobster on 2006-07-08
> **flipkick said:**
> disabling ipv6 helped me at this point. but it's still not as fast as on a windows station. maybe I should fix myself with a linux-router instead of this crappy shit here "Netgear mrb14 v3".

Thanks for the firefox tipp here. I already disabled it linuxwide, so firefox was the last thing i had to do.
 :idea:

I figured out how to disable IPV6 by googling it...

But I'm experiencing the same problems you are.  My Internet connection is still much faster with Windows.  I don't even have a router.  I'm using a Linksys 5 port workgroup hub.

Meh, I'll just connect directly to the modem.  My roommate has quit paying for her portion of the cable bill, so she doesn't need to have her computer on the network.

---

