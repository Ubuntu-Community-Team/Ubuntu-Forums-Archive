---
title: "Error while compiling The mana world"
date: 2005-11-04
forum: Gaming &amp; Leisure
---

### Post by Lifesteeler on 2005-11-04
hi, i get this error when im compiling the mana world from source, 
EDIT: this is what seems to be the error message in its whole... also there are no missing libraries before it.

: undefined reference to `non-virtual thunk to gcn::TextBox::mousePress(int, int , int)'
collect2: ld returned 1 exit status
make[1]: *** [tmw] Error 1
make[1]: Leaving directory `/home/lifesteeler/Desktop/Installs/tmw/tmw-0.0.17/sr c'
make: *** [install-recursive] Error 1


anyone know what to do? since im stuck...

---

### Post by Sslaxx on 2005-11-04
Looks like an incomplete thing to me. Does it say anything about missing libraries before that error, or syntax errors or the like?

---

### Post by Lifesteeler on 2005-11-04
nope, it runs perfectly until it stops with that error...

---

### Post by madjo on 2005-11-05
when you ran ./configure did that throw any issues/problems at you?

---

### Post by Bjørn on 2005-11-17
[QUOTE=Lifesteeler]: undefined reference to `non-virtual thunk to gcn::TextBox::mousePress(int, int , int)'
collect2: ld returned 1 exit status[/QUOTE]
It's a linker error related to the [Guichan]("http://guichan.sourceforge.net/") library. The cause of this is probably that the guichan-dev package you installed was compiled with an incompatible version of GCC than the GCC you are trying to compile [The Mana World](http://themanaworld.org/) with.

One solution would be to compile and install Guichan manually, I did this on my system using the $HOME prefix (./configure --prefix=$HOME) so that I didn't need to be root for it and there was no way it could mess up later Guichan installs. Of course that'd also require setting up CPLUS_INCLUDE_PATH, LD_LIBRARY_PATH and LIBRARY_PATH environment variables in your ~/.bashrc to make sure include and library files are found.

---

