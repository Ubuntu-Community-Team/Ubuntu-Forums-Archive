---
title: "Kubuntu-desktop wants to remove mysqlcc"
date: 2005-12-20
forum: Desktop Environments
---

### Post by vayu on 2005-12-20
I tried to use synaptic to install Kubuntu-desktop onto Ubuntu Breezy and it displays "packages to remove: mysqlcc".

Shouldn't the mysql control center should be unrelated to KDE or Gnome?

I want to have both Gnome and KDE on the same installation but I need mysqlcc.  I also don't want to rearrange my system too much, I currently don't have the time to set it up again like I did.


edit:

It turns out that the mysqlcc that I installed on Hoary before I dist-upgraded to Breezy uses a qt lib that is obsolete on Breezy.  However mysqlcc is not available in the repositories for breezy.  So what I did is I found a binary version of mysqlcc that would just run.  I uninstalled the existing mysqlcc, extracted the tarball and then was able to apt-get Kubuntu.  It was hard to find the tarball of mysqlcc and I don't have the link anymore but if someone needs it and can't find it PM me.

---

### Post by aysiu on 2005-12-20
How about ```
sudo apt-get install kde
``` instead of ```
sudo apt-get install kubuntu-desktop
```?

---

### Post by vayu on 2005-12-20
[QUOTE=aysiu]How about ```
sudo apt-get install kde
``` instead of ```
sudo apt-get install kubuntu-desktop
```?[/QUOTE]

I thought about that but I want to make sure I get all the apps and other goodies.

---

### Post by ace2005 on 2005-12-20
Couldn't you install them when you're in KDE?

---

### Post by ace2005 on 2005-12-20
Oh wait i have another idea, what if you install it by using Kubuntu's repo by adding this to the sources list:

deb [http://kubuntu.org/packages/kde35/](http://kubuntu.org/packages/kde35/) breezy main

This could work

Then synaptic has the new in repository thing which can show what was added from this source

---

### Post by aysiu on 2005-12-20
[QUOTE=vayu]I thought about that but I want to make sure I get all the apps and other goodies.[/QUOTE] KDE actually installs *more* "goodies" than kubuntu-desktop.

---

