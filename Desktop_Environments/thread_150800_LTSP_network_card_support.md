---
title: "LTSP network card support"
date: 2006-03-26
forum: Desktop Environments
---

### Post by cphuntington97 on 2006-03-26
LTSP seems to be working fine, I can X -query into the machine, dhcp/pxe seems to be all working, etc.

The only problem is that the kernel that came with ltsp doesn't support or isn't configured for my built in network card, which the ubuntu live cd automatically recognizes and uses (no problems).

So... do I add support for it in one of the included ltsp kernels?

Could I swap out one of the ltsp kernels for the one ubuntu uses that already supports the network card? Am I just missing some module? How do I find out which one to use?

Etc... help wanted.

---

### Post by cphuntington97 on 2006-03-26
For anyone who cares...

My card is nvidia nforce controller (built in).

All I had to do was specific NIC=forcedeth in pxelinux.cfg/default

---

