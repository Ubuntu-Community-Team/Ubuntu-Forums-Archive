---
title: "ping ubuntu box from windows"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mattme on 2006-07-16
Hi y'all.

My problem: I cannot contact my ubuntu system by hostname from a networked windows PC. Only when addresses to its IP address will requests work. This goes for ping, http, samba.

There is a router in between, it assigns local IP's by DHCP.  I've followed common advice which is to edit /etc/dhcp3/dhclient.conf to send a hostname to the DHCP server (the router). Unfortunately, this won't update if I change my system hostname, but it did appear to work. In the router's http interface, it displays 192.168.0.3 as 'stivo', which is perfect.

**But the hostname is still not avaliable from windows. Help!** 
Do I need to set the windows computer to get the DHCP hostnames from the router or something? 

Thanks, Matt

---

### Post by philippe_carlo on 2006-07-16
Well, if your router has DNS functionality, you must make sure to
(1) register the hostname from the linux box (which you appear to be doing)
(2) use the router's ip as dns server in the windows box

Another way is to register the hostname and ip of the linux box in c:\windows\system32\drivers\etc\hosts on the windows box

---

### Post by ayoli on 2006-07-16
The 'another way' of registering hostname in windows hosts file may not be the right solution with dynamic IP attibuted by a dhcp.
regards.

---

### Post by philippe_carlo on 2006-07-16
Of course, in that case, you will need a static IP.

---

### Post by mattme on 2006-07-16
(2) use the router's ip as dns server in the windows box

Any idea where I set this? This could well be the problem, everything worked dandy on my old network, but then I installed a new router which is at 192.168.0.1 rather than 192.168.1.1 Thanks guys I'll go have a look in windows connections sometime.

---

### Post by ayoli on 2006-07-16
> **mattme said:**
> (2) use the router's ip as dns server in the windows box

Any idea where I set this? This could well be the problem, everything worked dandy on my old network, but then I installed a new router which is at 192.168.0.1 rather than 192.168.1.1 Thanks guys I'll go have a look in windows connections sometime.
in the network properties > tcp/ip properties (where you set ip) there is a field DNS where you put your router's ip.
regards.

---

