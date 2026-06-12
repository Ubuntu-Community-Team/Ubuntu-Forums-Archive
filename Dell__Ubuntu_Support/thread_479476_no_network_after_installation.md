---
title: "no network after installation"
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by lmtoe on 2007-06-20
I have a new Dell Latitude 630.  After installing 7.0.4 desktop version, I have no recognized network interfaces.  I have integrated ethernet and wireless in the laptop but neither are recognized.  

No idea how to resolve this?  Please help

Many thanks in advance!

---

### Post by lmtoe on 2007-06-20
here is output from /etc/network/interfaces...

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


and here is output from ifconfig -a...

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4712 (4.6 KiB)  TX bytes:4712 (4.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Herb Perkins-Frederick on 2007-07-21
After I reinstalled Feisty on my new Dell, it did not recognize the ethernet port built into the motherboard.  I installed a 3com card, and it recognized that immediately.

---

