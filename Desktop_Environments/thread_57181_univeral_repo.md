---
title: "univeral repo"
date: 2005-08-15
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-15
how do i add the universal repo?

---

### Post by Kyral on 2005-08-15
You mean the Universe and Multiverse? Quite easy my good man! Just add the following lines to your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

You'd also be wise to add the Backports to your list. Mucho good stuff there :D

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Just add those in, save, and do a sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by SFN on 2005-08-15
If you mean universe, the instructions for that (as well as multiverse and backports) are [here](http://ubuntuguide.org/#extrarepositories).

---

