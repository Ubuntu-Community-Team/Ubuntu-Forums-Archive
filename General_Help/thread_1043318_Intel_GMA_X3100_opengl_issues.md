---
title: "Intel GMA X3100 opengl issues"
date: 2009-01-18
forum: General Help
---

### Post by p.snake on 2009-01-18
Hi, I have a Dell laptop with the card mentioned in the post title, and I have installed Intrepid but whenever compiz is on the opengl screensavers cause the screen to flicker any help please.

---

### Post by p.snake on 2009-01-19
bump anyone?

---

### Post by densou on 2009-01-20
paste here your *xorg.conf* and */var/Xorg.0.log*

useful ? [http://bugs.freedesktop.org/show_bug.cgi?id=19102](http://bugs.freedesktop.org/show_bug.cgi?id=19102)

which dell do you own ?

Latest stable backports are avaiable on there repositories:
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```
[at ease: add them into your */etc/apt/sources.list* and perform a *apt-get update* ; synaptic should notify you about stuff to install]

---

