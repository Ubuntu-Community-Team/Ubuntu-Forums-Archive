---
title: "Sakreble install"
date: 2009-07-18
forum: Gaming &amp; Leisure
---

### Post by furqanbhai on 2009-07-18
Can someone help me out with the installation of sakreble using the file I had attached... I tried the steps mentioned in the readme file but it wont compile properly nor does it run after that...Please help...

---

### Post by Grishka on 2009-07-19
> **furqanbhai said:**
> Can someone help me out with the installation of sakreble using the file I had attached... I tried the steps mentioned in the readme file but it wont compile properly nor does it run after that...Please help...

edit the Makefile, and change
```
INCDIR = /usr/include/qt/
``` to ```
INCDIR = /usr/include/qt3/
``` also, edit main.cc and add ```
#include <cstdlib>
```
also, please link to the [official download](http://sourceforge.net/projects/sakreble/files/) next time, instead of attaching the files.

---

### Post by furqanbhai on 2009-07-21
I downloaded comisat-gc 0.5.2 from softpedia and I am unable to install both the games which I downloaded from softpedia.... please help me to install sakreble and comisat 0.5.2. I have downloaded both the files in tar.bz2 format. What needs to be done next????

---

