---
title: "i3 Ubuntu Distro - thoughts?"
date: 2015-05-09
forum: Desktop Environments
---

### Post by CosmicFlux on 2015-05-09
Hi,

Any thoughts on an i3-based Ubuntu derivative? A couple of years ago I was working on a Terminal-based distro that didn't sacrifice GUI functionality, but after my daughter was born it kind of fell by the wayside. 

Since then I've been using the i3wm, which I've found can be configured to produce the same functionality. 

Cosmic

---

### Post by QIII on 2015-05-09
Hello!

i3 is still in the repo I believe.  You could do a minimal install and add i3.  Not sure if it will be the very most current version.

If you want i3.org's current stable version, then their website gives this as how you can install it:

```
sudo echo "deb http://debian.sur5r.net/i3/ $(lsb_release -c -s) universe" >> /etc/apt/sources.list
sudo  apt-get update
sudo apt-get --allow-unauthenticated install sur5r-keyring
sudo apt-get update
sudo apt-get install i3
```

---

