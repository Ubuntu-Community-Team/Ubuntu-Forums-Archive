---
title: "Having trouble installing Plib"
date: 2006-09-19
forum: Gaming &amp; Leisure
---

### Post by Jordash on 2006-09-19
Hey I downloaded Plib from here:

[http://plib.sourceforge.net/](http://plib.sourceforge.net/)

when I do ./configure

at the end it gives the following error message:

checking for glNewList in -lGL... no
checking for glNewList in -lMesaGL... no
configure: error: could not find working GL library

Anyone know how to fix it, I have an ATI card so I have the fglrx accelerator installed.

Thanks, in advance.

---

### Post by islet8 on 2007-05-13
I've got the same problem
I've installed libgl1-mesa-dri and libgl1-mesa-dev and freeglut and .....
with the following command in ubuntu 7.04:
> $ ./configure --with-GL=/usr
but it still error when configuring
any help will be appreciated

---

### Post by cesarespcab on 2009-04-03
Hello
the same problem (ubuntu 8.04, plib1.8.5)
my solution at that point was to install libopensg-qt-dev
and all works fine!

---

