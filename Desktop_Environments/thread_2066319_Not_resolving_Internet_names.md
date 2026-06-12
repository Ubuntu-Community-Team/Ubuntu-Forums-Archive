---
title: "Not resolving Internet names"
date: 2012-10-04
forum: Desktop Environments
---

### Post by jimerman on 2012-10-04
I am running Ubuntu 12.04 in a VM, NIC is bridged.  This machine is a DHCP/DNS server using DNSMASQ.  The network has 3 DNS servers:

The Linux machine, 192.168.15.3
A special DNS 192.168.15.2
The router to the external Internet, 192.168.1.254

In the Ethernet connection, I configured static IP and settings, gateway, and the 3 DNS with commas in between, no spaces.

Whenever I go to Firefox, it won't open any Internet web sites, only intranet.  When I do NSLOOKUP, for example "nslookup www.google.com" I get the response "www.google.com.MYDOMAIN.COM not found" - if I debug nslookup, it tries the entered address first, fails, appends my domain, and fails again.  Why when it fails doesn't it try the next DNS, and the next, until it gets the address?

It also appears to only look at 127.0.0.1:53 for dns resolution; why doesn't it fail over to the other DNS?  I changed the DNS server list in Edit Connections, to only the external gateway, and it still doesn't resolve.

---

### Post by jimerman on 2012-10-04
Pretty bad when you answer your own question!  [http://askubuntu.com/questions/131342/problems-with-dnsmasq-in-ubuntu-12-04](http://askubuntu.com/questions/131342/problems-with-dnsmasq-in-ubuntu-12-04)

dnsmasq was disabled in Network Manager, I enabled and rebooted, that did it.

---

