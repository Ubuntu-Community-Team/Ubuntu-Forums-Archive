---
title: "Some applications not accessing internet."
date: 2006-08-19
forum: Desktop Environments
---

### Post by kircher on 2006-08-19
Hi, I'm a relative newbie to ubuntu and linux (have been using for just over a week). My experience has been great. I had a few minor problems to start with, but I sorted them out. I have been trying to fix something though which I can't work out. I connect to the internet via a 4 port router, which has 2 windows xp machines connected to it, plus my ubuntu machine. I set myself a static ip by editing /etc/network/interfaces as follows: -
 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

By this, my ip should be 192.168.1.6. I'm having trouble getting azureus to connect to anything. I set azureus to use port 50000, and forwarded this port in my router in the same way I used to when I was using windows XP. Azureus just does not connect at all. The other 2 pcs on this network do not have static ips, because I didn't think that they should need it (they didn't when I used xp). Does anybody know anything about this?

---

### Post by TripleE on 2006-08-19
It is not a good idea to set a static IP in the DHCP range for the router.  I set my netgear router to reserve a DHCP address for my MAC address for my computer, but if you want to setup a static IP address.  You may want to go into your router and have the DHCP range start at 192.168.1.11 to minimize future problems.

As far as the port 50000, could your ISP be blocking that port?  I know that some do.  If it worked on your Windows box it should work on your Linux box too.  I have port 30000 forwarded on my and it works great.

---

### Post by kircher on 2006-08-20
still no success. I designated myself an IP which would never be used by the other 2 computers. They will only use 192.168.1.2 and 192.168.1.3. I forwarded everything properly, the way I used to in XP. It can't be the router. Ubuntu must be doing something, blocking the ports somehow or something else, and I have no idea what. Has anyone ever had an experience like this? I can browse using firefox, connect to amsn without changing anything, use frostwire to download. My ISP I know doesn't block the port I'm using because I've used it before with windows. As soon as I get this all set up I can delete my windows partition forever which I am looking forward to. Initially I thought that maybe when I set a static ip in ubuntu it wasn't actually working properly, but I've tested things and pinged myself from the router, and I definately do have the IP I set, plus ifconfig in a terminal confirms all of this anyway.

---

### Post by kircher on 2006-08-20
Just to clarify, I don't run a software firewall in ubuntu either.

---

### Post by kircher on 2006-08-20
anyone?

---

### Post by kircher on 2006-08-21
ok, I've mostly sorted this problem out myself anyway.

---

### Post by nexus_6 on 2006-08-22
i am having a similar problem, how did you solve yours?

---

