---
title: "Adept problem"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Ollan on 2006-09-18
Hi!
When I'm installing any package in Adept I get the following message:

> 
dpkg-preconfigure: cannot connect to X server :0
debconf: kan inte initiera skal: Kde
debconf: (DISPLAY problem?)
debconf: återgår till gränssnitt: Dialog
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


Background: Running Kubuntu Dapper with KDE 3.5.4

What's the problem.

By the way, why is USB so slow in Dapper? My USB 2.0 slots was much faster before the clean install of Dapper?!

---

### Post by lamego on 2006-09-18
Are you using the root user ? You should launch adept from a regular user (it will prompt for the password for the sudo).

---

### Post by Ollan on 2006-09-18
Yepp, I'm using it as an regular user, not sudo etc.

---

### Post by PatheticMoFo on 2006-11-01
Found this on google. Think it should help,
[http://www.linuxforums.org/forum/ubuntu-help/71737-x-display-errors.html](http://www.linuxforums.org/forum/ubuntu-help/71737-x-display-errors.html)

---

### Post by shrink on 2006-11-20
i'm getting exactly the same message when i install anything with adept.  everything else still seems to be working fine though and the installs always work.  the weird thing is that if i use apt-get through konsole then i don't get the same message.  i will give the solution on the link and see what happpens!

---

