---
title: "disable CD drive"
date: 2012-03-09
forum: Desktop Environments
---

### Post by ramakanta on 2012-03-09
I  have ubuntu 10.04, my Que. is how to disable my CD drive like in windows OS.
thank you.
 
:confused:

---

### Post by codemaniac on 2012-03-09
Go to System> Admin > Users and Groups> click Unlock + enter password> click properties> User Privileges tab> scroll down and uncheck "Use CD-ROM drives"> click OK.

---

### Post by pavi_elex on 2012-03-09
To disable cd-rom
simply remove the user from the 'cdrom' group. Then the user  should not be able to access it (in user management there is an advanced  tab where you can uncheck such option).

or
```
mv  /lib/modules/$(uname -r)/kernel/drivers/cdrom/cdrom.ko /root
```or

Go to System> Admin.> Users and Groups> click Unlock, enter  password> highlight a user account> click properties> User  Privileges tab> scroll down and uncheck "Use CD-ROM drives"> click  OK.

---

### Post by squilookle on 2012-03-09
What do you mean when you say you want to disable your CD drive? Do you want to permanently/completely disable it, or just stop it mounting or autorunning discs when you put them in?

---

### Post by ramakanta on 2012-03-11
> **codemaniac said:**
> Go to System> Admin > Users and Groups> click Unlock + enter password> click properties> User Privileges tab> scroll down and uncheck "Use CD-ROM drives"> click OK.
not working..

---

### Post by ramakanta on 2012-03-11
> **squilookle said:**
> What do you mean when you say you want to disable your CD drive? Do you want to permanently/completely disable it, or just stop it mounting or autorunning discs when you put them in?
i want to disable permanently.

also if possible please help me how stop auto-running or mounting. 
thank you.

---

