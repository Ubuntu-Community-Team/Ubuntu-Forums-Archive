---
title: "java"
date: 2005-09-14
forum: Desktop Environments
---

### Post by LucoB on 2005-09-14
Hi, 

This may sound like a dumb question but how do I install java on Ubuntu? I have looked at the package and its not clear which ones i need. 
Also how do I insall equlipse? 


Thanks.

---

### Post by xaverx on 2005-09-14
[QUOTE=LucoB]Hi, 

This may sound like a dumb question but how do I install java on Ubuntu? I have looked at the package and its not clear which ones i need. 
Also how do I insall equlipse? 


Thanks.[/QUOTE]

Ist simple:
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

before check your repositories
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

uncheck # in /etc/atp/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by McAviti on 2005-09-14
Since I need a bundle of different JDKs for development, I installed the versions directly from java.sun.com manually to /opt.
Java is not (yet) free software as in GPL (and not very popular amongst some Linux developers  ;-) ) it is not supported by the distributions very smoothly. Anyway, installing it manually was always easy and painless for me.

McA

---

