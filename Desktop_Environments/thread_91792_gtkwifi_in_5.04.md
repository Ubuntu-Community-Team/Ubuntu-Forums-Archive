---
title: "gtkwifi in 5.04"
date: 2005-11-18
forum: Desktop Environments
---

### Post by jbl4me on 2005-11-18
Hello,
     I am trying to get gtkwifi to work.  For some reason it complains about not haveing python extras but python is already installed, according to apt-get.  I have made sure that the repositories are correct as well.

Thanks
Will

---

### Post by kperkins on 2005-11-18
Make sure you have python2.4-gnome2-extras installed, that's the package it's looking for. (or python-gnome2-extras which will select the right extras package for you, in case Hoary isn't using 2.4--I don't remember if it does or not.)

---

