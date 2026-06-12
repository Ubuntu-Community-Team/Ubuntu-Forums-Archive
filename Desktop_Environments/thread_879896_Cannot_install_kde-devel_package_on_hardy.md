---
title: "Cannot install kde-devel package on hardy"
date: 2008-08-04
forum: Desktop Environments
---

### Post by christooss on 2008-08-04
Im having problems installing kde-devel.

apt-get install kde-devel gives me this error:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde-devel: Depends: kdesdk (>= 4:3.4.3) but it is not going to be installed
             Depends: libarts1-dev (>= 1.4.2) but it is not going to be installed
             Depends: kdelibs4-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: kdebase-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: libkonq4-dev (>= 4:3.4.3) but it is not going to be installed
E: Broken packages

```

Than I got through some conclusions. Im having problems directly with libasound2 package when I want to install libasound which is dependecy od kdelibs4-dev:
```

The following packages have unmet dependencies:
  libasound2-dev: Depends: libasound2 (= 1.0.15-3ubuntu4) but 1.0.16-0ubuntu0.1 is to be installed
E: Broken packages

```
If I want to uninstall libasound2 whole bunch of packages "needs" to be removed.
```

sudo apt-get remove libasound2
...


...
0 upgraded, 0 newly installed, 424 to remove and 0 not upgraded.
After this operation, 1478MB disk space will be freed.

```

How to remove libasound2 package without removing whole system?

---

### Post by christooss on 2008-08-04
Ok I found solution for my problems.

I opened Synaptic and than selected problematic package and than from menu Package used Force Version...

Synaptic is great :)

---

