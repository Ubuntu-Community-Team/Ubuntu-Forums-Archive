---
title: "How do I find out my IP address?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-02-23
The title says it all: what's my IP address? How do I find it?

---

### Post by echo $USER on 2006-02-23
[http://whatismyip.com]("http://whatismyip.com") or [http://whatismyip.org]("http://whatismyip.org") or from terminal "ifconfig"

---

### Post by GabrielWolff on 2006-02-23
[QUOTE=echo $USER][http://whatismyip.com]("http://whatismyip.com") or [http://whatismyip.org]("http://whatismyip.org") or from terminal "ifconfig"[/QUOTE]

OK, and for what in the output I look after typing ifconfig?
Or, better: What's this machine's IP?
bash~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:35:36:75
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe35:3675/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1478755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1769877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:740589340 (706.2 MiB)  TX bytes:1385358580 (1.2 GiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:899772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:66901038 (63.8 MiB)  TX bytes:66901038 (63.8 MiB)

---

### Post by echo $USER on 2006-02-23
check this out [http://www.faqs.org/docs/linux_network/x-087-2-iface.ifconfig.html]("http://www.faqs.org/docs/linux_network/x-087-2-iface.ifconfig.html")

look for "inet addr" that will be it
inet addr:192.168.2.101 you're on a private net, that is a private address, if you want your public ip go to [http://whatismyip.org]("http://whatismyip.org")

---

### Post by GabrielWolff on 2006-02-23
look for "inet addr" that will be it[/QUOTE]

But I got two of them...
G

---

### Post by echo $USER on 2006-02-23
inet addr:192.168.2.101 is what you're looking for.
inet6 addr: fe80::20a:e4ff:fe35:3675/64 is a ip v. 6 address, dont worry about that one for now.

---

### Post by ckennow on 2007-12-25
what about the external IP address from the command line.  I know my internal address I need the external ip from commandline.  How do i go to whatsmyip.org from the commandline

---

### Post by nils234 on 2007-12-25
from terminal to that web address? Don't know why you want to but hey:

sudo firefox [http://whatismyip.org](http://whatismyip.org)

---

### Post by Yannick Le Saint kyncani on 2007-12-25
wget -q -O- [http://whatismyip.org/](http://whatismyip.org/)

---

