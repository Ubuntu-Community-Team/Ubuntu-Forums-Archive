---
title: "no network manager in 8.1?"
date: 2008-12-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LesFromWaldenVT on 2008-12-08
I just switched to 8.1 and my ISP is constantly dropping my connection (at least, I think that is what is happening). When I switched to 8.1, the network management tool had disappeared from System/Adminstration. There doesn't seem to be any replacement. 
I've been restarting my connection by 1) power off cable modem, 2) kill dhclient3, 3) power cable modem on, 4) rerun the same dhclient3 command (found by 'ps -few | grep dhc'-before step 2, of course).
I guess I'm wondering a) how do I tell if it's the ISP that is the problem? b) is there an easier method, c) is the original network tool available via apt-get?

---

### Post by doas777 on 2008-12-08
I have no idea if this is your problem, but I never got NM to load if all my interfaces were configured statically in /etc/network/interfaces . I had to delete/touch my interfaces file before getting it to reappear. 

you can tell if this is your cause by looking at your system log after login, looking for a message from NM stating that it could not find any managed interfaces.

good luck

---

### Post by MarblePanther on 2008-12-08
There is also wicd

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

