---
title: "Startup errors"
date: 2006-07-16
forum: Desktop Environments
---

### Post by electroconvulsive on 2006-07-16
Since I tried to install Bugzilla (which didnt work and subsequently uninstalling it) during startup I get the following error message at about [COLOR="Sienna"]Starting Basic Networking[/COLOR] 
[COLOR="Red"]rm: cannot remove '/etc/mail/sendmail : read only file system
make *** [sendmail.cf] error 1
Updating with
/usr/share/sendmail/update_auth: line 98 cannot create temp file from document: read only file system
Creating /etc/mail/relay-domains
#optinal file
A forced reolad
** ***you should issue /etc/init.d/sendmail reload*** **
Mail Transport Agent: Sendmail not running.[/COLOR]

I have executed [COLOR="Red"]/etc/init.d/sendmail reload[/COLOR] but it doesnt stop the errors on startup.

This is slowing my startup time dramatically and making me have to manually start sendmail every time I log on. Can anyone help?

---

### Post by philippe_carlo on 2006-07-16
Please, do not post to multiple threads simultaniously. This should be posted once under networking.

---

### Post by arbol on 2007-02-01
I search on synaptic all references of sendmail and mark them to eliminate. After apply these changes and reboot the system the warning disappear.

I hope that it will be usefull.

---

