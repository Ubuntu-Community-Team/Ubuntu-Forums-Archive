---
title: "[WineX] Bison / WineX problem"
date: 2005-04-04
forum: Gaming &amp; Leisure
---

### Post by Lamber on 2005-04-04
> checking for X... no
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for yacc... no
checking for bison... no
checking for yacc... no
configure: error: no suitable bison/yacc found. Please install the 'bison' package.


I'm trying to install wineX (wich I downloaded with CVS)

It seems like i don't have bison installed. No problem, i can install it (i thought)

> robert@ubuntu:~/src/bison/1.875/bison-1.875 $ make
make  all-recursive
make[1]: Entering directory `/home/robert/src/bison/1.875/bison-1.875'
Making all in config
make[2]: Entering directory `/home/robert/src/bison/1.875/bison-1.875/config'
make[2]: Niets te doen voor `all'.
make[2]: Leaving directory `/home/robert/src/bison/1.875/bison-1.875/config'
Making all in po
make[2]: Entering directory `/home/robert/src/bison/1.875/bison-1.875/po'
make[2]: Niets te doen voor `all'.
make[2]: Leaving directory `/home/robert/src/bison/1.875/bison-1.875/po'
Making all in lib
make[2]: Entering directory `/home/robert/src/bison/1.875/bison-1.875/lib'
.deps/argmatch.Po:1: *** meerdere doel patronen.  Stop.
make[2]: Leaving directory `/home/robert/src/bison/1.875/bison-1.875/lib'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/robert/src/bison/1.875/bison-1.875'
make: *** [all] Fout 2


When i do "make / make install / make check" I keep getting this wierd error.

Does anyone has a solution to this problem/? I really would get wineX to work  :razz: 

Many thanks, 

Lamber

---

