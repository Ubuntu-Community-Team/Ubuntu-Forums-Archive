---
title: "Need Static IP in 8.10"
date: 2009-04-29
forum: Desktop Environments
---

### Post by snorkytheweasel on 2009-04-29
I need a static IP in 8.10. 

Every time I try to set the static IP on the NIC, using Network settings, it appears to "take." During the same session I can go back and look at the setting, and it's still static with the correct static IP.

However, if in that session I run IFCONFIG, the DHCP-assigned IP displays.

When I reboot or logout/login, it reverts back to DHCP.

How do I convince Ubu that I really do want a static IP?

---

### Post by tkoco on 2009-04-29
Are you running Network Manager?

---

### Post by nandemonai on 2009-04-29
Known Network manager bug in 8.10 [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214/](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214/).

I&#8217;ve found this works for me personally..

Delete the auto connection and create a new one.

Name it what you like, fill in all the details and check system setting and connect automatically.

Once your done apply it and it _should_ ask for gksudo access in order to save the configuration.

If all goes well then viola.

Upon reboot it will hold the setting.

(Bug was fixed in Jaunty thankfully).

---

