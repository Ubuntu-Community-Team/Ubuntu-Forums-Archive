---
title: "printer server monitors network"
date: 2006-01-05
forum: Desktop Environments
---

### Post by bulldogzerofive on 2006-01-05
Hello all

This is not really a problem, just an annoyance.

I have an HP printer, for which I need hplip.  Annoyance is, netstat revealed that it is monitoring ports 32769 and 32770 on device eth0, which is my internet connection.  Although I have a firewall, I consider this a (very mild) security risk.

Does anyone know how to configure hplip to either monitor only on device eth1 or to not monitor the network at all?  I could not find a man page or .conf file at all and the GUI does not seem to have any options for it.

Thanks all

---

