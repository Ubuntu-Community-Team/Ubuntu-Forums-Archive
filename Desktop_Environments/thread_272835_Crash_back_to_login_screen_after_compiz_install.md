---
title: "Crash back to login screen after compiz install"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Yoguess on 2006-10-07
After installing compiz by following directions at
[http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2](http://chromakode.blogsome.com/2006/02/16/howto-compiz-xgl-on-ubuntu-for-the-morbidly-lazy-2)
everything was cool except the lag.

Someone said to install "ati drivers" so i found a link and installed it

so now when my pc is idle, instead of going in to screensaver, it crashes and im at log in screen.

searched for it but no answers
anyone know of any ideas on how to fix this or go back beofre the "ati driver" install??

---

### Post by bulldog on 2006-10-07
Well you used an old Howro.

You have to use beryl and emerald and take a look at this howto,

[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

---

### Post by Yoguess on 2006-10-07
should i uninstall the old stuff then??

if yes, I know where compiz is and how to remove it, but xgl??

---

### Post by Yoguess on 2006-10-12
anyone???

---

### Post by Yoguess on 2006-10-13
never mind, i figured it out
un installed xserver-xgl
commented out Xsession additions
changed the default session to gnome

Problem solved

---

