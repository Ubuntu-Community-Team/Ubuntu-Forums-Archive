---
title: "People using Zelig package and R?"
date: 2007-09-17
forum: Education &amp; Science
---

### Post by madmaxx on 2007-09-17
Hi!
I am trying to install the [Zelig]("http://gking.harvard.edu/zelig/") package  on Edgy Eft but I do not manage. I tried synaptic and the r-cran-zelig package, which seems to install but "library(Zelig)" in R returns a "no package Zelig found". 
Now, I am a bit lost in the install procedure described in the Zelig manual ([PDF]("http://gking.harvard.edu/zelig/docs/static/install.pdf"), 8pp.). 
If someone managed to install Zelig successfully, I would be glad to know how you did it!
Thanks,
madmaxx

---

### Post by akniss on 2007-09-17
Have you tried running R as sudo to install, then entering the commands in the manual?
```
sudo R
source("http://gking.harvard.edu/zelig/install.R")
q()
```
That should install the needed packages.  Now run R as normal user and load Zelig.
```
R
library(Zelig)
```

---

### Post by madmaxx on 2007-09-17
Thanks akniss! Great tip! I followed your suggestion and made it -- nearly. I figured out that "gfortran" was not installed and some stuff is supposed to be compiled with it. (That is definitely missing in the Zelig manual.) Anyway, I tried again and now it nearly finishes the install. But I get two errors back and the packages 'gee' and 'mgcv' do not get installed:

```
* Installing *source* package 'gee' ...
** libs
gfortran   -fpic  -g -O2 -c dgedi.f -o dgedi.o
gfortran   -fpic  -g -O2 -c dgefa.f -o dgefa.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c ugee.c -o ugee.o
gcc -shared  -o gee.so dgedi.o dgefa.o ugee.o -lblas-3 -lgfortran -lm -lgcc_s -lgfortran -lm -lgcc_s -L/usr/lib/R/lib -lR
/usr/bin/ld: cannot find -lblas-3
collect2: ld returned 1 exit status
make: *** [gee.so] Error 1
ERROR: compilation failed for package 'gee'
** Removing '/home/marcus/.R/library/gee'
```

and

```
* Installing *source* package 'mgcv' ...
** libs
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c gcv.c -o gcv.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c gdi.c -o gdi.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c init.c -o init.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c magic.c -o magic.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c mat.c -o mat.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c matrix.c -o matrix.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c mgcv.c -o mgcv.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c qp.c -o qp.o
gcc -I/usr/share/R/include -I/usr/share/R/include     -fpic  -g -O2 -std=gnu99 -c tprs.c -o tprs.o
gcc -shared  -o mgcv.so gcv.o gdi.o init.o magic.o mat.o matrix.o mgcv.o qp.o tprs.o -L/usr/lib/R/lib -lRlapack -lblas-3 -lgfortran -lm -lgcc_s  -L/usr/lib/R/lib -lR
/usr/bin/ld: cannot find -lblas-3
collect2: ld returned 1 exit status
make: *** [mgcv.so] Error 1
ERROR: compilation failed for package 'mgcv'
** Removing '/home/marcus/.R/library/mgcv'
```

---

### Post by akniss on 2007-09-17
It kind of looks like you need to install build-essential packages in order to finish.
```
sudo apt-get install build-essential
```
Try that, then retry the previous steps.  If it works, great! If not, I might not be of any more help. (I'm no programmer, just an R user.)

---

### Post by euler_fan on 2007-09-18
It's my experience the R manuals (and their authors) assume a working knowledge of how to get software onto and off of a machine.

Not always accurate or fair, but otherwise they would spend many many pages going over various install scenarios for different platforms.

---

