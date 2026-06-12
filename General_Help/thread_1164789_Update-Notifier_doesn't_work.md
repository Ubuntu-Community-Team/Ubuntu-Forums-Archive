---
title: "Update-Notifier doesn't work"
date: 2009-05-20
forum: General Help
---

### Post by bperucchi on 2009-05-20
Linux go2b-server 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Ubuntu 9.04

My Update Manager doesn't work

It's doesn't start when Gnome Desktop are initialized.

[email]root@go2b-server:/etc/cron.daily[/email]# ps ax|grep update-notifier
20134 pts/9    S+     0:00 grep update-notifier

---

### Post by rudy.b on 2009-05-20
Do you see the update-notifier in your startup preferences:

System > Preferences > Startup Applications > Startup Programs > Update Notifier

If it's there and it's checked, see if you can run the update-notifier from the command line without any errors.

---

### Post by bperucchi on 2009-05-20
> **rudy.b said:**
> Do you see the update-notifier in your startup preferences:

System > Preferences > Startup Applications > Startup Programs > Update Notifier

If it's there and it's checked, see if you can run the update-notifier from the command line without any errors.

root@go2b-server:/etc/firestarter# update-notifier 

** (update-notifier:19791): WARNING **: not starting for system user

---

### Post by Yellow Pasque on 2009-05-20
> ** (update-notifier:19791): WARNING **: not starting for system user
Don't run the command as root.

I have update-notifier running, but it doesn't seem to work on a fairly fresh install of Jaunty (*shrug). Oh well, it was kind of an annoyance anyway.

BTW, yes, I do have a notifier area in one of my GNOME panels. Does anyone know if the update-notifier uses that or does it attempt to use the new Ubuntu notification system?

---

### Post by bperucchi on 2009-05-20
root@go2b-server:/etc/firestarter# update-notifier --force
** (update-notifier:21287): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:21287): DEBUG: crashreport_check

---

### Post by rudy.b on 2009-05-20
bperucchi, if you're logging in as root, that may be the problem.  Try logging in as a regular user and see if the update-notifier is started.  

> **Temüjin said:**
> BTW, yes, I do have a notifier area in one of my GNOME panels. Does anyone know if the update-notifier uses that or does it attempt to use the new Ubuntu notification system?

I do get the update notifier icon appearing in my notification area when updates are available, but I did an upgrade not a fresh install of Jaunty.  I think new default behaviour of the update notifier has changed.

---

### Post by Yellow Pasque on 2009-05-20
> **bperucchi said:**
> root@go2b-server:/etc/firestarter# update-notifier --force
** (update-notifier:21287): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:21287): DEBUG: crashreport_check

You're still running the command as root

---

### Post by bperucchi on 2009-05-20
> **Temüjin said:**
> You're still running the command as root


How I could run update-notifier as root?

My desktop profile as root. I hate had that run su or sudo to access all my system.

Best Regards
Breno

---

