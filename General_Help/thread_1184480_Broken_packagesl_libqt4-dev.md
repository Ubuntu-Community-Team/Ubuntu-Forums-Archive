---
title: "Broken packages:l libqt4-dev"
date: 2009-06-11
forum: General Help
---

### Post by Megavolt on 2009-06-11
Hi,

 I have ubuntu 8.04 and have the following problem when I try to install  libqt4-dev.

apt-get install libqt4-dev
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
  libqt4-dev: Depends: libxext-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrandr-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxmu-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libx11-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxt-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
              Depends: libxrender-dev but it is not going to be installed
              Depends: libxcursor-dev but it is not going to be installed
              Depends: libxinerama-dev but it is not going to be installed
              Depends: libxi-dev but it is not going to be installed
              Depends: libxft-dev but it is not going to be installed
              Recommends: libqt4-opengl-dev (= 4.4.3-0ubuntu1.2) but it is not going to be installed
E: Broken packages


 How do I solve this problem?

---

### Post by hansdown on 2009-06-11
Hi Megavolt.

When you open synaptic, click custom filters> broken. It should give you an option to fix broken packages.

---

### Post by Megavolt on 2009-06-11
custom->Broken is empty. But Missing Recommends isn't. But there is not much there I can change or update to fix libqt4-dev.

Please help.

---

### Post by hansdown on 2009-06-11
The package in synaptic may install the dependancies better.

Be sure to click "mark all upgrades", then install.

---

### Post by lamego on 2009-06-11
> libxext-dev (>= **4.3.0.dfsg**.1-4)
Those are Debian package versions, you must have added a debian repository to your list, that will cause serious problems (maybe it did already).
Please remove all the non ubuntu repository sources and then from the terminal type:
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

