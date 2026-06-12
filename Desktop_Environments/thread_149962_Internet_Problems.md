---
title: "Internet Problems"
date: 2006-03-25
forum: Desktop Environments
---

### Post by thecomicrelief on 2006-03-25
I recently installed Ubuntu 5.10, and it cannot recognise my internet connection.

I started with a Ubuntu 5.04 on a network similar to the one im on now except this network had a different ADSL modem (i cannot recall the model), i have since moved and reinstalled 5.04 under exact same configuration as last time, only now Ubuntu cannot connect to the internet.
I then updated to Ubuntu 5.10, and have the same problem.
The network is as follows, 2 computers, a windows xp, and the one in question, a multiboot Xp/Ubuntu 5.10, connect to a switch, along with the ADSL modem. Both XP's connect to the internet with no problems.
Ubuntu has no problem detecting the network, and i can connect to the other XP computer with no trouble.

---

### Post by dermotti on 2006-03-25
Its possibly a dns issue....can you ping 72.14.207.99 (google) ?

post your ifconfig

---

### Post by thecomicrelief on 2006-03-25
Heres my ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:88:44:29:85
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20d:88ff:fe44:2985/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1553 (1.5 KiB)  TX bytes:1779 (1.7 KiB)
          Interrupt:18 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9599 (9.3 KiB)  TX bytes:9599 (9.3 KiB)


and heres what happens when i ping 72.14.207.99

PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=241 time=249 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=241 time=249 ms
64 bytes from 72.14.207.99: icmp_seq=4 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=6 ttl=241 time=249 ms
64 bytes from 72.14.207.99: icmp_seq=7 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=8 ttl=241 time=246 ms
64 bytes from 72.14.207.99: icmp_seq=9 ttl=241 time=245 ms
64 bytes from 72.14.207.99: icmp_seq=10 ttl=241 time=251 ms
64 bytes from 72.14.207.99: icmp_seq=11 ttl=241 time=250 ms
64 bytes from 72.14.207.99: icmp_seq=12 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=13 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=14 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=15 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=16 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=17 ttl=241 time=246 ms
64 bytes from 72.14.207.99: icmp_seq=18 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=19 ttl=241 time=249 ms
64 bytes from 72.14.207.99: icmp_seq=20 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=21 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=22 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=23 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=24 ttl=241 time=246 ms
64 bytes from 72.14.207.99: icmp_seq=25 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=26 ttl=241 time=246 ms
64 bytes from 72.14.207.99: icmp_seq=27 ttl=241 time=247 ms
64 bytes from 72.14.207.99: icmp_seq=28 ttl=241 time=250 ms
64 bytes from 72.14.207.99: icmp_seq=29 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=30 ttl=241 time=246 ms
64 bytes from 72.14.207.99: icmp_seq=31 ttl=241 time=251 ms
64 bytes from 72.14.207.99: icmp_seq=32 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=33 ttl=241 time=252 ms
64 bytes from 72.14.207.99: icmp_seq=34 ttl=241 time=248 ms
64 bytes from 72.14.207.99: icmp_seq=35 ttl=241 time=248 ms

--- 72.14.207.99 ping statistics ---
35 packets transmitted, 35 received, 0% packet loss, time 34029ms

---

### Post by dermotti on 2006-03-25
So you can ping google. If you put that IP into your browser i bet you get google. You are having DNS issues. 

Your network setup looks really funky too. Are you setup dhcp?

---

### Post by thecomicrelief on 2006-03-25
Yeah definatly using DHCP, I don't really know much about networking except that my switch seems to use 10.1.1.x for its connections.

Any advice for fixing the dns?

---

### Post by dermotti on 2006-03-25
Yea, you goto **System --> Networking --> DNS (tab)**

under **DNS SERVERS**
add 10.1.1.1 (Or whatever your gateway is)
add 6.2.2.2 (for a backup address)

reboot. 

If that doesnt work we may need to change from dhcp to static

---

### Post by thecomicrelief on 2006-03-25
Fixed, thanks for all your help.

---

### Post by dermotti on 2006-03-25
Glad to help! :p

---

