---
title: "Can not log in as same user in nested gdmflexiserver session"
date: 2007-06-23
forum: Desktop Environments
---

### Post by gotgenes on 2007-06-23
When running the following command
```
gdmflexiserver -n
```
I can not log in to the nested session as the same user that issued the command, only as a different user on the system. e.g., If user joe logs in normally, then issues the command to get a nested login window, user joe can not log in to the nested session as user joe, but can as user jane.

No error message appears in the GDM login screen of the nested window, it simply rejects the attempts and plays the drum greeting sound. This used to work under Edgy, (same user could log in to as many graphical sessions as he/she wanted) but no longer works for me in Feisty. When using the "-d" flag, no warnings are issued indicating why the user was not allowed to log in. Any ideas?

Thanks in advance,
Chris

---

### Post by gotgenes on 2007-06-24
It seems this problem occurs on other Feisty installations, not just mine. I have [filed a bug report]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/122046") on Launchad, bug #122046. Please post there if you experience a similar situation for confirmational purposes.

---

