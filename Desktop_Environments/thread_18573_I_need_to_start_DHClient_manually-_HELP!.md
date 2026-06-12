---
title: "I need to start DHClient manually- HELP!"
date: 2005-03-07
forum: Desktop Environments
---

### Post by mistermax on 2005-03-07
I need to start DHClient manually in order to get a connection to my broadband router; is there something I need to do so it will get an IP automatically?

Interestingly it keeps saying on start up that it couldn't find my hostname "dosser" in /etc/hosts

---

### Post by alastair on 2005-03-07
You need to look at the file :

/etc/network/interfaces

man interfaces

e.g.

iface eth0 inet dhcp

See also :

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-high-dhcp](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-high-dhcp)

---

### Post by mistermax on 2005-03-13
[QUOTE=alastair]You need to look at the file :

/etc/network/interfaces

man interfaces

e.g.

iface eth0 inet dhcp

See also :

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-high-dhcp](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html#s-high-dhcp)[/QUOTE]


Still unclear on this; I have had a look at the man page and can see that I need to set up my mappings.

Currently the file looks like this:

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
broadcast 127.255.255.255
network 127.0.0.0

auto lo

iface eth0 inet dhcp
name Ethernet LAN card

auto eth0

this looks like my machine currently looks for a DHCP address on startup?

---

### Post by mistermax on 2005-03-16
Okay worked this one out myself with my 2 MHz brain!

I have an ASUS motherboard with on-board everything (Sound, Graphics, NIC)

When Ubuntu boots, even although I set up the 3 COm card I have as my interface; the main one according to Ubutnu was the Nvidia/Asus onboard thing.....

So there you go-

always check how many cards you have

if you have something looking like this:

[B]auto lo

iface eth0 inet dhcp
name Ethernet LAN card

auto eth0[/B] 

then swap change all mentions of eth0 to eth1

*If you are far more guru than me and this is boring reading please ignore, but I'm trying to pass on early-user experiences to other starters. *

---

