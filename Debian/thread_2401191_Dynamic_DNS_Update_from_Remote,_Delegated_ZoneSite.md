---
title: "Dynamic DNS Update from Remote, Delegated Zone/Site"
date: 2018-09-14
forum: Debian
---

### Post by FourFourSeven on 2018-09-14
Alright, so here's what I have:

I have a home server that is a primary DNS that hosts a domain & zone provided by DuckDns.org (let's call it "main.duckdns.org"). All LAN clients' domain names are dynamically updated to this home DNS server via the accompanying isc-dhcpd daemon. My public IP address, provided by my ISP, is dynamic.

I have set up a second server at a relative's house whose subdomain will be delegated from my **main**.duckdns.org zone: let's call it "**sub**.main.duckdns.org". The public IP address for this site is also dynamic.

What I'm trying to accomplish is to have **sub**.main.duckdns.org periodically send updates to **main**.duckdns.org's forward-mapping zone with its hostname + current IP address, somewhere around 4 hours. I have ruled out zone transfers since all it would accomplish is send **main** sets of non-routeable addresses (I use Class C on both networks). Unfortunately, **sub**.main's modem/router has only DynDNS as a DDNS option, nothing customizable. The same thing applies to my own modem on **main**'s network. I'm trying to see if using SSH IP & port forwarding/tunneling would work, but I can't get it to run on either host server (both Local and Reverse port forwarding). Then again, I don't yet fully understand it either.

How do I get this to work? Am I right in thinking OpenSSH forwarding would work? Or am I definitely missing something here?

---

### Post by TheFu on 2018-09-14
**ddclient** is the usual answer for dynamic DNS updates.  I don't know **anything** about duckdns, but I've used it with no-ip, dyn, and a few others.

---

### Post by FourFourSeven on 2018-09-15
I'm trying to experiment using nsupdate to update my remote DNS system, but it's not present. I've searched my repositories, but there's no mention of it. If it's in the bind-utils suite, I'm not seeing it. Know how I can get nsupdate?

EDIT: Nevermind, found it! I was supposed to search for "dnsutils"; it's not in "bind-utils." D'OH!

---

