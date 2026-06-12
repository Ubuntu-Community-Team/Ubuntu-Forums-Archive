---
title: "Missing Linux Modules"
date: 2009-05-08
forum: General Help
---

### Post by Laibcoms on 2009-05-08
If I try to re-install: linux-generic && linux-restricted-modules
> 
linux-generic:
 Depends: linux-restricted-modules-generic but it is not going to be installed


If I try to re-install: linux-restricted-modules-generic
> 
linux-restricted-modules-generic:
 Depends: linux-restricted-modules-2.6.28-12-generic  but it is not installable


If I try to re-install: linux-backports-modules-jaunty
> 
linux-backports-modules-jaunty:
 Depends: linux-backports-modules-jaunty-generic but it is not going to be installed


If I try to re-install: linux-backports-modules-jaunty-generic
> 
linux-backports-modules-jaunty-generic:
 Depends: linux-backports-modules-2.6.28-12-generic  but it is not installable


It turns out I have two missing modules that isn't showing up when using apt-get or synaptic.
*linux-restricted-modules-2.6.28-12-generic* && *linux-backports-modules-2.6.28-12-generic* are both missing.

I assume not yet released?  All servers/sources are checked.

I don't normally upgrade without all of related files available, but a few days ago, I accidentally included one of the files and as such, it created a chain reaction of updates.  I just ended up updating the rest of it, and after which, that's when I noticed I can't install/update the restricted and backports modules.

I don't know how to fetch the previous version tho, I haven't tried that yet.  Currently I'm stuck with waiting for those two modules.  Unless it was supposed to be available already?

Thanks a bunch for any information and tips!!

---

### Post by Yellow Pasque on 2009-05-08
I saw another thread about this today. Is there any specific reason you have the backports repo enabled?

---

