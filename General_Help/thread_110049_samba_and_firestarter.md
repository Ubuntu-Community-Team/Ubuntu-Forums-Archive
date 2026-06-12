---
title: "samba and firestarter"
date: 2005-12-29
forum: General Help
---

### Post by chocolatetoothpaste on 2005-12-29
I have a server that is a router/firewall running Firestarter.  I am now trying to setup it up as a file server.  So I enabled file sharing in the system menu.  The server won't show up in the network neighborhood.  Could firestarter be blocking this?  I have another ubuntu box that is a workstation and it shares files quite easily.  No firestarter on that machine.  any thoughts?

---

### Post by Suger on 2005-12-30
Yes, you need to allow incoming connections for Samba (it has a predefined policy in firestarter...), which you can restrict to your LAN (IPs should be something like 192.168.0.1/24 or /192.168.1.1/24).

---

### Post by chocolatetoothpaste on 2005-12-30
How can I specify a range of IP's?  Because my server uses dhcp.

---

### Post by Suger on 2005-12-31
IPs should be something like 192.168.0.1/24 or /192.168.1.1/24

---

