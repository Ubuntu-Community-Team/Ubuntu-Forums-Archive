---
title: "error in mysql update"
date: 2007-12-21
forum: Desktop Environments
---

### Post by shendric on 2007-12-21
Today's mysql-server software update failed, with the following message:

E: /var/cache/apt/archives/mysql-server_5.0.45-1ubuntu3.1_all.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 1

Any ideas what the problem could be?

---

### Post by bartpe on 2007-12-23
Hi,

Same problem on my machine.
Turned out I removed the ubuntu sql user "debian-sys-maint".
Check the file '/etc/mysql/debian.cnf' and enter valid user/password in there...

Regards,
Bart.

---

### Post by shendric on 2007-12-24
Yep, that was it.  I had copied over all the tables from a previous database when I upgraded to Gutsy, and it had copied the previous debian-sys-maint user and password.  I reset it to the present debian.conf password, and all went well.

Thanks much!

---

### Post by mr_niceguy on 2007-12-28
Normally updates are painless. I was a little disappointed with this one. Thanks for the help.

---

