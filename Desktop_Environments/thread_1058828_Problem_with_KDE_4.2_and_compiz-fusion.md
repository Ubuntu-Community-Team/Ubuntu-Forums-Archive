---
title: "Problem with KDE 4.2 and compiz-fusion"
date: 2009-02-03
forum: Desktop Environments
---

### Post by svt11 on 2009-02-03
Hello, I have installed ubuntu ultimate edition 2.0 x64. It have already included compiz-fusion and GNOME. I have installed KDE 4.2 using ppa.launchpad.net. When I tried to launch some compiz-fusion effects it didn't work. I have edited xorg.conf for my NVIDIA GeForce 6600 card like it is said on the compiz-fusion wiki. I can't even launch KDE desktop effects. Also I have uninstalled all compiz-fusion and when tried to install again it says - can't install compiz-kde - it depends on libplasma2 which i also couldn't install
```
svt11@svt11-desktop:~$ sudo apt-get install libplasma2
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
  libplasma2: Depends: kdebase-workspace-libs4+5 but it is not going to be installed
              Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but 4:4.2.0-0ubuntu1~intrepid1~ppa5 is to be installed
E: Broken packages
```
Any suggestions?
Thank you

---

### Post by rockmen1 on 2009-02-03
Because compiz in the offcial repository is not compiled against newest kde libraries in ppa, so if you want compiz to work, you have to compile yourself or just upgrade to janty testing.

---

