---
title: "Disable guest login, Xubuntu 14.10"
date: 2015-04-03
forum: Desktop Environments
---

### Post by remington2 on 2015-04-03
At one time, one could disable guest login by setting allow-guest=false in /etc/lightdm/lightdm.conf.
That file does not exist in a newly installed Xubuntu 14.10 system, instead there are three .conf files as follows:

> 
rwxrwxrwx 1 root root   55 Feb 14 13:07 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r-- 1 root root 1317 Jul  5  2014 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r-- 1 root root  452 Oct  9 09:54 users.conf


I tried adding allow-guest=false to the first,which is the most recent, but that had no effect.

What do I do to disable guest login?

Thanks, Jim

---

### Post by CantankRus on 2015-04-04
Look in** /usr/share/lightdm/lightdm.conf.d**
Not sure what the file is in Xubuntu.... something like **60-lightdm-gtk-greeter.conf**
You can edit that file or just create another starting with a higher number to override lower numbered configs.
eg I just create a **/usr/share/lightdm/lightdm.conf.d/99-no-guest.conf**
```
[SeatDefaults]
allow-guest=false
```
That way, you don't have to worry if you have the right config file and you can just delete the **99-no-guest.conf** to return to default settings.

---

### Post by jremington on 2015-04-06
Thanks, the latter method (99-no-guest.conf) worked fine!

---

