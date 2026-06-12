---
title: "create a debian package"
date: 2006-09-06
forum: Desktop Environments
---

### Post by hraposo on 2006-09-06
How can I create a debian package from a tar.gz package (from source-code).

---

### Post by ahaslam on 2006-09-06
I was wondering the same thing last week and found this on google:
[http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)

There'll no doubt be a thread or two here as well ;)

Tony.

---

### Post by bluenova on 2006-09-06
yea, I always install source packages this way:

./configure
make
sudo checkinstall

It then makes a deb package and installs it in the normal way, so it can be removed using synaptic/apt/aptitude

---

### Post by az on 2006-09-06
> **hraposo said:**
> How can I create a debian package from a tar.gz package (from source-code).

Checkinstall is not a great way to make a debian package.

It is actually pretty complicated, because there is a lot in terms of quality-control to worry about.

Look on the wiki.  Motu give regular sessions on how to package things properly.  You can see the class notes.
[https://wiki.ubuntu.com/MOTU/School](https://wiki.ubuntu.com/MOTU/School)

---

### Post by ahaslam on 2006-09-06
Azz, could you tell us what's wrong with checkinstall? It looks so simple in comparison.

Tony.

---

### Post by az on 2006-09-06
> **Anthony Haslam said:**
> Azz, could you tell us what's wrong with checkinstall? It looks so simple in comparison.

Tony.


No dependencies, no conflicts, no pre-intall post-install pre-remove post-remove scripts.  It does not enforce the use of any packaging policies good practice (location of files, etc...)

Lots of other reasons that I cannot think of.

Oh! And it can bork your system.  So can installing things from source; and building them into debian packages does not make that less dangerous, it can make it more so, in fact, since it can lock up the package manager in a conflict it cannot resolve if, for example, your shiny new dep file wants to overwrite another file that is part of another package.

---

### Post by ahaslam on 2006-09-06
Thanks azz,

So I guess that checkinstall is just a convenient way of backing up your compiled sources, so that you don't have to compile again in the event of reinstalling & it's no good if you plan to distribute the deb or use on another pc?

What you said about borking the system is quite concerning, I often use other peoples checkinstalls & compile a few things from source. I guess that I've been lucky ;)

Tony.

---

