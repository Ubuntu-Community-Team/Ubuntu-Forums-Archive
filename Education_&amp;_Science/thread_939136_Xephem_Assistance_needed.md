---
title: "Xephem Assistance needed"
date: 2008-10-05
forum: Education &amp; Science
---

### Post by Oxnyx on 2008-10-05
All,

I followed the instructions posted here:

[http://jalvesaq.googlepages.com/xephem.html](http://jalvesaq.googlepages.com/xephem.html)

All was going fine until I issued the following command:

dpkg-buildpackage -rfakeroot -uc -us

Everything appeared to be doing the right thing, until I received this message:
~~~~~~~~~~~~~~~
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xephem
dpkg-buildpackage: source version 3.7.2-1
dpkg-buildpackage: source changed by Jakson Alves de Aquino <jalvesaq@gmail.com>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: build-essential
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
~~~~~~~~~~~~~~~

I am not sure what is the best/most correct way to proceed. Should I back out (if so, how?)? Override? Any assistance will be most appreciated....

---

