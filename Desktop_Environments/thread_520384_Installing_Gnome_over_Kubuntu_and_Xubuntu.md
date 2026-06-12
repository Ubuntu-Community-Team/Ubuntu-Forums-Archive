---
title: "Installing Gnome over Kubuntu and Xubuntu"
date: 2007-08-08
forum: Desktop Environments
---

### Post by RHorse on 2007-08-08
After installing Kubuntu Edgy, I installed the Xubuntu desktop.  Now I would like to install Ubuntu desktop.  Can i just type apt-get install ubuntu-desktop, or will there be conflicts between xfce and gnome?  Since Ive already downloaded so many Gnome packages for Xubuntu, will this throw any wrenches into the works? 

*R* *H*

---

### Post by Kobalt on 2007-08-08
You will have a lot of packages, but they won't conflict.
If later on you wish to remove one of the *-desktop, this link might get uselful : [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by kmangwing on 2007-08-09
You shouldn't have any problems installing GNOME.  After you install the Ubuntu Desktop package, and Ubuntu gets to the login screen, I believe that you hit options and select sessions, and select GNOME, and make it the default session.  It isn't that hard, so you shouldn't have any problems.

---

### Post by merlinus on 2007-08-09
In the event that you wish to easily remove any post-install desktop, best to use aptitude and not apt-get.

```

sudo aptitude update && sudo aptitude install gnome-desktop

```

-merlin

---

### Post by RHorse on 2007-08-09
Thanks to all for your advice

R
Horse

---

