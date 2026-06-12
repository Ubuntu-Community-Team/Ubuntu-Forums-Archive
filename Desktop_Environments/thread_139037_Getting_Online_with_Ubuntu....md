---
title: "Getting Online with Ubuntu..."
date: 2006-03-03
forum: Desktop Environments
---

### Post by sony102600 on 2006-03-03
Is there anyway to get online using ubuntu if I am using a Asrock Dual 939 Mother Board?  I installed ubuntu about 3 days ago, and have been trying to activate and set to dhcp the eth0 setting and nothing seems to work?  

I am new to ubuntu but feel this probably requires some work over my head..

Any Help out there?

---

### Post by jamyskis on 2006-03-03
How exactly are you looking to get online? Do you have DSL/broadband, dial-up or are you going through a network?

---

### Post by sony102600 on 2006-03-03
thanks for the reply... I go to Iowa State, and am hooked up directly throught he university network.... here are some outputs for sudo dhclient and sudo ifconfig -a

dhclinet

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:13:8f:73:e8:e9
Sending on   LPF/eth0/00:13:8f:73:e8:e9
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:13:8F:73:E8:E9
          inet6 addr: fe80::213:8fff:fe73:e8e9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:7 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000
          RX bytes:1163970 (1.1 MiB)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe400

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:102840 (100.4 KiB)  TX bytes:102840 (100.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by wolfchri on 2006-03-03
The ASRock DualSata uses an ULI chipset for networking / NIC that is supported from Kernel 2.6.14 and later. I also have complete system freezes on Ubuntu Breezy with this board, as well as on PCLinuxOS 9.2 (2.6.12 kernel).

Dapper runs very well, in 64 bit and 32 bit and supports the network. So I suggest you go for Dapper. However, there were some issues loading the ULI kernel module after some updates during the Dapper development cycle. That should be solved by now.

---

