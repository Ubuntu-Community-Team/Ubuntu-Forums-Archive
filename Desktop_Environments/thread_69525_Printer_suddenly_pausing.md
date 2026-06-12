---
title: "Printer suddenly pausing"
date: 2005-09-27
forum: Desktop Environments
---

### Post by reedlaw on 2005-09-27
I have an Ubuntu lab set up and lately almost every day the printer is stopping.  It ran fine for weeks previously.  Now when it pauses itself I have to login as sudo user and resume the printer.  In the cups log I get the following errors:

> E [27/Sep/2005:15:29:13 +0800] [Job 2284] pdftops-options: -cfg /etc/cups/pdftops.conf
E [27/Sep/2005:15:30:38 +0800] [Job 2284] Unable to send print file to printer: No such device
E [27/Sep/2005:15:30:38 +0800] PID 2408 stopped with status 1!

I haven't done any changes to pdftops, in fact, I was unaware of its existence.  The printer in question is a USB-connected HP LaserJet 1320n.

Thanks,
Reed

---

