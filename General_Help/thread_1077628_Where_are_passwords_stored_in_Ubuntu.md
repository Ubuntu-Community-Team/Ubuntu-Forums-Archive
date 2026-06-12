---
title: "Where are passwords stored in Ubuntu?"
date: 2009-02-22
forum: General Help
---

### Post by bluefox815 on 2009-02-22
Hi, I'm curious as to where the encrypted user account passwords are on my computer?  I'm running Ubuntu 8.10

I want to know this so that I can restore account passwords without requiring the user to enter them by hand.  They just have to enter it once, then I backup the encrypted password, and replace it if necessary.

---

### Post by bodhi.zazen on 2009-02-22
In general, if a user forgets his or her password you reset it with

sudo passwd user_name

You  can back up /etc/shadow /etc/passwd and if you wish

[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

[http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html](http://tldp.org/HOWTO/Shadow-Password-HOWTO-2.html)

Take GREAT CARE with any backups you make, they can be used to crack passwords (see john the ripper).

---

### Post by bluefox815 on 2009-02-22
Yes, thank you, the shadow file is exactly what I was looking for.  I already knew about the /etc/passwd file, but that would only backup the user account without the password.

---

