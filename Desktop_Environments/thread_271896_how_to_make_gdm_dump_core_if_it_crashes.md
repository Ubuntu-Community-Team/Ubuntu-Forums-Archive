---
title: "how to make gdm dump core if it crashes?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by eudoxos on 2006-10-05
Hello, I am having some issues with gdm dying and would like to investigate the coredump (yes, recompiled, with -ggdb3). The problem is that gdm crashes without dumping core.

I did set limits on core in /etc/security/limitc.sonf to '* - core 1024' (tried also with 'unlimited'), but it seems that this file is not honored, since even after a regular login, I have core limit still 0. I did put 'ulimit -Sc unlimited' to /etc/environment, to make sure, which doesn't work either.

[LIST]
[*] Show do I set (hard) core ulimit to ulimited or at least a sufficiently big value for EVERYBODY on the system?
[*] Where does the default of 0 come from? Can it be tuned in /proc?
[/LIST]
 
Many thanks! Eudoxos

---

