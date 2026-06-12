---
title: "Installing kdevelop"
date: 2006-06-28
forum: Desktop Environments
---

### Post by ubuntuubuntu on 2006-06-28
When installing kdevelop, I get the following message: 
"Error: Dependecy is not satisfiable: kdelibs4"

Then I tried to install kdelibs4, and it it had another dependecy not satisfiable, and so on. How can I install kdevelop.

Thanks.

---

### Post by digimars on 2006-06-28
The easiest way is probably through Synaptic (System->Administration->Synaptic Package Manager).  Just look for develop, and scroll through it till you find kdevelop, mark it for installation and it should inspect your system for other packages that you may need and install them for you.

---

### Post by aysiu on 2006-06-28
kdevelop appears to have disappeared as of Breezy: > Package kdevelop

    * warty (kde): An IDE for Unix/X11 [universe]
      4:2.1.5.1-7: amd64 i386
    * hoary (kde): An IDE for Unix/X11 [universe]
      4:2.1.5.1-7: amd64 i386 powerpc

---

### Post by digimars on 2006-06-28
There's always Anjuta.

---

### Post by Jucato on 2006-06-28
It's now known as kdevelop3 in Dapper, and requires kdelibs4c2:

[http://packages.ubuntu.com/dapper/kde/kdevelop3](http://packages.ubuntu.com/dapper/kde/kdevelop3)

---

