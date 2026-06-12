---
title: "Help: kdelibs unresolvable dependencies after partial upgrade"
date: 2009-04-08
forum: General Help
---

### Post by ubnewbie2 on 2009-04-08
Update manager is showing greyed out entries...
kdelibs-bin
kfind

This is after it said I should do a partial upgrade.  I did this upgrade and it removed some of my packages, for example mysql admin, and knoda.   I reinstalled mysql admin, but I can't reinstall knoda.  It is claiming unresolvable dependencies.

```
knoda:
 Depends: kdelibs4c2a (>= 4:3.5.9)
 Depends: libhk-kdeclasses7 but it is not going to be installed
 Recommends: kghostview  but it is not installable
```

I tried to install kdelibs4c2a using synaptic and it said

```
kdelibs4c2a:
  Depends: kdelibs-data (<4:3.5.11) but 5:3.4.2.94-1+eeepc1 is to be installed
```

This is all happening on eeebuntu.  

What a mess!  Any hope?

---

### Post by ubnewbie2 on 2009-04-09
Running apt-get at the command line to install knoda produced similar result, but it firmly implies the package is broken.


```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  knoda: Depends: kdelibs4c2a (>= 4:3.5.9)
         Depends: libhk-kdeclasses7 but it is not going to be installed
         Recommends: kghostview but it is not installable
E: Broken packages

```

---

