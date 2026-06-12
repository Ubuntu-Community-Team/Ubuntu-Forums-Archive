---
title: "cannot ssh to a box on my lan unless my cable modem is on!"
date: 2009-01-16
forum: Desktop Environments
---

### Post by graysky on 2009-01-16
Really odd... I can't ssh or connect via VNC to another box on my LAN unless my cable modem is on.  If I try, the command just hangs there.  I tried connecting to both the host name and the IP of the box - neither of which works without the cable modem on.  Thoughts?

---

### Post by skern03 on 2009-01-16
> **graysky said:**
> Really odd... I can't ssh or connect via VNC to another box on my LAN unless my cable modem is on.  If I try, the command just hangs there.  I tried connecting to both the host name and the IP of the box - neither of which works without the cable modem on.  Thoughts?
It would be helpful if you described the rest of your network. For example, I have a cable modem that I connect to a wired/wireless Linksys cable router. The router serves DHCP addresses, and provides a firewall. If memory serves correctly, the modem is 192.168.1.0, and the router is 192.168.1.1. If I open the router with [http://192.168.1.1](http://192.168.1.1), I get an Admin window that shows the DHCP table among other things.

Is this anything like what you have?

---

### Post by graysky on 2009-01-17
Yes, here is my network architecture:

PC <--> Gigalan switch <--> Router <--> Cable modem

Here is my /etc/network/interfaces
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp

iface eth1 inet static
address 192.168.0.9
network 192.168.0.0
netmask 255.255.255.0
broadcast       192.168.0.255
gateway 192.168.0.1
mtu     4000
```

---

### Post by skern03 on 2009-01-17
> **graysky said:**
> Yes, here is my network architecture:

PC <--> Gigalan switch <--> Router <--> Cable modem

Here is my /etc/network/interfaces
# The primary network interface
auto eth1
#iface eth1 inet dhcp
iface eth1 inet static
address 192.168.0.9
network 192.168.0.0
gateway 192.168.0.1
mtu     4000[/code]

What version of Ubuntu? In 8.10, DHCP works pretty well; in earlier versions than 8.x, I had to use static IP addresses. In any case, switching to DHCP for your network probably won't fix your issue. 

You listed three physical devices in the route to your PC: cable modem, router and gigalan switch. Are all of your PCs connected to the Gigalan switch? What are the IP addresses of each?

Your gateway should be the device to which you connect your PCs on the LAN, right? That ought to be the router or the switch.

You said you can't SSH to a box; can you ping any of the boxes on your LAN when your cable modem is off?

---

### Post by graysky on 2009-01-17
> **skern03 said:**
> What version of Ubuntu? In 8.10, DHCP works pretty well; in earlier versions than 8.x, I had to use static IP addresses. In any case, switching to DHCP for your network probably won't fix your issue. 

You listed three physical devices in the route to your PC: cable modem, router and gigalan switch. Are all of your PCs connected to the Gigalan switch? What are the IP addresses of each?

Your gateway should be the device to which you connect your PCs on the LAN, right? That ought to be the router or the switch.

You said you can't SSH to a box; can you ping any of the boxes on your LAN when your cable modem is off?

Running 8.10 (amd64).  I do it via static so I can use 4000 mtu size.

All PCs are connected to the switch.  The IP addresses are all statically assigned from 192.168.0.9 up to .12

No, can't ping, ssh, vnc, etc. to the boxes when the cable modem is off.

---

### Post by skern03 on 2009-01-17
> **graysky said:**
> Running 8.10 (amd64).  I do it via static so I can use 4000 mtu size.

All PCs are connected to the switch.  The IP addresses are all statically assigned from 192.168.0.9 up to .12

No, can't ping, ssh, vnc, etc. to the boxes when the cable modem is off.

Your setup and mine are virtually identical, with the exception of static IP addresses, so I ran a test by powering down my cable modem. I then pinged a network attached printer -- it's attached through the wall, not wireless. The ping was successful.

My bet is that the gateway address you have may not be pointing to your switch. 

Another possibility which I'd classify as remote, since your system works when the modem is on... The first time I set up a cable router and a cable modem, they both tried to grab the same IP (192.168.1.0). Of course, nothing worked.

Do you know the IP addresses of all three devices?

---

### Post by The Cog on 2009-01-18
How long dod you wait? I wonder if it will succeed in connecting after a few minuites pause. If it turns out that a 1 or 3 minuite wait is needed, perhaps the destination machinne is trying to perform a DNS lookuup to identifying the calling machine. Maybe it's waiting for the DNS lookup reply which doesn't arrive when the modem is off.

---

