---
title: "Setting up a Local Yum Repo was Easy"
date: 2008-05-08
forum: Fedora/RedHat and derivatives
---

### Post by Antman on 2008-05-08
Wow... I never thought that setting up my own yum repo for Fedora would be so freaking easy... 

Now I can quickly install updates or packages from my local network at lightning speed. So far I set it up for Fedora 8, once Fedora 9 is final I'll setup one for it too...... Nice!! :guitar:
Step by step instructions are at: [http://www.howtoforge.com/setting-up-a-local-yum-repository-fedora8]("http://www.howtoforge.com/setting-up-a-local-yum-repository-fedora8")
Enjoy.... :KS

---

### Post by pelle.k on 2008-05-09
Nice one. Personally, i don't feel like setting up a web server just because i need to resolve local dependencies for a package, but i might do it if i had server on my network.

I would do it this way;
[http://www.g-loaded.eu/2005/12/11/local-yum-repository/](http://www.g-loaded.eu/2005/12/11/local-yum-repository/)

If you need to resolve repository dependencies on a package that is on your hard drive, nothing beats yum;
```
yum localinstall $rpmpackage --nogpgcheck
```
Nogpgcheck is only needed if the package isn't signed, or you haven't imported the key.

---

