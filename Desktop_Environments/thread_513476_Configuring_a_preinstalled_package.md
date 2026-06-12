---
title: "Configuring a preinstalled package"
date: 2007-07-30
forum: Desktop Environments
---

### Post by posiedon321 on 2007-07-30
When I install a package it tells me that a package dependency is not installed. So I install it. When I go to reinstall the first package, it tells me that the dependency package is configured yet. How do I go about configuring the package? For example:

"(Reading database ... 88175 files and directories currently installed.)
Preparing to replace kdenlive 0.4-0.0 (using kdenlive_0.4-0.0_i386.deb) ...
Unpacking replacement kdenlive ...
dpkg: dependency problems prevent configuration of kdenlive:
 kdenlive depends on libmlt++0 (>= 0.2.0); however:
  Package libmlt++0 is not configured yet.
 kdenlive depends on libmlt0 (>= 0.2.0); however:
  Package libmlt0 is not installed.
dpkg: error processing kdenlive (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdenlive"

---

### Post by pointone on 2007-07-31
Try:

```
dpkg-reconfigure <package name>
```

---

### Post by posiedon321 on 2007-08-02
> **pointone said:**
> Try:

```
dpkg-reconfigure <package name>
```

I typed "sudo dpkg-reconfigure libmlt++0_0.2.2+cvs20061009-0.0_i386.deb". This is my results:

Package `libmlt++0_0.2.2+cvs20061009-0.0_i386.deb' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: libmlt++0_0.2.2+cvs20061009-0.0_i386.deb is not installed

But yet when I look at the Adept package manager, it is listed as installed.

---

