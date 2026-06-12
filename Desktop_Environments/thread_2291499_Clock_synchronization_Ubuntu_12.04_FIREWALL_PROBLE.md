---
title: "Clock synchronization Ubuntu 12.04 FIREWALL PROBLEM"
date: 2015-08-20
forum: Desktop Environments
---

### Post by icheaux on 2015-08-20
Hey, i'm new on this site. Sorry if this thread is in the wrong site. And sorry for my bad english. (I'm from Argentina)

The problem is, that i need use NTP to synchronize time in various pc with Ubuntu 12.04.
I recieve a error when use "sudo ntpdate -u ntp.ubuntu.com" ( i test many external servers).

Error resolving ntp.ubuntu.com Name or service not known (-2)
and
No servers can be used. Exiting.

The network have a firewall, they use a VLAN, i mean we work with a external server, that we haven't the root permissions to modify.

Exist any alternative to use?

Thanks!

---

### Post by SeijiSensei on 2015-08-21
Any NTP servers running on the local network?  Otherwise, if the firewall blocks traffic on port 123, you're pretty much out of luck.  The only other option would be to run your own server and connect it to a hardware time-keeping device that ntpd supports.

---

