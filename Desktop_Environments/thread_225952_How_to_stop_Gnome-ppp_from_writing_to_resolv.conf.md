---
title: "How to stop Gnome-ppp from writing to resolv.conf?"
date: 2006-07-30
forum: Desktop Environments
---

### Post by rogblake on 2006-07-30
I'm on a dialup internet line, using Gnome-PPP for the connection. I also have bind set up as a local caching DNS server, so my /etc/resolv.conf file contains the line "nameserver 127.0.0.1" and my ISP's name servers are set up as forwarders in the bind config.

The problem I'm having is that Gnome-PPP insists on over-writing resolv.conf when it connects. I've tried enabling the "Manual DNS" option in its settings, but that does not help. Since Gnome-PPP is a front-end for wvdial, I've also tried manually editing the ~/.wvdialrc config file with the desired DNS settings but that file also gets over-written by Gnome-PPP. I've even tried changing the permissions on resolv.conf to make it a read-only file, but it still gets clobbered!

Anyone know how to get Gnome-PPP to keep "hands off" my DNS settings when it connects?

---

### Post by rogblake on 2006-07-30
I figured it out with a little more digging. I should have realized that the culprit was actually pppd -- I removed the scripts in /etc/ppp/ip-up.d that diddled with the resolv.conf file, and that took care of the problem. D'oh!

---

