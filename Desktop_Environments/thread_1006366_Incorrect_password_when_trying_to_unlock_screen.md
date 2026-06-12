---
title: "Incorrect password when trying to unlock screen"
date: 2008-12-09
forum: Desktop Environments
---

### Post by Zorael on 2008-12-09
When trying to unlock the screen, such as after having locked it or just resumed the system from suspend or hibernate, it refuses to accept my password. If I switch to a tty screen, I can successfully login using exactly the same credentials, so I *know* it hasn't been ninjachanged.

If I pick Switch User, I get sent to the login screen. If I then login normally (with the same user and password), it unlocks and resumes my earlier session.

The only passwordy thing I know I've done is to set a root password, since FOR SOME REASON it demands it if I boot up into recovery mode and choose to start a root shell. Without one I know, I can't enter the shell.


Any ideas?

---

### Post by dalmeida on 2009-01-22
I was also having the same problem, found the solution below here:
[https://lists.launchpad.net/ubuntu-eee-coders/msg00805.html](https://lists.launchpad.net/ubuntu-eee-coders/msg00805.html)

CAUSE:
 /sbin/unix_chkpwd has wrong group/permissions
SOLUTION:
 sudo chown root:shadow /sbin/unix_chkpwd
 sudo chmod 2755 /sbin/unix_chkpwd

---

### Post by particleMan86 on 2009-02-08
I tried this fix and it didn't solve the problem. I have the correct permissions on /sbin/unix_chkpwd. Is there anything else that might be causing this?

---

### Post by Xgamer04 on 2009-04-17
I'm having the same issue and that workaround also didn't work. So far, I've just narrowed it down to something to do with shadow. After disabling shadow (/sbin/shadowconfig off) I was able to log in just fine after locking the screen.

---

### Post by basher501 on 2009-09-07
According to a popular Linux Administration book, for security purposes, the permissions on the /etc/shadow file should be set to 600.  If you set the permissions on /etc/shadow to 600 and use the Lock Screen function,  on Ubuntu 9.04, you will not be able to unlock the screen.  To log back in you will have to restart the computer.  To re-enable the use of the Lock Screen function you'll need to set the permissions on /etc/shadow to 640.

---

### Post by comperocean on 2011-07-17
i am in right permission and privilege of 
"-rwxr-sr-x  1 root     shadow    35432 2011-05-31 20:33 unix_chkpwd"
but i have not unlock the locked screen.

[Resolved]
sudo chown root:shadow /etc/gshadow
sudo chown root:shadow /etc/gshadow-
sudo chown root:shadow /etc/shadow
sudo chown root:shadow /etc/shadow-

from "root:root" to "root:shadow"

the issue will be resolved.

---

