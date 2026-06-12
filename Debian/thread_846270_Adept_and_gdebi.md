---
title: "Adept and gdebi"
date: 2008-07-01
forum: Debian
---

### Post by Fred_E _krugar on 2008-07-01
Well folks I am using Lenny and I am having some problems.

Fist I can not seem to install Adept package manger, apt says it is missing??? 

Second I cannot install deb packages, apt says that package gdebi is missing or referred to a different package.


WTH do I need to do help plz Kerry_S even though you are a traitor, you are probably the most knowledgeable on debian.

---

### Post by Fred_E _krugar on 2008-07-01
Ok I see that gdebi is now gdeb in lenny.

Does anybody know about the Adept Package Manager??

---

### Post by basenvironment on 2008-07-01
buggy...i think is the problem
plenty of threads about it at [http://forums.debian.net](http://forums.debian.net)

---

### Post by benuski on 2008-07-02
Yep, its really buggy and so is only available from experimental.  You'd be better off using synaptic if you need a graphical interface.

---

### Post by cdiem on 2008-07-02
You can try with [kpackage]("http://en.wikipedia.org/wiki/KPackage") as well, it has a nice graphical interface for KDE.

Adept seems to have packages only for Stable and for Experimental:
[http://packages.debian.org/search?keywords=adept](http://packages.debian.org/search?keywords=adept)

---

### Post by Fred_E _krugar on 2008-07-02
> **cdiem said:**
> You can try with [kpackage]("http://en.wikipedia.org/wiki/KPackage") as well, it has a nice graphical interface for KDE.

Adept seems to have packages only for Stable and for Experimental:
[http://packages.debian.org/search?keywords=adept](http://packages.debian.org/search?keywords=adept)


That was what I was actualy looking for I just could not remember the name thanks.

---

### Post by markharding557 on 2008-07-05
> **Fred_E _krugar said:**
> Well folks I am using Lenny and I am having some problems.

Fist I can not seem to install Adept package manger, apt says it is missing??? 

Second I cannot install deb packages, apt says that package gdebi is missing or referred to a different package.


WTH do I need to do help plz Kerry_S even though you are a traitor, you are probably the most knowledgeable on debian.

In a root terminal type> dpkg -i packagename.deb and thats it job done

---

