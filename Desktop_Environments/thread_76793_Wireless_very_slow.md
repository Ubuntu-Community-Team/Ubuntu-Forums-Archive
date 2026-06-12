---
title: "Wireless very slow"
date: 2005-10-15
forum: Desktop Environments
---

### Post by clems[ on 2005-10-15
Hello,

I installed yesterday Ubuntu 5.10 and i have a problem with my network, infact it's very slow (2 hours to copy 350Mo)

PMCIA card US Robotics and a Netgear routeur
-------------------------------------------------------------
clems@minux:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
wireless-mode managed
wireless-essid home
wireless-key s:************
-------------------------------------------------------
clems@minux:~$ iwconfig wlan0
wlan0     IEEE 802.11b+/g+  ESSID:"home"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:DA:3B:2C
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=50/100  Signal level=30/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 -------------------------------------------------------
clems@minux:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1448 (1.4 KiB)  TX bytes:1448 (1.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:49:EA:04:E5
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:feea:4e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19785 errors:6 dropped:0 overruns:0 frame:0
          TX packets:21665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13232906 (12.6 MiB)  TX bytes:2188809 (2.0 MiB)
          Interrupt:5
-------------------------------------------------------------------------------------------
clems@minux:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
--------------------------------------------------------------------------------------------
clems@minux:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
clems@minux:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.62 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=3.62 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=3.63 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 3.621/3.627/3.634/0.005 ms
clems@minux:~$ ping 192.168.0.14
PING 192.168.0.14 (192.168.0.14) 56(84) bytes of data.
64 bytes from 192.168.0.14: icmp_seq=1 ttl=128 time=4.53 ms
64 bytes from 192.168.0.14: icmp_seq=2 ttl=128 time=4.44 ms
64 bytes from 192.168.0.14: icmp_seq=3 ttl=128 time=4.37 ms
64 bytes from 192.168.0.14: icmp_seq=4 ttl=128 time=4.71 ms

--- 192.168.0.14 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 4.371/4.515/4.711/0.136 ms
-----------------------------------------------------------------------------------
clems@minux:~$ tracepath 192.168.0.14
 1:  192.168.0.5 (192.168.0.5)                              6.684ms pmtu 1500
 1:  192.168.0.14 (192.168.0.14)                           16.996ms reached
     Resume: pmtu 1500 hops 1 back 1
------------------------------------------------------------------------------------

If someone have an idea ^^

Before Ubuntu 5.10 i tested Fedora4 and it works perfectly

---

### Post by vassie on 2005-10-16
I have the same problem with my DWL-650+ card, however if I use my DWL-610 card via ndiswrapper it's fine :S

Ben

---

### Post by vassie on 2005-10-18
Sorry to bump

Ben

---

