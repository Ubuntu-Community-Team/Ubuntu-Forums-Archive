---
title: "Package Always Tagged 'upgradable'"
date: 2007-08-14
forum: Desktop Environments
---

### Post by armware on 2007-08-14
When I run Adept Manager (or apt-get, aptitude, ect) it always says that the package 'compiz-core' is upgradable. I can upgrade the package, which succeeds, then check for updates again and there it is.

It is quite possible that something happened during an install/upgrade, so the first thing I did was completely remove (and purge) compiz, run apt-get clean, then reinstall to make sure it redownloads the package (which it did).

Ran an upgrade, sure enough it's upgradable still.

There is a slight chance it's the compiz repo, but very doubtful as I haven't seen/heard anything about this. It seems more to me like an installed software database issue.

How can I fix this?

---

### Post by luisromangz on 2007-08-14
Yes, is the Compiz for Ubuntu "official" repos which have that ever-upgrading package. I preffer Treviño's repository for compiz related packages.

---

