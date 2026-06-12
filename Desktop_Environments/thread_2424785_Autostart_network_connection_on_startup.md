---
title: "Autostart network connection on startup"
date: 2019-08-14
forum: Desktop Environments
---

### Post by sy-kalhor on 2019-08-14
Hi all. I am using Lubuntu 19.04 x64. My PC has 2 network cards and I need to connect to both network at startup. 

I am not familiar with Lubuntu's network manager. When I right click on the network icon in the taskbar and choose the "Edit Connections..."  I get into a terminal application. I see both of my Ethernet connections there and I have enabled "Automatically connect"  checkbox for both of them. 

But when the PC starts only one of them is connected and I have to manually connect to the other one at each startup (by left clicking on the network icon on the taskbar and selecting the other Ethernet device"

How can I force both connections to connect on startup. Also is it possible to say which of them to be connected first (I need the priority too).

---

### Post by SeijiSensei on 2019-08-14
Are they connected to separate routers in separate subnets?  Does the second router provide DHCP?  Can you use a static IP instead?

The machine will connect eth0 (or perhaps eno0 or enp1s0) before eth1/eno1/enp1s1.  I'm not sure why the order matters though.  I've never had a situation with multiple adapters where that would matter.

---

### Post by sy-kalhor on 2019-08-16
So the story is this: One of the Ethernet ports is working normally and connects to a router and I can connect to internet with it no problem. The other one is connected directly to another PC and I use it to SSH into the other PC.

When my main PC starts, the Ethernet port that used to connect to another PC is active but the one that I use to connect to internet is not activated on startup and I have to do that manually. Here is the output of "ip addr show". As you can guess by the IP addresses...the "ens3" is used to connect to another PC while the "enp2s0f0" is connecting me to internet

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether ac:87:a3:16:1c:07 brd ff:ff:ff:ff:ff:ff
    inet 10.42.0.1/24 brd 10.42.0.255 scope global noprefixroute ens3
       valid_lft forever preferred_lft forever
    inet6 fe80::3aff:3f42:fcca:446c/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: enp2s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet xxx.xxx.xxx.xx/23 brd 134.109.21.255 scope global dynamic noprefixroute enp2s0f0
       valid_lft 86337sec preferred_lft 86337sec
    inet6 xxxx::xxxxx:xxxxx:xxxxx:xxxx/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

---

