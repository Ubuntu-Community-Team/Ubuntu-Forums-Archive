---
title: "where can i install newer lib's from?"
date: 2005-12-18
forum: General Help
---

### Post by Danielle on 2005-12-18
hi, i bought a Linux magazine with a CD on the cover. the CD has a program i want to install called Kleansweep, the file is called - kleansweep_0.1.9-1_i386.deb

when i tried to install it Terminal's output said:

dependency problems prevent configuration of kleansweep:
 kleansweep depends on libqt3-mt (>= 3:3.3.5); however:
  Version of libqt3-mt on system is 3:3.3.4-8ubuntu5.
 kleansweep depends on libstdc++6 (>= 4.0.2); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
dpkg: error processing kleansweep (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kleansweep

so, can i install - libqt3-mt (>= 3:3.3.5) and libstdc++6 (>= 4.0.2) from somewhere? or is there a way to add to my sources.list and apt-get kleansweep? i checked Synaptic and it only has the versions already installed. thanks

---

### Post by 23meg on 2005-12-19
Both these library versions are in the development release (Dapper) at the moment and may cause instability if you install them. When you need to check out whether some libs you need for a particular app are in Ubuntu, do a search in [http://packages.ubuntu.com](http://packages.ubuntu.com) for "all" distributions.

---

### Post by Danielle on 2005-12-19
thanks, 23meg. so, if i install them will they overwrite the ubuntu versions i already have? is there a way for the libs to work only with Kleansweep?

---

