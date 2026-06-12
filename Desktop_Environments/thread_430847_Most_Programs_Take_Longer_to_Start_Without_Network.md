---
title: "Most Programs Take Longer to Start Without Network"
date: 2007-05-02
forum: Desktop Environments
---

### Post by Kenji Miyamoto on 2007-05-02
For some reasons, all of the graphical programs on Ubuntu take several times longer to start up when this laptop's not connected to a network.  Is there a way to fix this?

---

### Post by dcstar on 2007-05-03
> **Kenji Miyamoto said:**
> For some reasons, all of the graphical programs on Ubuntu take several times longer to start up when this laptop's not connected to a network.  Is there a way to fix this?

You may need to check your hostname, your /etc/hosts file as well as /etc/hosts.conf.

Your system is probably trying to do local DNS lookups, and because there is no actual DNS server to send back a quick response, you have to wait for timeouts to occur.

---

