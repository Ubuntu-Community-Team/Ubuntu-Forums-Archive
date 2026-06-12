---
title: "Opera 9 Beta - installing?"
date: 2006-02-09
forum: Desktop Environments
---

### Post by myke on 2006-02-09
Though my primary browser will remain Firefox, I want to try the new beta 9 version of Opera as it has these new widget features that will run with the installed version of Opera 9 without actually having it open at the same time continually.  Opera provides a debian version of it but I'm not sure how to install it as, frankly, though I've customized my system nicely it's been mostly thru synaptic!

this is the file in my home directory:  opera-static_9.0-20060206.1-qt_en_i386.deb

How do I install this (thru the terminal I'm presuming) and is this a general way to do so for any deb file not in the repositories I might want to install from a separate download?

---

### Post by o_fortuna on 2006-02-09
[QUOTE=myke]Though my primary browser will remain Firefox, I want to try the new beta 9 version of Opera as it has these new widget features that will run with the installed version of Opera 9 without actually having it open at the same time continually.  Opera provides a debian version of it but I'm not sure how to install it as, frankly, though I've customized my system nicely it's been mostly thru synaptic!

this is the file in my home directory:  opera-static_9.0-20060206.1-qt_en_i386.deb

How do I install this (thru the terminal I'm presuming) and is this a general way to do so for any deb file not in the repositories I might want to install from a separate download?[/QUOTE]
Just open the terminal and type this:
```
dpkg -i opera-static_9.0-20060206.1-qt_en_i386.deb
```
The general command to install a .deb is "dpkg -i". I think Ubuntu 6.04 will have a way to doubleclick-install .deb files.

---

### Post by atoponce on 2006-02-09
Simple, in a terminal, from the location that the file is location, type:

```
dpkg -i opera-static_9.0-20060206.1-qt_en_i386.deb
```

---

