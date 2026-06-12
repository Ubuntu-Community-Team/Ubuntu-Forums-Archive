---
title: "hald is doing SIGSEGV; how do i get desktop without hald?"
date: 2009-09-28
forum: Desktop Environments
---

### Post by rshetye on 2009-09-28
hald is doing SIGSEGV, how can I bypass dbus and hal to get to the desktop?

**ANSWER:**
> [B][http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515214](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515214)
Get the xorg.conf from this port and replace your xorg.conf

OR the following is ALL that you need in your xorg.conf

[QUOTE]Section "ServerLayout"
        Identifier      "Default Layout"
        Option "AutoAddDevices" "off"
EndSection

Also, run "sudo /etc/init.d/hal restart" once your gnome desktop is up and running.

[/B]



HAL is a pos that needs to be kept out of serious stuff like X. HAL is NOT stable enough, one hiccup and your ENTIRE desktop is inaccessible without ANY indication of WHAT the HELL is wrong!!!!! I'd love to hear the explanation of how ANY dependency on HAL's flakiness is better in ANY form whatsoever as compared with the registry nonsense that MS keeps getting beat up for

Seriously, I mean, HAL has to have ONE hiccup and my desktop is inaccessible with no warnings/workarounds/explanations/indications???????????? What kind of Engineering is this?
[/QUOTE]

Edit: deleted all kinds of hald logs

System is Dell Inspiron 6400 running Ubuntu 9.04. Basic install.

---

### Post by rshetye on 2009-11-15
This is not to be considered solved since the hald has started crashing again... on a 9.10 clean install + updates.....

---

