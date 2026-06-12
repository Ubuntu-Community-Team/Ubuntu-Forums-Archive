---
title: "Need Help With NAT!"
date: 2009-06-05
forum: General Help
---

### Post by pro003 on 2009-06-05
Ok. I've been struggling with this for hours and can't get it work.
Of all the things I've done in Ubuntu, the smallest attention was payed to NAT or internet connection sharing.
Here's the thing. 
1. One desktop with eth0 and wlan0 (d-link) under Ubuntu jaunty
2. One laptop with eth0 under Windows Vista Ultimate x64

I want to to share my internet (pppoe through wlan0 ap) connection with laptop which is connected to my desktop through ethernet cable.

First of all I can't seem to get it up eth0, because I selected as my primary device to be wlan0 (maybe am wrong) but I can't connect to laptop through eth0 no matter what. I managed so far to connect to internet on desktop through wlan0 using pppoe protocol. Now, what should I do?

Anyone, I'd appreciate no links and stuff, I need direct help. I've been googleing for all afternoon and still with no solution.

---

### Post by mocoloco on 2009-06-05
Here's how I do it.  Host machine is connected with eth0 and sharing out on eth1.

```
#!/bin/bash

echo "Setting ip for eth1.."
sudo ifconfig -v eth1 192.168.20.1
echo "..done."
sudo iptables -vA FORWARD -i eth0 -o eth1 -s 192.168.20.0/24 -m state --state NEW -j ACCEPT
sudo iptables -vA FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -vA POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```


Since I only use it off and on I just run that script manually every time I need it, and never looked at setting it permanently.
Also decided not to set up DHCP, so I just have a static IP and manual DNS settings on the other machines it shares to.

My source for this was Ubuntu's community page on [Internet Connection Sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing").  You say you didn't want links but that page explains it much better than I could :).

---

### Post by uupreti on 2009-06-05
If you wanna do with bridge then may be it will help you.

Briding is probably simple technique to share internet.

Simply follow these steps

1. Install bridge-utils using synaptic
```
sudo aptitude install bridge-utils
```2. Then stop your networking and do following

```
1. sudo /etc/init.d/networking stop
2. sudo nano /etc/network/interfaces

Replace with following

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 wlan0

```Save the change and resstart the network
```
sudo /etc/init.d/networking start
```

---

### Post by pro003 on 2009-06-05
thanks guys, I'll be taking care of this right now. Bridge utils seem like nice idea, since i've tried manipulating with iptables, but that is far complicated than many people think. I've used a couple of top positioned google searched sites with threads and howto's about nat and routing, and didn't make it.

If I make it now, I'll post back.

thanks.

---

### Post by fragos on 2009-06-05
IMHO the simplest way is buy a wireless router -- can be found for less than $20 if you look. As well as WiFi access they normally have a 4 port ethernet hub. No special configuration is required unless your ISP will only connect to a particular MAC. In that case clone your PC's MAC in the router. Connect the router to your cable/DSL modem and then plug your PC's Ethernet port into the routers hub.

---

