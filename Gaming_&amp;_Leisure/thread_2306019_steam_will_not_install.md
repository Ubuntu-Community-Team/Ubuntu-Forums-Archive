---
title: "steam will not install"
date: 2015-12-11
forum: Gaming &amp; Leisure
---

### Post by nero60142 on 2015-12-11
I am new (today) to ubuntu and when i tried to install steam i got the following error, any help would be appreciated


The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue:

---

### Post by nero60142 on 2015-12-11
resolved by doing this
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install steam

---

