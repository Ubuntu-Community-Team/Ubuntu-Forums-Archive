---
title: "Unable to connect"
date: 2018-05-15
forum: Debian
---

### Post by nemo1985 on 2018-05-15
Hello everybody.
For some years I used a home computer as limp server with debian, everything worked like a charme.
Today I started the computer after a couple of years and it suddenly can't connect to the net.
My router doesn't detect it, I have always used a static ip (with ip rservation for the mac address in the router).
I messed with it for some hours, did the net configuration from scratch but it just doesn't work.
I tried to run ubuntu from a usb drive and the network works without issues.

> 
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


> 
ip route show
default via 192.168.0.1 dev eth0 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.3 


> 
ifconfig
eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        ether 00:19:66:8e:65:fa  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 888  bytes 115929 (113.2 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 888  bytes 115929 (113.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


this is my interfaces file:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
allow-hotplug eth0
iface eth0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        gateway 192.168.0.1
#       dns-nameservers 192.168.0.1 8.8.8.8


I suspect that the problem is the missing gateway (which should be 192.168.0.1).

Thank you in advance for any help you can give me.

---

### Post by bijayalaxmi1808 on 2018-05-24
I think yes gateway is needed when you refer to an IP which is outside of the local network.
This is the case when you request something that is on internet.

I am not sure if the DNS server is also needs to be added or not?

---

