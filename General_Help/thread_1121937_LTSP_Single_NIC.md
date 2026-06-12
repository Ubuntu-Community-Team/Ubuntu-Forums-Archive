---
title: "LTSP Single NIC"
date: 2009-04-10
forum: General Help
---

### Post by roodavis on 2009-04-10
I want to setup a test LTSP environment at home.  Is it possible to set up an LTSP server on a machine with a single NIC?

I succeeded in installing Ubuntu Server 8.10 on a ppc Mac Mini, but building/installing the ltsp chroot fails.  I suspect it is because it can only find one NIC. So before I get to far into the troubleshooting I thought I should ask the community.

Thanks and have a great day.

Rick Davis

---

### Post by shel-hall on 2009-07-05
> **roodavis said:**
> I want to setup a test LTSP environment at home.  Is it possible to set up an LTSP server on a machine with a single NIC?

Yep.  It just requires a little fiddling with both the server setup and with your network setup.

> I succeeded in installing Ubuntu Server 8.10 on a ppc Mac Mini, but building/installing the ltsp chroot fails.  I suspect it is because it can only find one NIC.

I've done this one time on one machine, so I'm no expert, but I doubt it's a single-NIC issue.

Here are the cogent parts of my original environment:

Network with DHCP served by DSL router.
Old Dell computer with one NIC and a clean HDD.

I did this (net, after much fiddling and googling):

Installed the LTSP system from the 9.04 Alternate CD.
Booted to the normal desktop.
Uninstalled NetworkManager
Edited the various files required (/etc/lstp/dhcpd.conf /etc/resolv.conf /etc/network/interfaces and so forth)
Turned off the DHCP server in the DSL router (can't have two DHCP servers!)
Rebooted

Et, as they say, voila.

-Shel

---

