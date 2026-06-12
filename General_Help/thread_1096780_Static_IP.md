---
title: "Static IP"
date: 2009-03-15
forum: General Help
---

### Post by unplugged23 on 2009-03-15
Hey there, 

I was hoping someone could help me get my static ip figured out. I've been trying to set it up, but I'm a little confused. I can only find articles on converting a DHCP to static, but it appears that i have some wierd lo loopback. I have no idea what this means. when i go to edit my etc/network/interfaces file i get ```
auto lo
iface lo inet loopback

``` and when i type ipaddr i get ```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:07:e9:78:48:53 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.100/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::207:e9ff:fe78:4853/64 scope link 
       valid_lft forever preferred_lft forever
3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether ea:91:ea:e3:61:ec brd ff:ff:ff:ff:ff:ff

``` Can anyone help out with this?

---

### Post by heindsight on 2009-03-15
loopback is a logical network interface from your computer back to itself. You shouldn't change that.

I assume you're trying to set up static IP on your ethernet interface (eth0)?

To do that, you have to add an entry for eth0 to /etc/network/interfaces. This entry should look something like:

```
iface eth0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.1

```
The first line says that eth0 is an IPv4 interface with static IP address.
The next lines give the IP address, the network mask and the default gateway address (specifying a gateway is optional, but if you want to be able to send traffic to addresses outside your local LAN over this interface then you should set gateway to the address of your gateway router).

You may also want to change the line that currently says:
```
auto lo
```
To:
```
auto lo eth0
```
To have eth0 automatically brought up at boot time.

You may also have to edit /etc/resolv.conf to add entries for your nameservers there.

see the manuals for the interfaces file:
```
man interfaces
```
and resolv.conf
```
man resolv.conf
```

Edit:
After you've added the entry to /etc/network/interfaces do:
```
sudo ifup eth0
```
to bring up eth0 and then do
```
ifconfig eth0
```
to see info about your interface.
You could also try testing it by trying to ping another address in your LAN, eg:
```
ping 10.0.0.1
```

---

### Post by unplugged23 on 2009-03-15
Cool thanks,

So just to clarify in a couple of things: should ```
iface eth0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.1
``` be added to or should it replace the /etc/network/interface file? also, should I copy and paste this code or will it need to be customized for my computer? if do how?
Thanks again for your help! :D

---

### Post by heindsight on 2009-03-15
> **unplugged23 said:**
> Cool thanks,

So just to clarify in a couple of things: should ```
iface eth0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.1
``` be added to or should it replace the /etc/network/interface file? also, should I copy and paste this code or will it need to be customized for my computer? if do how?
Thanks again for your help! :D

You have to add it to /etc/network/interfaces. You will need to change the IP address to the correct IP address for your network and you'll have to change the gateway address to the IP address of your gateway router.

---

