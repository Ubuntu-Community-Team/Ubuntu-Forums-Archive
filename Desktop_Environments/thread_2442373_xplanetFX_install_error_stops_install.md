---
title: "xplanetFX install error stops install"
date: 2020-05-02
forum: Desktop Environments
---

### Post by 27grains on 2020-05-02
I installed ubuntu 20.04. I am trying to install xplanetFX and Iam getting an error from gdebi "error Dependency is not satisfiable: python-gtk2"
 Ununtu 20.04 dropped python2. I found [https://linuxconfig.org/install-python-2-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/install-python-2-on-ubuntu-20-04-focal-fossa-linux)
 and installed python2. Then I installed python switcher [https://linuxconfig.org/ubuntu-20-04-python-version-switch-manager](https://linuxconfig.org/ubuntu-20-04-python-version-switch-manager).
 terminal python -V  gives me Python 2.7.18rc1 as my default python version.
 What is the work around the error python-gtk2?  The install stops at the error.
 Thank You.

---

### Post by herve-fournerat on 2020-05-03
Same problem here. Xplanetfx stopped working after upgrading from Bionic to Focal. Unable to install on a fresh install as well.

[EDIT] Installation is possible after installing python-gtk2 and python-glade2 from following links :
[https://www.ubuntuupdates.org/package/core/eoan/universe/base/python-gtk2](https://www.ubuntuupdates.org/package/core/eoan/universe/base/python-gtk2)
[https://www.ubuntuupdates.org/package/core/eoan/universe/base/python-glade2](https://www.ubuntuupdates.org/package/core/eoan/universe/base/python-glade2)

---

