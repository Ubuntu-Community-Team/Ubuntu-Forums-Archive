---
title: "ufw: can't delete rule TO 1.0.0.0/8"
date: 2008-05-24
forum: Desktop Environments
---

### Post by gaiterin on 2008-05-24
Hi!
Why I can't delete this rule?
Thanks very much!
Regards




```
mypc@mypc-desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
1.0.0.0/8                  ALLOW   Anywhere

mypc@mypc-desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
1.0.0.0/8                  ALLOW   Anywhere

mypc@mypc-desktop:~$ sudo ufw delete allow to 1.0.0.0/8
Rules updated
mypc@mypc-desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
1.0.0.0/8                  ALLOW   Anywhere

mypc@mypc-desktop:~$ 

```

---

