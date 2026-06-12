---
title: "S-L-O-W netwrok detection at boot-time"
date: 2005-12-26
forum: General Help
---

### Post by cclemon on 2005-12-26
I was wondering if it is possible to do something with that network interface detection during the boot process. The thing is that I'm sitting on a laptop with wifi connection, but the boot-process is listening to DHCP broadcast for both eth0 and eth1 (just a wild guess, since I actually don't know why it takes so long).

What I want my system to do is to stop looking for networks that does not exist for hundreds of seconds before it goes to next step.

Any suggestions?

---

### Post by strips on 2005-12-26
The same thing has bothered me some time. I could not find anything usefut about it. Network detection should fork and not keep the computer from booting if you ask me.

What I did was to lower the timeout of DHCP requests from 60 to 15 sec.

edit /etc/dhcp3/dhclient.conf

and set "timeout 15" or any other value. If you set it to low, it might time out before you get a IP lease.

---

