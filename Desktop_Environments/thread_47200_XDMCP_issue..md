---
title: "XDMCP issue."
date: 2005-07-07
forum: Desktop Environments
---

### Post by Quentusrex on 2005-07-07
I have successfully installed the LTSP 4.1 on Ubuntu 5.04. It is able to PXE boot all clients, and everything... except... When I am suppose to get the XDMCP login screen all I see is the crossed thatched background. And it just sits here. There is no login prompt, nor anything else... 

Thanks ahead of time for the help.


It might be that somehow port 177 is blocked, but I'm not sure. The clients where able to download the PXE image and everything else...

---

### Post by JLTB on 2005-07-08
Hi Quentusrex,

Slightly different issue, but I have tried to get tightvnc working with kdm and xdmcp at least 3 times with the same problem (following the gentoo wiki tutorial and others).  Symptoms of my problem are nmap returning 'closed|filtered' for port 177 on UDP (xdmcp uses udp).

Basically it appears as though something is blocking the port, it's not a firewall ... .i've gone down that alley.

This problem has plauged me on all debian based distros I have tried :(.

The only solution I have ever found is to use GDM instead of KDM (that worked on debian).  I haven't tried it on ubuntu (i use kubuntu), but it's worth a shot.

good luck!

---

