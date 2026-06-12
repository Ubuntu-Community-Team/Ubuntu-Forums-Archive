---
title: "SHARP355/CUPS printer issue"
date: 2008-02-14
forum: Desktop Environments
---

### Post by jdix123 on 2008-02-14
I just tried to configure a printer through the IP port, and I went through System-administration-printing, selected new printer, and set up my networked SHARP AR-M355N printer.  These drivers were (apparently) included.  

I tried this both on a Hardy laptop (Pentium 4m, 512 RAM) and on a Gutsy desktop (P4, 1.2 G RAM) with the same result:

The printer appears to be setup, but does not print jobs sent to it.  It also does not print a test page.

---

### Post by derekshaw on 2008-05-06
If you are in the same situation as me, it is because the optional PS module was not purchased for the printer.  The PPD for the sharp ar-m355n only includes PS support.

I got it to work (after a fashion) by using an HP laserjet of some description (I think I chose 9000) with the Gutenprint (PCL6) driver in CUPS.

using Hardy Heron desktop.

---

