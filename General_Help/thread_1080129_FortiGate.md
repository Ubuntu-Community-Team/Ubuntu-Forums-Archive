---
title: "FortiGate"
date: 2009-02-25
forum: General Help
---

### Post by SickOfMS on 2009-02-25
Hi

Im running Ubuntu 8.10 and need to connect to a FortiGate server. How can I establish a vpn connection to this server from Ubuntu?

---

### Post by Joshonekenobi on 2009-03-16
I am trying to accomplish the same thing. 

Which Fortigate do you have ?

---

### Post by delog on 2009-04-20
I need to connect fortigate SSL VPN too. I tried to use IES4linux. But it did not work for fortigate. I need help.

---

### Post by CNLiberal on 2009-07-20
Has anyone gotten this to work?  I'm running Ubuntu 9.04 x64.

Jim

---

### Post by white8785 on 2009-07-23
I'm looking for a solution for this as well.

---

### Post by dcstar on 2009-07-23
> **white8785 said:**
> I'm looking for a solution for this as well.

Doesn't the basic VPNC package work?

---

### Post by CNLiberal on 2009-07-23
I was able to find a FortiGate linux program.  It was able to connect to my Fortigate 100 firewall.  However, it didn't create the static routes that would allow me to connect to the devices in that network.  Once I created the static routes, I was able to connect.  The name of the package was:

forticlientsslvpn_linux_4.0.2010.tar.gz

I'd much rather use something else.  The VPN client uses an SSL cert.  I don't know the password associated with the cert is.  If I did, I could probably use OpenVPN.

---

