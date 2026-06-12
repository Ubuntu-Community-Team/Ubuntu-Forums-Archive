---
title: "Installing crossover"
date: 2005-10-27
forum: Desktop Environments
---

### Post by rj686 on 2005-10-27
I'm trying to install teh crossover demo but it says that "$home" but belong to you and you must log in as root rather than sudo. How do we log in as root on ubuntu i thought it was only sudo?

---

### Post by rj686 on 2005-10-27
whoops.....cant install it as root........sorry

---

### Post by nystyletaco on 2005-10-27
[QUOTE=rj686]I'm trying to install teh crossover demo but it says that "$home" but belong to you and you must log in as root rather than sudo. How do we log in as root on ubuntu i thought it was only sudo?[/QUOTE]

For future reference, you can login as root by using ***sudo su***

---

### Post by pelleke on 2005-12-18
Actually, it says it can't find my X-server then... 

> Setup requires an X display to run.  There is a display variable set, however
you have no permissions to access the X server (:0.0) it points to.
Try running xhost +localhost before su'ing to root.


Running the recommended command before using sudo su makes no difference...

---

### Post by Rackerz on 2005-12-18
Have you tried typing the command; startx

---

