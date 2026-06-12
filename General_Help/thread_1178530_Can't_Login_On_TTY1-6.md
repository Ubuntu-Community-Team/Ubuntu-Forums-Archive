---
title: "Can't Login On TTY1-6"
date: 2009-06-04
forum: General Help
---

### Post by charonn0 on 2009-06-04
I have been unable to login in TTY1-6 text mode. I can log in on TTY7, the graphical interface and I can also login via ssh. I tried creating a new user to see whether it was simply my account that was having trouble, but the new account couldn't log in either.

Here's the error from /var/log/auth.log:
> 
Jun  4 12:40:51 guardian login[2412]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=tty6 ruser= rhost=  user=andrew
Jun  4 12:40:54 guardian login[2412]: FAILED LOGIN (1) on 'tty6' FOR `andrew', Authentication failure

> Jun  4 12:42:58 guardian groupadd[6536]: new group: name=test, GID=1001
Jun  4 12:42:58 guardian useradd[6561]: new user: name=test, UID=1001, GID=1001, home=/home/test, shell=/bin/bash
..snip...
Jun  4 12:43:17 guardian login[2403]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=tty5 ruser= rhost=  user=test
Jun  4 12:43:20 guardian login[2403]: FAILED LOGIN (1) on 'tty5' FOR `test', Authentication failure
Jun  4 12:43:28 guardian login[2403]: FAILED LOGIN (2) on 'tty5' FOR `test', Authentication failure

Ubuntu 9.04 with all updates.

---

### Post by charonn0 on 2009-06-06
More info:

If I'm not logged in on TTY7 then it works fine.

---

### Post by charonn0 on 2009-12-14
Now on 9.10, problem seems to be gone.

---

