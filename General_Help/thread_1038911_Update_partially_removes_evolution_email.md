---
title: "Update partially removes evolution email"
date: 2009-01-14
forum: General Help
---

### Post by BigCityCat on 2009-01-14
There was an update that was done via the update manager and now evolution does not function. I ended up removing what was left but it won't let me reinstall because it says that i have other software with unresolved issues.

Add remove says

Cannot install 'evolution'

This application conflicts with other installed software. To install 'evolution' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


synaptic says

the following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.

evolution:
  Depends: evolution-common (=2.24.2-0ubuntu1) but 2.24.3-0ubuntu1 is to be installed
 Recommends: evolution-plugins but it is not going to be installed





Thanks for any help.

---

### Post by BigCityCat on 2009-01-14
This is bs though. How am I going to use this operating system exclusively if it does updates and messes up a system that was working fine. I will come back later but for now I have to reboot and use my dependable Vista partition.

---

### Post by dcstar on 2009-01-14
> **BigCityCat said:**
> This is bs though. How am I going to use this operating system exclusively if it does updates and messes up a system that was working fine. I will come back later but for now I have to reboot and use my dependable Vista partition.

"Messes up" after you removed a package that is intertwined with other packages.

All you had to do was post here with whatever the original problem was before doing something that has turned out to be a mistake, not complain that part of a system is now not functioning correctly after your actions.

Do you want help or not, or is having to wait for a few minutes too much trouble?

---

### Post by wilcs on 2009-01-14
Same problem as BigCityCat.


Update manager informed me that there are updates avaiable.

I updated and was informed that it can only do a partial upgrade now.

So I let it continue.

I ended up with:
evolution-common, evolution-data-server & evolution-data-server 
upgraded to 2.24.3-0ubuntu1.
BUT for evolution itself only version 2.24.2-0ubuntu1 is available.

Now in exactly the same position as BigCityCat.


Do we wait for the new version of evolution?
{ Running 64 bit Ubuntu )

---

### Post by horace on 2009-01-14
I had this happen too (think because backports are enabled?) but was able to get round it by using Synaptic to force the versions of common and data-server back to 2.24.2 (package/force version), then reinstalling evolution - worked for me.
hth

---

### Post by wilcs on 2009-01-14
Thanks Horace.

That worked for me too.

---

