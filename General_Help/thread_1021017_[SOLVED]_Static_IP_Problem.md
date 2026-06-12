---
title: "[SOLVED] Static IP Problem"
date: 2008-12-24
forum: General Help
---

### Post by XFaisalX on 2008-12-24
Hey fella's.
I was trying to set up a static IP for Linux Ubuntu (Server Edition), but for some darn reason it doesn't work.
I followed a tutorial online till I came to the updating part.
I tried to connect to update but the connection just fails.
Could anyone help me out please?
I have interfaces set as:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

and hosts setup as:
```
127.0.0.1       localhost.localdomain   localhost
192.168.0.100   (My own name).(A name).com     (My own name)

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 

```

---

### Post by skippymo on 2008-12-24
in any environment i usually just make the reservation for my NIC to whatever, say you wanted to make your NIC 192.168.0.20 for bit torrents etc. go to your router / server and add that mac address to the reservation. that way you can manage it from that end instead of changing your pc(s) all the time.

just a suggestion.

---

### Post by skippymo on 2008-12-24
sorry just saw that you want it for your server.....nevermind. cheerio!

---

### Post by dcstar on 2008-12-25
> **XFaisalX said:**
> Hey fella's.
I was trying to set up a static IP for Linux Ubuntu (Server Edition), but for some darn reason it doesn't work.
I followed a tutorial online till I came to the updating part.
I tried to connect to update but the connection just fails.
Could anyone help me out please?
I have interfaces set as:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```
......


What is the address of your router, and what happens when you ping it?

---

### Post by zvacet on 2008-12-25
Maybe you will find [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3") helpful.

---

### Post by XFaisalX on 2008-12-25
I already followed that one, also the newer version.
But don't worry, I got my problem fixed already.
Just had a few things wrong in there, but it's fixed.
Now the only problem left is to get my teamspeak up.
I can ping google.com etc, the connections fine.
Ty for your help ^^

---

