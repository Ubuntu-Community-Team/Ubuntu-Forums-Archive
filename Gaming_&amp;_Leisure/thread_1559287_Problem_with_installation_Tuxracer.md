---
title: "Problem with installation Tuxracer"
date: 2010-08-23
forum: Gaming &amp; Leisure
---

### Post by x_master222 on 2010-08-23
I tried to install the game called Tuxracerm, I followed installation manual, but when I enter into the terminal "./configure" the problem appears:

marek@marek-nb:~/Downloads/tuxracer-0.61$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.

What should I do ?

Here is the installation manual I followed: [http://tuxracer.sourceforge.net/manual.html#installlinux](http://tuxracer.sourceforge.net/manual.html#installlinux)

Thank you

---

### Post by alexandrius on 2010-08-23
why do you compile, when there is done this already. Check Software Center

---

### Post by Perfect Storm on 2010-08-23
x_master222, you need to install the some compiling tools;
```
sudo apt-get install build-essential
```

---

### Post by x_master222 on 2010-08-23
now: 

configure: error: Cannot find Tcl library

(I opened Synaptic and installed Tcl before installing Tuxracer)

---

### Post by Perfect Storm on 2010-08-23
> **x_master222 said:**
> now: 

configure: error: Cannot find Tcl library

(I opened Synaptic and installed Tcl before installing Tuxracer)

Wait a minut. If you installed Tuxracer already - you don't need to compile and build it from source.

99% of the stuff you need is already available through ubuntu repositories. I think you should also check Playdeb (see my signature).

to the "tcl" question; When compiling stuff under Ubuntu (and other Debian based systems) you need to install the -dev package of it as well.

---

### Post by x_master222 on 2010-08-23
I am just trying to install it. It is not installed. 

I downloaded these two files: [http://tuxracer.sourceforge.net/download.html](http://tuxracer.sourceforge.net/download.html)

and followed the manual. How else can I install it using ubuntu repositories ?

---

### Post by Perfect Storm on 2010-08-23
It's because you're properly looking for tuxracer which haven't been worked on since year 2001. check for extremetuxracer.

---

### Post by x_master222 on 2010-08-23
I did not know that  ... thank you .. extremetuxracer works!

---

### Post by JCyberinux on 2010-10-21
> **Artificial Intelligence said:**
> It's because you're properly looking for tuxracer which haven't been worked on since year 2001. check for extremetuxracer.

i know that this is a 2 months old thread but im going to say something,
thank you sir for your advice on extreme tuxracer... i've also downloaded the tuxracer as x_master222 does. and also i encountered same problem as he is. 

i am now in the process of apt-get install extremetuxracer, and it works... and i'm just waiting to be finish. thank you so kindly.

---

### Post by Perfect Storm on 2010-10-21
My pleasure ^_^


(I have also marked the thread solved).

---

