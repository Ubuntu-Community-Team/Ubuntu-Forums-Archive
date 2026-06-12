---
title: "xbox tunneling?"
date: 2006-11-19
forum: Gaming &amp; Leisure
---

### Post by darkenedday on 2006-11-19
In windows I used neXBC to connect to xbox connect (i have i regular old xbox not a 360) I can't seem to find a linux program that will allow me to do this my current set up is I have two ethernet cards in one PC one going to my router, the other to the xbox, anyone know of any good linux tunneling programs for the xbox?

---

### Post by woedend on 2006-11-19
i've written on this subject numerous times as have others, just search around.
this isa good starting point
[http://www.ubuntuforums.org/showthread.php?t=204295&highlight=firestarter+bridge+card+static](http://www.ubuntuforums.org/showthread.php?t=204295&highlight=firestarter+bridge+card+static)

---

### Post by darkenedday on 2006-11-19
I did what you said in the post, for bridging, i tried firestarter and personally didn't like that option

but this is the output I got when I attempted to do ifup br0

mike@Apollo:~$ ifup br0
/etc/network/interfaces:30: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by darkenedday on 2006-11-19
If it helps any this is what my interfaces file looks like
 
 
 
 auto lo
 iface lo inet loopback
 address 127.0.0.1
 netmask 255.0.0.0
 
 auto eth0
 iface eth0 inet dhcp
 
 auto eth1
 iface eth1 inet dhcp
 
 auto eth2
 iface eth2 inet static
 address 192.168.1.113
 netmask 255.255.255.0
 
 auto ath0
 iface ath0 inet dhcp
 
 auto wlan0
 iface wlan0 inet dhcp
 
 
 iface eth3 inet static
 address 192.168.1.111
 netmask 255.255.255.0
 
 auto eth3
 
 
 iface br0 
 bridge_ports all

---

### Post by nalmeth on 2006-11-19
I use XLIL for playing on the Xlink Kai network.

It's java based, and XLIL is the linux client. Only problem was, people are pretty much only playing Halo 2, with the odd exceptions. 

Who knows, maybe there are more players online now?

---

### Post by woedend on 2006-11-19
its hard to tell what line 30 is but im guessing its bridge_ports all...is that correct?
make sure bridge-utils is installed, and change "all" to the 2 cards.

for example, if eth0 takes internet in, and eth1 goes to the xbox, use
bridge_ports eth0 eth1
let me know how that works

but i just realized you weren't trying to just get internet but to connect to xbc instead of live, so this wont be of much help other than letting the xbox get internet access.  id try the above post...ive never messed with it.

---

### Post by darkenedday on 2006-11-19
no, the line is "iface br0" it says there are too few parameters for an iface line

exe: iface eth1 inet dhcp

3 paramaters, i'm guessing br0 has more options I need to define?

---

### Post by woedend on 2006-11-19
oops, right.  try iface br0 inet dhcp
assuming you use dhcp, otherwise it looks like you would know how to do it statically.
let me know.

---

### Post by darkenedday on 2006-11-19
ok so that worked howeverit seems to be just running endlessly in a terminal is that supposed to happen? and now if i just go to another pc connected to mine with crossover cable it should be able to access the internet

edit:
the DHCP discover took lnger then expected it stops eventually, however it makes it impossible to connect to the internet when i put my internet card (eth1) in, am I not supposed to? If I take out my internet card i get this output when i run ifup br0

mike@Apollo:~$ sudo ifup br0

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
There is already a pid file /var/run/dhclient.br0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:10:4b:87:fa:96
Sending on   LPF/br0/00:10:4b:87:fa:96
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


also I have eth0 eth2 and eth3 currently set to static I'm guessing I should switch them to dhcp? ( these cards are connected to other boxes to allow those boxes internet access, does that work with the cards set to dhcp? or do they need to be static for internet connection sharing and simply leave the other cards in the other boxes at dhcp?

---

### Post by woedend on 2006-11-19
it wont work with dhcp unless you have a dhcp server running...ive never went this far with dhcp.  i set them all up statically regardless.  which cards do what in your setup?

---

