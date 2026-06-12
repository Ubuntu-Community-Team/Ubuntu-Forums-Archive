---
title: "Authentication Error gnome 14.04"
date: 2016-04-06
forum: Desktop Environments
---

### Post by evan32 on 2016-04-06
Hi guys,

Recently I got an LTSP server up and running and I manage to log into the gnome desktop environment fine. However when I log out and am presented with the gnome login screen, underneath the password field it keeps saying authentication error repeatedly and when I try to type the password in it resets it every single time as if it's attempting to press the unlock button every split second.

Anyone had this issue with an idea on how to fix it? or perhaps a log file I can look at to diagnose the issue.

---

### Post by scar3 on 2016-09-23
This  happened to me after i tried to remove evolution and its dependencies.  During the uninstallation (apt-get) reminded me that 'gnome' and some other seemingly-unrelated packages would be removed.  I thought they were just metapackages and gnome wouldn't actually be removed, but gnome actually got removed along with several other essential components.  When i went to unlock my screen i was having the same issue described by OP, my guess is there were some stray gnome processes left over (like the lock screen) but it couldn't communicate with other gnome components.  I eventually rebooted the computer and gnome didn't even start this time, i had to log in via command line.  After i reinstalled gnome (apt-get install gnome), gnome started up and i was able to log into the GUI....

---

