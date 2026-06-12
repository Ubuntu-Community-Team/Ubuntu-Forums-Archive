---
title: "Bonding NIC's woes"
date: 2009-05-31
forum: General Help
---

### Post by fujikofujio on 2009-05-31
Hi I'm using 9.04 desktop on two of my computers and they each have 2 network cards, so I bonded their nics for performance, one of them runs as a web server.

here is the /etc/network/interfaces file, they are identical on both computers

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet dhcp
	slaves all
	bond-mode 0
	bond-miimon 100
	bond-downdelay 200
	bond-updelay 200

I also disabled network manager applet on both of them as this seems to mess up the bonding during restart.

The other pc works fine when restarted, the server does not however. This is the result of ifconfig on the working one after a restart.

> bond0     Link encap:Ethernet  HWaddr 00:04:75:cd:a6:cd  
          inet addr:192.168.219.122  Bcast:192.168.219.255  Mask:255.255.255.0
          inet6 addr: fe80::204:75ff:fecd:a6cd/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:8489 errors:0 dropped:0 overruns:83 frame:0
          TX packets:7354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3213136 (3.2 MB)  TX bytes:2218129 (2.2 MB)

eth1      Link encap:Ethernet  HWaddr 00:04:75:cd:a6:cd  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1606947 (1.6 MB)  TX bytes:1082329 (1.0 MB)
          Interrupt:23 Base address:0x4000 

eth2      Link encap:Ethernet  HWaddr 00:04:75:cd:a6:cd  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4293 errors:0 dropped:0 overruns:83 frame:0
          TX packets:3706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1606189 (1.6 MB)  TX bytes:1135800 (1.1 MB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1141188 (1.1 MB)  TX bytes:1141188 (1.1 MB)


Now here is the result of ifconfig on the server (running nginx/php/mysql/squid/privoxy)

> 
bond0     Link encap:Ethernet  HWaddr 00:02:b3:e7:73:43  
          inet addr:192.168.219.142  Bcast:192.168.219.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fee7:7343/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:254072 (254.0 KB)  TX bytes:101775 (101.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:02:b3:e7:73:43  
          inet addr:192.168.219.142  Bcast:192.168.219.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:189199 (189.1 KB)  TX bytes:50509 (50.5 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:b3:e7:73:43  
          inet addr:192.168.219.142  Bcast:192.168.219.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64873 (64.8 KB)  TX bytes:51266 (51.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53615 (53.6 KB)  TX bytes:53615 (53.6 KB)


For some reason eth0 and eth1 still continues to request an ip from the dhcp server. Only after typing

> 
sudo ifconfig eth0 down
sudo ifconfig eth1 down


does the bonding work again and I'm able to access the internet and my web server becomes accessible again on the internet.

Any clues, tips, I would greatly appreciate it thanks :)

---

