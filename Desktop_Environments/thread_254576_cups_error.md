---
title: "cups error"
date: 2006-09-10
forum: Desktop Environments
---

### Post by r£v on 2006-09-10
how do i resolve the error:
checking cups/cups.h usability... no
checking cups/cups.h presence... no
checking for cups/cups.h... no
configure: error: cannot find cups-devel support
I have tried installing most of the cups packages in adept and googling for the source but i have yet to find the package/source for it.

---

### Post by whizbaby on 2006-09-10
What are you actually trying to do? If you have done a normal ubuntu install cups should be on the system. Is it not? Are you trying to compile cups manually? Why not installing the package? (if you want to compile you'll need to install *libcupsys2-dev* and *libcupsimage2-dev* )

---

### Post by r£v on 2006-09-10
At first i did not realise cups comes with it. The problem now is that when I am on [http://localhost:631](http://localhost:631) and it prompts me for a passwd before making any changes. So when I enter either my account and passwd or root account and passwd it comes up with the error 401 saying authentication failure when i am 100% certain i entered the correct passwd. What do I do now?

---

### Post by whizbaby on 2006-09-10
It's true that the system comes with CUPS, but the CUPS-daemon has not the permission to verify passwords by default (security issue, you have to grant access yourself). This is why you get an error message.
You could enable the passwd-check-ability by typing
**sudo adduser cupsys shadow**
and then
**sudo /etc/init.d/cupsys restart**

---

