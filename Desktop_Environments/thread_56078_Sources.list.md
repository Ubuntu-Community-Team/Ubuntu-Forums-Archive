---
title: "Sources.list"
date: 2005-08-11
forum: Desktop Environments
---

### Post by Owdy on 2005-08-11
Im not sure how to configure that so it would be optimal. What you say my current one? Im not sure about all those multiverse, universe areas what they mean.

> deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main universe restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe multiverse

## security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## KDE
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

## kubuntu digikam, kipi-plugins
deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./

## add Java software
deb [http://jrfonseca.dyndns.org/debian/](http://jrfonseca.dyndns.org/debian/) ./

---

### Post by Lord Illidan on 2005-08-11
If  you live in Finland, everything seems optimal, except the last line. I am not sure that it is good to have a Debian repository on Ubuntu. It could break the distribution.

---

### Post by Owdy on 2005-08-11
[QUOTE=Lord Illidan]If  you live in Finland, everything seems optimal, except the last line. I am not sure that it is good to have a Debian repository on Ubuntu. It could break the distribution.[/QUOTE]
 Yes, i live in finland. Ok, i remove that last line. Thanks!

---

