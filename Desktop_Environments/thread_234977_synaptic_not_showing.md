---
title: "synaptic not showing"
date: 2006-08-12
forum: Desktop Environments
---

### Post by tjmoes on 2006-08-12
why doesnt my distro have the add and remove functions or the synaptic showing cant find it, i got a fresh iso  of 6.06 I have tried to find it as in whereis cmd but nut there grrrr v5.1 had it sorta but I dont have it in here

---

### Post by llamakc on 2006-08-12
Are you logged in as the admin user you created during the install?

If you open a terminal it SHOULD be at:

/usr/sbin/synaptic

```

ken@dothan:~$ which synaptic
/usr/sbin/synaptic

```

You could do `sudo apt-get install synaptic` if it is not installed from a terminal window.

---

### Post by tjmoes on 2006-08-12
did a sudo getapt and that did it but my main ? b4 was no add/remove function in the system folder which lead me to the non synaptic but still no add/remove

---

### Post by tjmoes on 2006-08-12
got it to install but cant run it since i cant log into a root acount cept thru the terminal gui says reead only and i still dont have an add/remove in the system menu

---

### Post by llamakc on 2006-08-12
Is your user a member of the admin group?

---

### Post by tjmoes on 2006-08-12
user a member of the admin: not sure how to give permission or ware

---

