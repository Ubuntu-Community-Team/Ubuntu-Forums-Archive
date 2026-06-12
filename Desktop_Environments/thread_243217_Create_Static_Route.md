---
title: "Create Static Route?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ddmeredith on 2006-08-24
I'm not sure if this is the right forum for this - I'm a bit new to forums (sp. - fora?).  

I recently set up Ubuntu Server 6.06 Dapper Drake as a router for my network.  I set up Linux Firewall through Webmin, BIND DNS, and DHCP server.  I then used vpnc to connect to a Cisco VPN concentrator.  I can ping IP's on the inside the corporate network using my Linux box, and I can ping the remote gateway (192.168.1.214) from the other computers behind my Linux box, but I cannot ping other computers (i.e., the DNS server, the primary domain controller) except from the Linux box.  

I set up a route with the command, "sudo ip route add 192.168.1.0/24 via 192.168.1.214 dev tun0", but that does not seem to help the other computers.  I'm almost there to making my Ubuntu box a VPN gateway - does anyone have any suggestions?

---

