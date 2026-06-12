---
title: "Getting a static IP for a network printer"
date: 2009-02-25
forum: General Help
---

### Post by Mooseknuckle on 2009-02-25
Hello ... I have an HP laserjet 2800 that I connect to.   When I add it through the printer admin interface, it works just fine.   Hp-lip detects it and all is grand.

However, it seems to assign it a static IP address, like 192.168.0.3.  What eventually happens is that when I power it off, and then a device like my G1 phone connects to the wireless network, and my router sees that 0.3 is available, and assigns it to my phone.   Now, I power my printer back on (hardwired to the router), and it gets assigned 192.168.0.4, and when I try to print to my already configured printer, it tries 0.3, and of course no printer is found.   What I end up having to do pretty much every time I print is delete, and readd the printer.

This is getting really old.   Is there an easy fix?

Thanks in advance!!!

---

### Post by moody_mark on 2009-02-25
Hi, you could try configuring your router to hand out dynamic addresses from say 192.168.0.16 through to 192.168.0.254, and then leave 192.168.0.1 through to 192.168.0.15 for static addresses which you can assign your printer to.

---

### Post by edu1962 on 2009-02-25
Hello, can't you enable DHCP Reservation on your router ? That did the trick for me. ;)

---

### Post by Iowan on 2009-02-25
Beaten to the punch - again.  Your router should be able to set up "static leases" (AKA "fixed" or "reserved" addresses) based on MAC Address.  This address should be in the subnet, but outside the DHCP address pool.  The printer can be set to get address via DHCP, but will always be assigned the same one.

---

### Post by sgosnell on 2009-02-25
Some routers won't do that, but will let you set the lease time as 'forever'.  Setting static IP addresses is done on the router, but the exact method depends on the router.  You can access it through firefox, and the IP of the router is usually 192.168.1.1, or 192.168.2.1, or some variation of these, from 0 through 2 most of the time.  You may have to try a few variations.

---

