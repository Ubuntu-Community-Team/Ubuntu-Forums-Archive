---
title: "Fix For Synaptic Problems"
date: 2006-09-11
forum: Desktop Environments
---

### Post by cyclone on 2006-09-11
im getting this error when ever i try to load synaptic

E: Type 'http://ubuntu-backports.mirrormax.net/' is not known on line 39 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


any help would be greatly appreciated.

---

### Post by Big_J on 2006-09-11
comment out (or delete if you don't want to use it) [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) from sources.list

do 
sudo gedit /etc/apt/sources.list
and comment or delete line 39

---

