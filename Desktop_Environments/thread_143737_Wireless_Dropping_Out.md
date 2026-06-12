---
title: "Wireless Dropping Out"
date: 2006-03-13
forum: Desktop Environments
---

### Post by GTar on 2006-03-13
Hey,

I've set up Breezy with a PCI wireless card for the internet. Picked it up automatically and it worked fine.

The problem is that is continually drops out and wont reconnect. I'll be using the internet when all of a sudden, server not found and GAIM dies etc.

I dual boot with XP and have NEVER in 2 years of using it had a problem with the wireless, and still don't.

Any ideas or suggestions? How do I reconnect if this happens?

---

### Post by htinn on 2006-03-14
Whenever my network drops I just do this:

sudo /etc/init.d/networking restart

It may take about 30 seconds or so, but it does come back eventually.

---

### Post by gtrtoolman on 2006-11-12
I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman

---

