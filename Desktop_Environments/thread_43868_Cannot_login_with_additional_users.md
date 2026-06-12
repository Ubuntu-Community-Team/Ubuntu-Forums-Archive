---
title: "Cannot login with additional users"
date: 2005-06-23
forum: Desktop Environments
---

### Post by speedsix on 2005-06-23
I've created a user account for my wife alongside mine and it refuses to let me in either gnome or even a tty console. I added the user with System > Admin > Users & Groups.

i have deleted and recreated the account but it won't accept the password. I've even added an account with the adduser command, same problem.

Any ideas?

Many thanks

Ubuntu 64 Hoary btw

---

### Post by speedsix on 2005-06-24
Anyone?

---

### Post by tonym on 2005-06-24
I've had this but can't explain why.  I got round it by changing the user's password whilst logged on as root (or sudo).  eg

passwd username

---

### Post by speedsix on 2005-06-24
Excellent that worked a treat!

I'd like to know why though  :???:

---

