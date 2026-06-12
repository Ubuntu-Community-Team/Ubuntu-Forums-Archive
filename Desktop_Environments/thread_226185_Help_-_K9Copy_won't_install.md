---
title: "Help - K9Copy won't install"
date: 2006-07-30
forum: Desktop Environments
---

### Post by jackkerouac on 2006-07-30
Hello.

Somehow I uninstalled my copy of K9copy. When I go to try and re-install it (I use Gnome), I get the following errors:

```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  k9copy: Depends: kdelibs4 (>= 4:3.3.2-6.2) but it is not installable
          Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
E: Broken packages

```

Any help would be appreciated.

---

### Post by jackkerouac on 2006-07-31
*** Bump ***

---

### Post by az on 2006-07-31
Are all the repositories enabled?  Dapper, Dapper-security and dapper-updates?  Main and universe (for all three)?

---

### Post by jackkerouac on 2006-07-31
> Are all the repositories enabled? Dapper, Dapper-security and dapper-updates? Main and universe (for all three)?

yes. I think K9copy is looking for an older version of kdelibs4, etc.

---

