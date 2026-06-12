---
title: "Network help"
date: 2006-06-07
forum: Desktop Environments
---

### Post by balloons on 2006-06-07
I need help setting up the following network.
I want one network card to be always on, DHCP for an IP to a modem for my internet. Then I want an offline network to share files between me and my server, via a spare router. This worked out of the box on breezy, not sure  what I did to make it stop afer upgrading.

```
-----------------------
internet modem
192.168.0.1
------------------------
|
|
|
---------------------
linux box
eth0 DHCP (direct internet connection)                     --------------
eth1 192.168.1.100 static     ----------------             router   192.168.1.1
-----------------------                                 ---------------
                                                                      |
                                                                      |
                                                                      |
                                                    another pc 192.168.1.101 static
```

---

### Post by steve.horsley on 2006-06-07
Can you post the output from these commands: 
> ifconfig
route
cat /proc/sys/net/ipv4/ip_forward


---

### Post by balloons on 2006-06-07
**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:50:09:D4
          inet addr:69.221.3.36  Bcast:69.221.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe50:9d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4796909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4297367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1061349544 (1012.1 MiB)  TX bytes:2431321817 (2.2 GiB)
          Interrupt:177 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:861666 (841.4 KiB)  TX bytes:861666 (841.4 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.226.1  Bcast:192.168.226.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.153.1  Bcast:192.168.153.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
**route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.226.0   *               255.255.255.0   U     0      0        0 vmnet1
69.221.3.0      *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.153.0   *               255.255.255.0   U     0      0        0 vmnet8
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
default         69.221.3.37     0.0.0.0         UG    0      0        0 eth0

```
**cat /proc/sys/net/ipv4/ip_forward**
```
0
```

Thanks for your help :-) I should note that enable the eth1 connection in network config, drops my internet connection. (gateway problem).

---

### Post by steve.horsley on 2006-06-07
I think I follow what's going on.

I assume that you took ifconfig while eth1 was disabled, but took route while eth1 was enabled. 

I also assume that you made a typo, and the other PC is not on 192.168.1.101 (because that's the same subnet, you don't need to go through a router). I will assume that the other PC is on 192.168.2.x for now.

If I'm right, try this: 
backup **/etc/network/interfaces** and then add the following to it (or replace the existing eth1 stanza):
```
auto eth1
eth1 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    up route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1
```

If eth1 is 192.168.1.100 and the other PC is 192.168.1.101 then you are presumably connectiong through a switch and not a router. If so, you do not need to add a route to the routing table - don't enter that line.

We'll see how that goes.
Steve

---

### Post by balloons on 2006-06-08
Lol. Your right I must have copied the wrong ifconfig. I enabled it first to make sure, but must have grabbed an old ifconfig. I'm actually using a WRT54G with dd-wrt on it, but I'd just like to use it as a switch, as I don't need (or want) the internet on the other pc. Plus, I don't need access to it 24/7 only a few hours on some days, hence it's easier to turn the wrt54g on and off, and enable/disable the connection. I do have a 24 port switch (nice and big :grin:) that I could use if needbe. I added what you said, but still cannot ping 192.168.1.1, which is the wrt54g. I can reshow the other commands, if it will help.. 

**interfaces file**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp


iface eth1 inet dhcp


auto eth1
eth1 inet static
    address 192.168.1.100
    netmask 255.255.255.0


```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:50:09:D4
          inet addr:69.221.3.36  Bcast:69.221.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe50:9d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5252833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4947448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1139780231 (1.0 GiB)  TX bytes:3142419965 (2.9 GiB)
          Interrupt:177 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:39:03:FE
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe39:3fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4182 (4.0 KiB)  TX bytes:8428 (8.2 KiB)
          Interrupt:209 Base address:0x800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1195542 (1.1 MiB)  TX bytes:1195542 (1.1 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.226.1  Bcast:192.168.226.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.153.1  Bcast:192.168.153.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

**route**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.226.0   *               255.255.255.0   U     0      0        0 vmnet1
69.221.3.0      *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.153.0   *               255.255.255.0   U     0      0        0 vmnet8
default         ppp-69-221-3-37 0.0.0.0         UG    0      0        0 eth0

```

**iptables -L**
```
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.0.1          anywhere
ACCEPT     all  --  192.168.1.1          anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:10320:10340
ACCEPT     udp  --  anywhere             anywhere            udp dpts:10320:10340
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.0.1          anywhere
ACCEPT     all  --  anywhere             anywhere
LSI        udp  --  anywhere             anywhere            udp dpt:33434
LSI        icmp --  anywhere             anywhere
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             ppp-69-221-3-
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
LSI        udp  --  anywhere             anywhere            udp dpt:33434
LSI        icmp --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (6 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  ppp-69-221-3-36  192.168.0.1   tcp dpt:domain
ACCEPT     udp  --  ppp-69-221-3-36  192.168.0.1   udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
```

---

### Post by steve.horsley on 2006-06-08
There is a mistakein the interfaces file at the moment - I missed a word, and you need to remove the line that says eth1 is DHCP. ANd it looks like your file doesn't say to start eth0 ad startup (auto etho). Try this :
```
# 
This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The local network
auto eth1
iface eth1 inet static
    address 192.168.1.100
    netmask 255.255.255.0

```

I don't know the WRT thing, I'll assume is behaves as a switch.

I'm not that good with iptables, bit it looks to me as though the firewall is largely disabled, and should be allowing you to talk to 192.168.1.x. 

Try installing ethereal to see in detail what's going on over the interfaces. See if you can see the pings going out over eth1, and the replies coming back in. The routing table looks OK to me know - you aren't getting a second default route, so your internet shouldn't be breaking when eth1 comes up.

---

### Post by balloons on 2006-06-08
I included iptables, because after fixing the gateway issue, I couldn't ping 192.168.1.1, so I guessed firewall issues. I was correct. I configured the firewall with firestarter. Turning firestarter off lets me see and connect to 192.168.1.1, and access the other pc, etc. thanks for you help. The question now becomes a firewall issue, so hopefully I can sort it out. As you saw though, I was allowing packets from the modem and router, so not sure why they were being blocked?

**With firewall**
sudo ping  192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

**Without firewall**
sudo ping  192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.19 ms

---

### Post by balloons on 2006-06-08
Yep, works great now.. Just have to temp disable the firewall.. Guarddog didn't seem to do any better with it

---

### Post by steve.horsley on 2006-06-08
Good. All I can say about iptables is that I thknk it has a -v option for the listing, that gives packet counts. You may be able to figure out from that which line is dropping your pings.

---

