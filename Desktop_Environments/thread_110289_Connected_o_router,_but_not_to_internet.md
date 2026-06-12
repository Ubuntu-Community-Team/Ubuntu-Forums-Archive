---
title: "Connected o router, but not to internet"
date: 2005-12-30
forum: Desktop Environments
---

### Post by Paige on 2005-12-30
I installed Ubuntu today, and everything seems to work all right.
Almost that is. 

I can't connect to the internet.

I connect (via cable on an ethernet card) through a D-link Dl-542 router.
Router and ADSL modem both work fine, I have no problems connecting on my XP-macines. 

My Ubuntu 'puter can communicate with the router, but not access the internet.

I can ping mu router, but not the internet.
IP-adress is OK

So... What do I try next?

Please keep answers "simple" as I am a complete Linux newbie, though experienced in networking in Windows.

(Meaning I understand quite a lot, but haven't really found my way around the Ubuntu interface yet. ;) )

---

### Post by Paige on 2005-12-30
I think I may have posted this thread in the wrong forum.
Feel free to move it.

I wonder if this:
[http://ubuntuforums.org/showthread.php?t=109451&page=2](http://ubuntuforums.org/showthread.php?t=109451&page=2)
might be the right solution, but where do i fix it?

---

### Post by 0MG on 2005-12-30
are you pulling dhcp from the router or are you using a hardcoded IP? If you are hardcoded, you probably don't have a default gateway set up.

to check and see if you have a default gateway, go to a terminal and type: route

if you don't see a default gateway, you'll need to set one up.

to do that, go to a terminal and type: route add default gw 192.168.0.1 (or whatever your router is)

of course the easy way to do this is just to pull dhcp from your router. type: dhclient eth0 (or whatever interface you are using).

Good luck.

---

### Post by Paige on 2005-12-30
route -n gives this result:
> Kernel IP routing table
Destination 192.168.0.0
Gateway 0.0.0.0
Genmask 255.255.255.0
Flags U
Metric 0
Ref 0
Use 0
Iface eth2

Destination 192.168.0.0
Gateway 0.0.0.0
Genmask 255.255.255.0
Flags U
Metric 0
Ref 0
Use 0
Iface eth0

Destination 0.0.0.0
Gateway 192.168.0.1
Genmask 0.0.0.0
Flags Ug
Metric 0
Ref 0
Use 0
Iface eth0

---

