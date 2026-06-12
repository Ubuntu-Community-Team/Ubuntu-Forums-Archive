---
title: "how can i downgrade a package"
date: 2006-09-29
forum: Desktop Environments
---

### Post by shizow on 2006-09-29
i get the following 

```

 apt-get install libcairo2-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installed
E: Broken packages

```

somehow i installed a 3rd party packages which does not have a dev package, how can i downgrade libcairo2?

---

### Post by lagagnon on 2006-09-29
to downgrade anything:

apt-get install exactnameandversionofpackage

---

### Post by dcstar on 2006-09-30
> **shizow said:**
> i get the following 
......
somehow i installed a 3rd party packages which does not have a dev package, how can i downgrade libcairo2?

Start Synaptic, select the package and use the "Force Version" option.

---

