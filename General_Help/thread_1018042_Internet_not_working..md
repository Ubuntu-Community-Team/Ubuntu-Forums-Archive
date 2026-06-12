---
title: "Internet not working."
date: 2008-12-21
forum: General Help
---

### Post by retskrad on 2008-12-21
I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.
When I right click on the internet thing at the right top, it says Auto eth0 or something, I clicked on it and the internet loads again. Thenn again it says disconected. I have tried amny times to restart. Internet works in windows, but not in ubuntu. Whats going on?


PS:I'm using ubuntu 8.10.

EDIT: I wrote ifconfig in the terminal and I got this and burned it to a dvd and logged into windows to show you guys:

> admin3@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:11:09:6c:cd:5e
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:240 errors:0 dropped:0 overruns:0 frame:0
TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15040 (15.0 KB) TX bytes:15040 (15.0 KB)

admin3@ubuntu:~$

---

### Post by eBoxNet on 2008-12-21
do you use a router in order to connect to the net?
does it have dhcp enabled?can you check in your lan connection settings under windows if it gets automatically an ip?

---

### Post by Xiangxianni on 2008-12-21
> **retskrad said:**
> I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.
When I right click on the internet thing at the right top, it says Auto eth0 or something, I clicked on it and the internet loads again. Thenn again it says disconected. I have tried amny times to restart. Internet works in windows, but not in ubuntu. Whats going on?


PS:I'm using ubuntu 8.10.

EDIT: I wrote ifconfig in the terminal and I got this and burned it to a dvd and logged into windows to show you guys:
From the output of ifconfig,your NIC haven't  got a ip address.This is the root cause.

---

### Post by retskrad on 2008-12-21
I removed ubuntu and installed kubuntu with wubi. Still no internet.

---

### Post by retskrad on 2008-12-22
Anyone?

---

