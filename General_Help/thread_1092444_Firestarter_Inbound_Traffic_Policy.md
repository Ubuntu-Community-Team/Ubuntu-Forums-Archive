---
title: "Firestarter Inbound Traffic Policy"
date: 2009-03-10
forum: General Help
---

### Post by tommyperkins on 2009-03-10
Hi,

I've been working on my Ubuntu Server for about a week now and got it configured through reading these forums but I'm a little stuck with setting up the Inbound Traffic Policy in Firestarter.

The problem I'm having is that I need to enter the IP of the computer/s in 'Allow connections for host' to access the server on VNC and KTorrent & Webmin web interfaces.

I don't mind entering a batch of IP's (192.168.0. - to whatever) although I was wondering if there's an easier way to do this as my IP will always change.

I though the best way would be to assign a specific IP through the router, but the machine connecting to it is on wireless.

Thanks and sorry if there's already a topic on this (i did do a search).

---

### Post by lovinglinux on 2009-03-10
If you are accessing the server only inside your LAN, then you can configure the internal IP of the machine connecting to the server to be static.

---

### Post by tommyperkins on 2009-03-10
> **lovinglinux said:**
> If you are accessing the server only inside your LAN, then you can configure the internal IP of the machine connecting to the server to be static.

OK, I'll give it a go. Wasn't sure if you could assign a MAC address on my router through a wireless connection.

Is it complicated allowing access to computers outside the LAN as this is something I would like to implement going forward?

---

### Post by wannadumpwindows on 2009-03-10
> **tommyperkins said:**
> OK, I'll give it a go. Wasn't sure if you could assign a MAC address on my router through a wireless connection.

Is it complicated allowing access to computers outside the LAN as this is something I would like to implement going forward?

It depends on the router. The documentation for mine says that you can't, but it works just fine.

It also says you can't manage it from the wireless side, which it also allows, no matter how it's set up.

---

