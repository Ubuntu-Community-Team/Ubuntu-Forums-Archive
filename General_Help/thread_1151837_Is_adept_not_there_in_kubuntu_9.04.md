---
title: "Is adept not there in kubuntu 9.04?"
date: 2009-05-07
forum: General Help
---

### Post by mahela007 on 2009-05-07
I just upgraded to kubuntu 9.04 via the alternate CD and found that the package manager adept is no longer there. Is there a package manager that's been used instead of adept?

---

### Post by jerrrys on 2009-05-07
i do not run 904, but this may help...

[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by mahela007 on 2009-05-07
A very useful link but it doesn't really say if Adept has been dropped in kubuntu 9.04 or .. well otherwise it's a bug in my update

---

### Post by growled on 2009-05-07
I believe Adept has been replaced with KPackageKit.

---

### Post by mahela007 on 2009-05-07
Sure looks like it.. thanks for your replies.

---

### Post by tremolux on 2009-06-19
I really liked adept a lot because it provided a lot of flexibility and was good at "finding" packages. I hope the new package manager works at least as well as adept; I was not satisfied with the other package/update tools available on earlier versions of Ubuntu.

---

### Post by chandra on 2009-06-19
I am running Kubuntu Jaunty 9.04 on an AMD 64 PC and find that I have both adept and kpackage-kit on my system:
```
dpkg -l adept kpackagekit
```
gives
ii  adept          3.0~beta4ubunt package management suite for KDE
ii  kpackagekit    0.4-0ubuntu8.1 KDE package management tool using PackageKit

So, both are installed and Adpet appears on its own line in the KDE classic menu as

Adept Installer Add/Remove Software

I must add that I upgraded from Interpid, though.

---

### Post by kuja on 2009-06-19
Adept is still in the repositories, it just isn't installed by default now.

---

### Post by Chris Musampa on 2009-06-19
I've read of problems with both adept and kpackagekit in jaunty.  I do most package management from the command line but occasionally find synaptic useful, I'd rather not have any gnome apps on my system but rather that than a dodgy package manager.

---

