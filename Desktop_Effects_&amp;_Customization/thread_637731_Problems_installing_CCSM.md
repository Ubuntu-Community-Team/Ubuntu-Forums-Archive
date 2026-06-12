---
title: "Problems installing CCSM"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by DAE_JA_VOO on 2007-12-11
How's it guys.

I'm trying to install CCSM on a notebook, but i can't do it via the net, so i downloaded the .deb file. The problem is that i get an error that says the following:

Dependency is not satisfiable: python-support

the thing is that i have 0.6.4 of that file installed, and that's the newest version i can find for download.

Any help please!

---

### Post by mcduck on 2007-12-11
I just run 'apt-cache show compizconfig-settings-manager' to check it's dependencies and this is what I found:

Depends: python, python-central (>= 0.5.8), python-compizconfig, python-gtk2

Make sure you have those installed..

---

