---
title: "dhcp gives wrong DNS"
date: 2005-12-29
forum: General Help
---

### Post by chocolatetoothpaste on 2005-12-29
I have one ubuntu box that acts as a router and is a dhcp server, and 2 xp machines and a ubuntu box that connect to the internet through it.  The problem is, I think the DHCP machine is giving my other ubuntu workstation the wrong DNS.  It gives these 2: 192.168.0.1 which is my DSL modem, and 205.171.3.65, which is a proper DNS server ip address.  Now, in place of the DSL ip, it is supposed to assign 205.171.2.65, and I have to change it EVERY time I turn on my computer.  How do I fix it to be permanent?  Is it a problem with my server? I kind of think it is.

---

### Post by tlc on 2005-12-29
This may or may not help, but my Netgear router was playing silly buggers with my DNS settings when acting as a DHCP server, so I deactivated DHCP on the router, gave it all the correct static IP info, and found that my /etc/resolv.conf file was still being overwritten by gibberish every boot. I suspect it was the dhcpd daemon, but I didn't know how to turn that off, so the quick and dirty fix I used was:
```
sudo nano /etc/resolv.conf
```
...entered the correct DNS servers for my ISP...
```
nameserver 62.24.168.9
nameserver 62.24.168.10
```
...then did a...
```
sudo chattr +i /etc/resolv.conf
```
...to lock the file.

(You can unlock it with chattr -i. Or maybe the other way around, I can't remember, but you get the idea.)

---

### Post by chocolatetoothpaste on 2005-12-29
Also, my server does the same thing.  It changes one of the DNS entries on bootup.  So how can I fix the problem?

---

### Post by chocolatetoothpaste on 2005-12-29
Cool I will try it.  Thanks.

---

