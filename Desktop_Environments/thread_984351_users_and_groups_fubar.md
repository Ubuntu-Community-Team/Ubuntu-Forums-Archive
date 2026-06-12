---
title: "users and groups fubar?"
date: 2008-11-16
forum: Desktop Environments
---

### Post by kritro on 2008-11-16
I have 8.04

Panic!!!
I was trying to log on to the user and group admin gui, but I didn't come in.

I then rebooted the machine from shell and it didn't start like it was supposed to. 

I try to run dpkg reconfigure -a and started xwindows manually, but many services is not starting because of error with users.

When I try to start them its like this

/etc/init.d/apache2 start
message:
install: invalid user 'www-data'
apache2: bad user name www-data     [fail 9
---------------------
/etc/init.d/mysql start, only says   [fail]
------------------------

/etc/init.d/ssh start
message:
Privilege separation user sshd does not exist    [fail]
 ----------------------

and so it goes on and on.
Is it something that has gone wrong with the user/group setup?

Is there some way I can reconfigure it?

Thanks

---

### Post by kritro on 2008-11-17
reinstalled the os

---

