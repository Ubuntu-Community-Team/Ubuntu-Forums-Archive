---
title: "Friday Oct 8th update = no network manager"
date: 2010-10-08
forum: Desktop Environments
---

### Post by website.reader3 on 2010-10-08
Is anyone getting this problem?  Around 3:30 pm PDT this afternoon, Friday Oct 8, 2010 I allowed the system to update the lucid package, but now I've lost the network manager, a new entry appears in network interfaces as eth0:avahi and the sudo command runs ridiculously slow (trying to resolve into a non-working network)

I cannot get the nm-applet to work at all, not even after a dbus reset.

Curious if this is happening to anyone else?

----
Okay, had to reboot twice, had to use the services command to restart the network-manager "service network-manager restart" to enable the icon to appear again, as opening a xterm and entering the CLI command "nm-applet --sm-disable" doesn't do it.

---

