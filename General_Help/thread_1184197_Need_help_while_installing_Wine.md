---
title: "Need help while installing Wine"
date: 2009-06-10
forum: General Help
---

### Post by rushikesh988 on 2009-06-10
hello friends,

I am trying to install Wine but while configuring the Wine setup I get the follwing error 







Wine Installer v1.0

Running configure...

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for cpp... cpp
checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

Configure failed, aborting install.

--------------------------------------------------------------------------
Plz help me . i can't install any other software too...

---

### Post by michy99 on 2009-06-10
Is there any reason you can't install wine from the repositories instead of compiling it from source?

---

### Post by bolweval on 2009-06-10
Applications/add/remove/search wine / apply changes

---

### Post by Yellow Pasque on 2009-06-10
The "stable" branch of wine is available in the Ubuntu repo. The "development" branch can be installed from Wine's repos: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by DaftPyramid on 2009-06-10
Perhaps you should install the flex package...

Or just download the development package from winehq.

---

### Post by Yellow Pasque on 2009-06-10
> **DaftPyramid said:**
> Perhaps you should install the flex package...

Or just download the development package from winehq.
The OP is missing tons of dependencies besides that one. He/she probably doesn't want to build from source anyway. Also, from Wine site:
> The -dev packages are only needed if you are compiling Winelib applications. In other words, you probably don't need them.

---

### Post by rushikesh988 on 2009-06-11
> **michy99 said:**
> Is there any reason you can't install wine from the repositories instead of compiling it from source?

actually A little problem is that i don't have internet connection on my PC . thats Y I am trying to install it from that Tar.bz2 File..

---

### Post by rushikesh988 on 2009-06-11
Can anybody tell me the Exact or Easy way of installing package from source codes..


I know only 1 way that..

unzipp the package

./configure

make
make install


thats iT!!!!!

---

### Post by Yellow Pasque on 2009-06-11
You're missing lots of dependencies. If you had an internet connection, you could:
```
sudo apt-get build-dep wine
```

---

### Post by oldos2er on 2009-06-11
Instead of installing from source, if you have access to another computer with internet try [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by rushikesh988 on 2009-06-17
> **oldos2er said:**
> Instead of installing from source, if you have access to another computer with internet try [http://keryxproject.org/](http://keryxproject.org/)

that one is too good it not only solved my problem but also helped my friends to give them a software

---

