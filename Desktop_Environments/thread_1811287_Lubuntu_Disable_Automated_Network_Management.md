---
title: "Lubuntu Disable Automated Network Management"
date: 2011-07-24
forum: Desktop Environments
---

### Post by Jack Waugh on 2011-07-24
I have a system that has the Lubuntu desktop software loaded on it.  I want to connect eth0 to my modem to the Internet.
I have a second Ethernet interface, eth1.  I want to use that on a local network.

I find that when I try to configure eth1 manually while the Lubuntu desktop is running, my configurations don't "stick", and the desktop talks about eth1 being available, and says it has become the default interface.  Then the Internet becomes unreachable from ordinary applications not specially configured.

So it looks as though one or more daemons and/or some other software associated to or part of the Lubuntu desktop software is seeing that the interface is available and taking over its management.  How do I turn that off?

---

