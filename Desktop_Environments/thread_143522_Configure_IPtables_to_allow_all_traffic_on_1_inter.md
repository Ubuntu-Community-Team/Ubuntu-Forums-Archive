---
title: "Configure IPtables to allow all traffic on 1 interface"
date: 2006-03-12
forum: Desktop Environments
---

### Post by jamespi on 2006-03-12
I have a USB DSL Modem as ppp0, a wifi card as eth1 (sharing the internet connection round my house) and an extra ethernet card as eth0.

The eth0 ethernet card is connected to my XBox via a crossover cable.
(N.B i am not trying to share the internet connection via NAT with my xbox, i actually want to use KAID to tunnel it)

here is the setup (i've censored my public IP):

eth0      Link encap:Ethernet  HWaddr 00:01:02:24:8D:E3
          inet addr:192.168.1.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe24:8de3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6379 (6.2 KiB)  TX bytes:1605 (1.5 KiB)
          Interrupt:16 Base address:0xc400

eth1      Link encap:Ethernet  HWaddr 00:04:75:88:AA:1B
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fe88:aa1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:483817 (472.4 KiB)  TX bytes:1151674 (1.0 MiB)
          Interrupt:17 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6096 (5.9 KiB)  TX bytes:6096 (5.9 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:XX.XX.XX.XX  P-t-P:62.241.161.241  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:16384  Metric:1
          RX packets:6238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3842585 (3.6 MiB)  TX bytes:795732 (777.0 KiB)


Note that my broadcast IP on eth0 is wrong - it should be 192.168.1.255 but i dont know how to change it and it doesnt matter anyway.

I used firestarter to setup the NAT over eth1.  

Now my problem is this: if i turn my firewall off, i can ping, ftp and http to my xbox (at IP 192.168.1.2). When the firewall is on, i ping and get "operation not permitted". This i assume means the firewall is blocking that traffic. I told firestarter to allow incoming connections from 192.168.1.2 but since this is outgoing that shouldnt make a difference, and hasn't. 

All outgoing connections have to be blacklisted to be blocked, so there is no way to tell it to let traffic through to 192.168.1.2 since it should be doing that by default.

Can firestarter understand 3 network interfaces? or is it purely designed to handle 1 internet + 1 LAN?

I totally trust my xbox not to hack me, so it would be good to just tell iptables not to bind to eth0. 

How do i do this?

---

### Post by jamespi on 2006-03-13
scratch all that, it doesnt matter; KAID doesnt use the IP stack to access the xbox anyway, so it detects it through the firewall.

---

### Post by yusufk on 2006-03-13
perhaps the broadcast address does make a difference. You may want to specify the right one in /etc/network/interfaces. I notice the same problem, often with my wireless interface, when I use the network configuration app I get the wrong broadcast address, a bug maybe?

---

