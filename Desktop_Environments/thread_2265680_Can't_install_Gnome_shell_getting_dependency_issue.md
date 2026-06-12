---
title: "Can't install Gnome shell? getting dependency issues"
date: 2015-02-16
forum: Desktop Environments
---

### Post by rimside2 on 2015-02-16
I just reinstalled Ubuntu and remembered that I preferred the Gnome shell over Unity, and while trying to install Gnome in 14.04 I came across some dependdncy errors, and was wondering how to fix them? I never really got into fixing things with 12.10 as I didn't usually get many errors.

This is the dependency errors I have gotten:

gnome-shell: Depends: libgjs0-libmozjs-24-0 but it is a virtual package
             Depends: libpulse-mainloop-glib0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
             Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
             Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1 is to be installed
             Depends: gnome-shell-common (= 3.12.2-0ubuntu0~trusty2) but 3.12.2-0ubuntu0~trusty2 is to be installed

---

### Post by mc4man on 2015-02-17
You should mention what gnome 3 ppa or ppa's you are using
(quite likely the use of requires a sudo apt-get dist-upgrade

---

