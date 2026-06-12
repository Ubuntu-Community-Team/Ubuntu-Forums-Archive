---
title: "can't gain root access! why?"
date: 2008-08-18
forum: Debian
---

### Post by Marinski on 2008-08-18
All right, here is my situation. I am trying to run a simple server, installed Debian on it, then apache, then mysql. When installing mysql I ran some script, which asked me if it should restrict remote root logins or something like that. I said "yes". The result - I cannot log on my box as root anymore. If I try ssh -l root I get Permission denied, please try again. If I login with my regular user account I cannot gain root privielgies using su. Whenever I try it says "authentication failure". I can still use the root account for the mysql server, but the system won't let me become root. Where did this script touch? Any ideas?

---

### Post by seanc7 on 2008-08-18
Preventing remote SSH access with the root login is a typical security setup on Linux. When you said "yes" to the mysql installation script question, it did that for you.

You'll need to SSH via another login on the box then use "SU" to do things as root. Or if you have physical access to the box then login via root that way.

---

### Post by Marinski on 2008-08-19
Strange thing was, that when I connected as a regular user, I couldn't become root via su. AND - in /etc/ssh/sshd_config PermitRootLogin was still yes :) Funny, eh?

---

### Post by maybeway36 on 2008-08-20
You could boot a live CD, mount the hard drive, chroot into it, and change the password. chroot is really a very handy tool.

---

