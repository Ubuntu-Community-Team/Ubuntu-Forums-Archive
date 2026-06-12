---
title: "Help needed for upgrading to KDE SC 4.4"
date: 2010-02-12
forum: Desktop Environments
---

### Post by syncmasterpt on 2010-02-12
I'm running Kubuntu 9.10 on two computers. In both of them I have enabled the KDE 4.4 backport: [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports) being the only difference that one is the 32 bit version and the other the 64bit version.

On the 32bit version the apt-get update and upgrade cycle detected the new KDE release and installed it without any problems.

On the 64bit version, I got no packages to upgrade.

I've checked the PPA and there are 64bit packages... Any ideas why this isn't working?

Solved -> Installed the meta-package kubuntu-desktop that was missing.

---

