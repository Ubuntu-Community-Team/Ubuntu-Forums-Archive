---
title: "Slow startup with static IP"
date: 2008-05-13
forum: Debian
---

### Post by funkadelic on 2008-05-13
I have a very simple home network set up based around a Linksys WRT54G router...

I recently switched my Debian 4 server over to using a static IP address. Everything is working fine, except my server is now very slow to start up, hanging up at "Starting MTA..." and again when starting AppleTalk...

Can someone tell me what is going on here and/or how to fix it?

---

### Post by lemming465 on 2008-05-20
Probably /etc/resolv.conf doesn't have a suitable DNS server listed anymore.

---

