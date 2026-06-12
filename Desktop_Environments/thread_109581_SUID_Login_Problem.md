---
title: "SUID Login Problem"
date: 2005-12-28
forum: Desktop Environments
---

### Post by carl.roth on 2005-12-28
I have just installed the os and logged on as a normal user. When I try to perform any action that requires root access a suid login window appears. Every time I enter my password if gives me a "wrong password" error.  I know the password is correct as I have tested it in a terminal window using the "su" command which I can successfully execute.

Any ideas?

My password is longer than the window type in field - is the "dots" that appear stop scrolling before the end of my password. Do you think that this may be related to the problem?

Carl

---

### Post by Corvillus on 2005-12-28
Not sure if this is your problem, but in Ubuntu, whenever you do something in GNOME or KDE that requires root privileges, sudo gets called as the setuid root mechanism instead of su, and you have to use your user account's password instead of root's.

---

