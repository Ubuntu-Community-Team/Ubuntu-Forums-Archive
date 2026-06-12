---
title: "Wireless working, but no internet?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by mkaareng on 2005-12-02
My wireless connection is working, and I have the router up and running.  I get internet through my ethernet card, but not wirelessly.  What could be wrong?

-Martin

---

### Post by dcstar on 2005-12-02
[QUOTE=mkaareng]My wireless connection is working, and I have the router up and running.  I get internet through my ethernet card, but not wirelessly.  What could be wrong?

-Martin[/QUOTE]
Numerous things, post the output of the following commands:

netstat -rn
ifconfig

---

### Post by arpunk on 2005-12-02
Can you ping a host *outside* your LAN? i.e: google.com? also, what is the output of *sudo ifconfig* and *sudo iwconfig*. Does the router have DHCP enabled?

---

### Post by gade on 2005-12-02
You can also put the output of the [FONT="Courier New"]/etc/hosts[/FONT] and type the folowing command : [FONT="Courier New"]route -n[/FONT]
Verifity your connection type, if you have a DHCP connection ou direct IP

---

### Post by MetalMusicAddict on 2005-12-02
Make sure your DNS server IP (router IP usually) is in the "DNS" tab in the "Network Settings" tool.
Ive had your same problem because of this.

---

### Post by mkaareng on 2005-12-03
Thank you for helping out. Here are the outputs:

martin@host-132-91-111-24:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
24.111.90.0     0.0.0.0         255.255.254.0   U         0 0          0 eth0
0.0.0.0         24.111.90.1     0.0.0.0         UG        0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
martin@host-132-91-111-24:~$
martin@host-132-91-111-24:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:00:99:F2:02
          inet addr:24.111.91.132  Bcast:24.111.91.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:ff:fe99:f202/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:838701 (819.0 KiB)  TX bytes:59771 (58.3 KiB)
          Interrupt:9 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:0D:54:A1:81:1B
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:54ff:fea1:811b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10783 (10.5 KiB)  TX bytes:24416 (23.8 KiB)
          Interrupt:9

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:633286 (618.4 KiB)  TX bytes:633286 (618.4 KiB)

martin@host-132-91-111-24:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:00:99:F2:02
          inet addr:24.111.91.132  Bcast:24.111.91.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:ff:fe99:f202/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:848173 (828.2 KiB)  TX bytes:60839 (59.4 KiB)
          Interrupt:9 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:0D:54:A1:81:1B
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:54ff:fea1:811b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10783 (10.5 KiB)  TX bytes:24416 (23.8 KiB)
          Interrupt:9

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:645898 (630.7 KiB)  TX bytes:645898 (630.7 KiB)

martin@host-132-91-111-24:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:EF:77:FE
          Bit Rate:54 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Link Quality=243/0  Signal level=-34 dBm  Noise level=-18 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

martin@host-132-91-111-24:~$ /etc/hosts route -n
bash: /etc/hosts: Permission denied
martin@host-132-91-111-24:~$ /etc/hosts
bash: /etc/hosts: Permission denied
martin@host-132-91-111-24:~$

What do you guys see here?

-Martin

---

