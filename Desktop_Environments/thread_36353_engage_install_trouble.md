---
title: "engage install trouble"
date: 2005-05-23
forum: Desktop Environments
---

### Post by veratyr on 2005-05-23
I'm trying to get engage set up by using this repo

deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/

when i sudo apt-get i get the following:

engage: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
          Depends: libe but it is not going to be installed
          Depends: libecore0 but it is not going to be installed
          Depends: libedb1 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libeet0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
          Depends: libimlib2 but it is not going to be installed
          Depends: examine but it is not going to be installed
E: Broken packages

Any ideas?

---

### Post by DJ_Max on 2005-05-23
First of all you're using a repository for another distribution, so you're asking for trouble. The fact that you can't install it is a good thing, otherwise you're have problems down the line. Debian make packages differently, from the looks of things, the dependency versions.

Libc is a very important package, wouldn't mess with it. What are you trying to install?

---

### Post by veratyr on 2005-05-23
I'm trying to install the engage dock and any required libs.

---

