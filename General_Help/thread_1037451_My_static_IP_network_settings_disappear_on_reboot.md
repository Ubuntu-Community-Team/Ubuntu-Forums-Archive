---
title: "My static IP network settings disappear on reboot?"
date: 2009-01-11
forum: General Help
---

### Post by Linuxwho? on 2009-01-11
Hi all, I am sure it is something I am doing.  Ubuntu 8.04 desktop.  I have to reenter my network setting every time I reboot!  What am I doing wrong?  Thanks.

---

### Post by hotweiss on 2009-01-11
> **Linuxwho? said:**
> Hi all, I am sure it is something I am doing.  Ubuntu 8.04 desktop.  I have to reenter my network setting every time I reboot!  What am I doing wrong?  Thanks.

It's best to set-up your static IP on the router...

---

### Post by Linuxwho? on 2009-01-11
> **hotweiss said:**
> It's best to set-up your static IP on the router...

Sorry, I dont know what that means.  Static on router and dhcp on server?  I want a static on server.  Thanks.

---

### Post by _sleeper on 2009-01-11
could you be more specific?

if i understand well, i think that you should give on your router a static ip for your server and disable dhcp, if that's the case.

---

### Post by Linuxwho? on 2009-01-11
> **_sleeper said:**
> could you be more specific?

if i understand well, i think that you should give on your router a static ip for your server and disable dhcp, if that's the case.

Sure.  I do not use DHCP at all.

All I want to do is give my ubuntu server a static IP.   Every time I do this I can get out to the net.  However, When I reboot, my ip settings do not save. I do not want to have to keep retyping my ip settings in every time I reboot the server.

---

### Post by Iowan on 2009-01-11
You could either set your DHCP server (router?) to issue a static lease (based on MAC address) if it is capable, or you can set up a static address in */etc/network/interfaces*.  Hardy (8.04) didn't seem to have the NM bug. A sample file from one of my machines:```
auto lo
iface lo inet loopback
 
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```It's possible the network and broadcast lines are unnecessary. Are you required to use a static address, or DHCP doesn't work?

---

### Post by Yellow Pasque on 2009-01-11
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by Linuxwho? on 2009-01-11
> **Iowan said:**
> You could either set your DHCP server (router?) to issue a static lease (based on MAC address) if it is capable, or you can set up a static address in */etc/network/interfaces*.  Hardy (8.04) didn't seem to have the NM bug. A sample file from one of my machines:```
auto lo
iface lo inet loopback
 
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```It's possible the network and broadcast lines are unnecessary. Are you required to use a static address, or DHCP doesn't work?

Thanks.  I do not have or want DHCP.  So this is a bug?  My last install of ubuntu was not erasing its network setting on reboot.

---

### Post by hotweiss on 2009-01-11
> **_sleeper said:**
> could you be more specific?

if i understand well, i think that you should give on your router a static ip for your server and disable dhcp, if that's the case.

With new routers you don't even have to disable dhcp when you create a static IP.

---

### Post by Iowan on 2009-01-11
It's been a few versions ago, but seems like there was a thread (or two?) where **dhclient** assigned a DHCP address to the interface - despite being set up for static address. Does your machine get an IP address on reboot - or is that why you must manually re-enter settings?

---

### Post by _sleeper on 2009-01-12
so did you have any luck?

---

### Post by Caraibes on 2009-01-12
This is a bug in 8.10, it wasn't so in 8.04... 

There are many workarounds posted all around the web, but so far, none has been "nice & clean"...

I just have 2 connection, the default one that won't go away, and the "good" one, with the static IP. At first boot in the morning, I just select the "good" one... (click on the network icon)

---

### Post by DeMus on 2009-01-12
> **Linuxwho? said:**
> Hi all, I am sure it is something I am doing.  Ubuntu 8.04 desktop.  I have to reenter my network setting every time I reboot!  What am I doing wrong?  Thanks.

The IP number you type into Ubuntu is it a number which your router accepts as a static number? I mean, I know routers with DHCP who use let's say nrs. 1 to 50 (192.168.1.1~192.168.1.50) and from 51 at the end it is a static number.
How about your router, does it have the same? Read the manual of the router to find out.

DeMus

---

### Post by Linuxwho? on 2009-01-14
> **DeMus said:**
> The IP number you type into Ubuntu is it a number which your router accepts as a static number? I mean, I know routers with DHCP who use let's say nrs. 1 to 50 (192.168.1.1~192.168.1.50) and from 51 at the end it is a static number.
How about your router, does it have the same? Read the manual of the router to find out.

DeMus

Thanks but I am not using a router for anything.  I am simply static IP'ing my machine.  We do not have or use DHCP. ):P

Yes your comments are very helpful bc I am so new to Linux I learn something from almost any comment.  Caraibes nailed it for me though.  Thank you one and all!!  :D

Shoot..I dont see an icon to thank anyone. :confused:

---

