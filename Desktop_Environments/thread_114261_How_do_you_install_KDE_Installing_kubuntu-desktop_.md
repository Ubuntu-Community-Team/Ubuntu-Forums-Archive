---
title: "How do you install KDE? Installing kubuntu-desktop asks me to remove packages."
date: 2006-01-08
forum: Desktop Environments
---

### Post by NPN_Transistor on 2006-01-08
I'm trying to install KDE from my ubuntu (gnome) system. 

I tried installing kubuntu-desktop, but it says to install it I have to remove libmodplug 0, libxine 1, a bunch of xlibmesa stuff, and xlibomesa4.  

Is it safe to remove these packages? Is installing kubuntu-desktop even the right way to install KDE? 

Thanks for your help. And sorry for being a n00b.

---

### Post by Ampersand on 2006-01-08
Have a look through the list of packages that will be installed, sometimes libraries are removed and replaced with different versions of the same library. Generally, it shouldn't be a problem if it doesn't try and remove any programs

As an alternative to installing kubuntu-desktop, you can install the kde package then add any other sets of programs you need (kdemultimedia, kdenetwork &c).

---

### Post by Sef on 2006-01-08
yes it is the right way.  I did it through apt-get: 

sudo apt-get install kubuntu-desktop


(No problems for me.)  Hope u get yours fixed soon.

---

### Post by aysiu on 2006-01-08
Any difference if you do ```
sudo apt-get install kde
```?

---

