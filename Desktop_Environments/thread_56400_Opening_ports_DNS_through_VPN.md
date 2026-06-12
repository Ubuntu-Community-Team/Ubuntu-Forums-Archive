---
title: "Opening ports: DNS through VPN"
date: 2005-08-12
forum: Desktop Environments
---

### Post by jrb114 on 2005-08-12
Hi,

I'm connected to my school network through at pptp connection and I've set it up so that all traffic to xxx.xxx.0.0/16 goes through the VPN connection (which is set up as interface ppp0) and all other traffic goes via eth0 through the default gateway. I need to access the school network to connect to a license server.

I'm using Firestarter to control the firewall (sorry, I don't know very much/anything about iptables :(, help appreciated!), and the crunch is this... When I have the firewall enabled, and I connect to the VPN, I lose all DNS resolution (both internal and external). /etc/resolv.conf has been updated to the school's DNS, and I've tried (using Firestarter) to open port 53 for DNS to "everyone" and to the DNS IPs (in the external xxx.xxx.xxx.xxx rather than 192.168.100.x form, since I don't know their internal addresses - do I need them?).

With the firewall disabled though, I get full functionality and the license server behaves normally. Is there a better (or at least simpler) way to do this?

Can anybody help please?

Thanks

---

### Post by cwaldbieser on 2005-08-12
[QUOTE=jrb114]Hi,

I'm connected to my school network through at pptp connection and I've set it up so that all traffic to xxx.xxx.0.0/16 goes through the VPN connection (which is set up as interface ppp0) and all other traffic goes via eth0 through the default gateway. I need to access the school network to connect to a license server.

I'm using Firestarter to control the firewall (sorry, I don't know very much/anything about iptables :(, help appreciated!), and the crunch is this... When I have the firewall enabled, and I connect to the VPN, I lose all DNS resolution (both internal and external). /etc/resolv.conf has been updated to the school's DNS, and I've tried (using Firestarter) to open port 53 for DNS to "everyone" and to the DNS IPs (in the external xxx.xxx.xxx.xxx rather than 192.168.100.x form, since I don't know their internal addresses - do I need them?).

With the firewall disabled though, I get full functionality and the license server behaves normally. Is there a better (or at least simpler) way to do this?

Can anybody help please?

Thanks[/QUOTE]

I think firestarter's web site has some info about a workaround for problems with VPNs.  They are supposed to come out with a support for this in a later version.

---

