---
title: "Problems with cable internet connection"
date: 2006-05-24
forum: Desktop Environments
---

### Post by Kallikrates on 2006-05-24
I installed Breezy Badger on my computer about three months ago. At the time, it recognised the modem without problems, and the Internet worked from the start.

A few weeks ago, I started to have problems. It would take up to 15 minutes to connect to the Internet when I booted the computer. And then two days ago, the connection died completely. The problem does not come from the modem or my provider, as I'm posting this from the same computer (but on Windows 2000).

I'm using cable internet via [Numéricable]("http://www.numericable.fr/hp/index.php"). My Modem is a Motorola Surfboard SB4200E. It is connected to my computer via a USB cable, and it's not part of a local network.

I posted about that problem on the French Ubuntu Forum, though I can't link to it as it seems to be down. The people who tried to helped me couldn't find a solution to my problem, but gave me a list of things to try which I'm going to duplicate here:

```
ifconfig -a

eth0      Lien encap:Ethernet  HWaddr 00:11:2F:B4:A6:F6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:23 Adresse de base:0x9000

eth1      Lien encap:Ethernet  HWaddr 00:0C:E5:EA:15:63
          inet adr:82.216.115.246  Bcast:82.216.115.255  Masque:255.255.255.0
          adr inet6: fe80::20c:e5ff:feea:1563/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:257618 (251.5 KiB)  TX bytes:1062 (1.0 KiB)

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:49175 (48.0 KiB)  TX bytes:49175 (48.0 KiB)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
```
netstat -rn

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
82.216.115.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
```
```
cat /etc/resolv.conf

nameserver 81.220.255.4
nameserver 80.236.0.68
```
```
ping -c 1 66.102.7.147

connect: Network is unreachable
```
I also found this to try when I searched these forums:```
sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 9347
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0c:e5:ea:15:63
Sending on   LPF/eth1/00:0c:e5:ea:15:63
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.51.128.1
SIOCADDRT: Network is unreachable
bound to 82.216.115.246 -- renewal in 36780 seconds.
```
After looking at [this thread]("http://www.ubuntuforums.org/showthread.php?t=151443&highlight=%22connect%3A+Network+unreachable%22+cable"), I tried to edit /etc/network/interfaces, but the line the OP had to add in it were already in mine:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth1

iface dsl-provider inet ppp
provider dsl-provider
```
Finally, I tried sudo pppoeconf, but it seemed to keep timing out, and finally gave me this error message:> Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.
Can someone help me? I'm getting desperate here. ](*,)

---

### Post by Kallikrates on 2006-05-25
bump?

---

### Post by Kallikrates on 2006-05-29
I've tried reinstalling Ubuntu, but I still haven't an internet connection. For now, I've installed Breezy, but I also tried with Dapper Beta.

During the installation, my connection wasn't detected. I tried to configure it manually. I used the IP address that I get by doing ipconfig in Windows, and I also tried with the IP address I used to have in Ubuntu, when the internet was working. No results with either.

I've tried using an ethernet cable instead of a USB cable to plug my modem into the computer, but it didn't work either.

Please help?

PS: my new results:
```
emanuelle@ubuntu:~$ ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:11:2F:B4:A6:F6
          inet adr:81.220.144.68  Bcast:81.220.144.255  Masque:255.255.255.0
          adr inet6: fe80::211:2fff:feb4:a6f6/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interruption:23 Adresse de base:0x9000

eth1      Lien encap:Ethernet  HWaddr 00:0C:E5:EA:15:63
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:92257 (90.0 KiB)  TX bytes:92257 (90.0 KiB)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

emanuelle@ubuntu:~$ netstat -rn
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic   MSS Fenêtre irtt Iface
81.220.144.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         81.220.144.1    0.0.0.0         UG        0 0          0 eth0
emanuelle@ubuntu:~$ cat /etc/resolv.conf
nameserver 81.220.144.1
emanuelle@ubuntu:~$ ping -c 1 66.102.7.147
PING 66.102.7.147 (66.102.7.147) 56(84) bytes of data.
From 81.220.144.68 icmp_seq=1 Destination Host Unreachable

--- 66.102.7.147 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
```

---

### Post by jpg on 2006-09-04
I can't help much, but I have a similar problem with a bad NIC on the motherboard, and then the same situation with the USB connection: it was auto-detected, worked fine for several months, and then just stopped working, probably due to some software update (I am guessing).

Let us know if you find any solutions...

---

### Post by Kallikrates on 2006-09-04
Oh, oops. I had completely forgotten about this post. It's been [solved]("http://forum.ubuntu-fr.org/viewtopic.php?id=40769&p=2") ages ago, sorry.

The problem was that there was no default route to eth1.
```
sudo route add default dev eth1
```
That solved the problem, though only temporarily, as I had to do it for each reboot, until the problem disappeared as mysteriously as it had appeared.

I hope it can help you :)

---

