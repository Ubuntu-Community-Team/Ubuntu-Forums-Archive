---
title: "kdm/gdm choice at upgrade confused me a little"
date: 2010-10-11
forum: Desktop Environments
---

### Post by schwim on 2010-10-11
Hi there everyone,

I upgraded one of my machines to .10 from .04 and during the process was asked which desktop manager I used; gdm or kdm.

This kind of confused me a little.  Is KDE now a part of the Ubuntu install?  I wouldn't mind hopping back and forth to see the upgrades in KDE.  If KDE was installed during the upgrade, how might I choose to boot into it?

Thanks in advance for your time.

---

### Post by sisco311 on 2010-10-11
Hi,

KDE is not part of the default Ubuntu installation, however if it's installed on your system you should be able to select it from the bottom of the login screen (instead of Gnome, which is Ubuntu's default desktop environment).. 

To change the default display manager, run:
```
sudo dpkg-reconfigure <display manager>
```
and follow the instructions.

i.e.:
```
sudo dpkg-reconfigure gdm
```
or
```
sudo dpkg-reconfigure kdm
```

---

### Post by schwim on 2010-10-11
Thanks very much for your reply, sisco.

I wonder if you can have a bug free experience out of the box with installing KDE in Ubuntu, as opposed to installing Kubuntu, with which they've supposedly ironed out the foibles.  Can  someone expect a reasonably smooth experience with KDE in Ubuntu or should one just appreciate the work that has gone into mating Gnome with Ubuntu?

---

### Post by sisco311 on 2010-10-11
Check out:  [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by schwim on 2010-10-11
Thanks very much for the link, sisco.  I think I'll stick with gnome for now :)

---

