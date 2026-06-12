---
title: "unable to login as root"
date: 2006-03-13
forum: Desktop Environments
---

### Post by grahamwhiteman on 2006-03-13
I am fairly new to linux, I have installed 5.04 and for some reason I cannot login in using the root user. I can confirm the pwd because every time I need to change something requiring root privileged I am asked for the pwd. I have tried login via X and also via a terminal session (with no success). 

This might be a silly question, but has/does ubuntu install/setup such that you cannot login as the root user for security reasons?

---

### Post by Koybe on 2006-03-13
Ubuntu use sudo. Get information [here.](https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges)

---

### Post by yanik on 2006-03-13
you should also try ubuntu 5.10

---

### Post by Jaygo333 on 2006-03-13
Ubuntu does try to restrict(discourage) its users from loggin in as root. In case they cause damage. 
Otherwise, any body can.
the command for root is "su" then the password. If you haven't typed a password for "su", type "su passwd" , that should prompt you to cahnge the password. type a new one and try "su", should now log you in as root.

---

### Post by thoffland on 2006-03-13
[QUOTE=Jaygo333]Ubuntu does try to restrict(discourage) its users from loggin in as root. In case they cause damage. 
Otherwise, any body can.
the command for root is "su" then the password. If you haven't typed a password for "su", type "su passwd" , that should prompt you to cahnge the password. type a new one and try "su", should now log you in as root.[/QUOTE]


Jaygo, just to chime in... I've been using "sudo -s" and just taking care of things that way, then typing "exit" to become a regular user again. Is this good/acceptable/bad practice?

---

### Post by aysiu on 2006-03-13
You don't need to log in as root:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

