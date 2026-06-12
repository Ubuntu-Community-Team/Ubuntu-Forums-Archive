---
title: "kshutdown serious failure"
date: 2006-08-24
forum: Desktop Environments
---

### Post by anopheles on 2006-08-24
Recently installed kshutdown on Breezy i386.

The GUI appears to work, and the countdown to shutdown time looks ok, but when shutdown time arrives, the panel item title changes to "please wait" - and nothing happens.

Subsequently requesting Shutdown from the K menu appears to start another shutdown sequence, but (sometimes?) that does nothing too; and then attempting to request shutdown from the K menu again becomes impossible.

I then issued shutdown from a command line, and the system really did appear to close - xwindows gets clobbered, lots of services shutdown - then I saw several messages as though it was rediscovering USB hubs etc - almost as though starting up again - and the system completely froze with the power light blinking (main power still on).  

I did notice a message close to the end about "battery check ok" or something like that, which is strange considering this is a desktop system, not a laptop. Relevant?

Anyone got any input on this? Is kshutdown supposed to work on Breezy?

---

### Post by anopheles on 2006-08-24
sorry, should have made clear that my problem with kshutdown is with Kubuntu/Breezy, rather than ubuntu + kde.

---

