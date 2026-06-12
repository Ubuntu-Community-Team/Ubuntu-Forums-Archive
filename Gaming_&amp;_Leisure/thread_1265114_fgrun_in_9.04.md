---
title: "fgrun in 9.04"
date: 2009-09-13
forum: Gaming &amp; Leisure
---

### Post by ubudog on 2009-09-13
Hi, I was wondering where I would get fgrun for Ubuntu 9.04.  Any ideas?

---

### Post by Perfect Storm on 2009-09-13
You could try these; [http://www.viciouslime.co.uk/downloads/cat_view/2-debs](http://www.viciouslime.co.uk/downloads/cat_view/2-debs)
Other than that you can grab the source code here; [http://sourceforge.net/projects/fgrun/](http://sourceforge.net/projects/fgrun/)

---

### Post by ubudog on 2009-09-13
> **Artificial Intelligence said:**
> You could try these; [http://www.viciouslime.co.uk/downloads/cat_view/2-debs](http://www.viciouslime.co.uk/downloads/cat_view/2-debs)
Other than that you can grab the source code here; [http://sourceforge.net/projects/fgrun/](http://sourceforge.net/projects/fgrun/)

Ok, thanks for the help :o

---

### Post by ubudog on 2009-09-13
How would I go about installing it?

---

### Post by Perfect Storm on 2009-09-13
The source or .deb?

---

### Post by ubudog on 2009-09-13
I am going to use the source.  I have downloaded it and I am wondering how to install it.

---

### Post by Perfect Storm on 2009-09-13
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential plib1.8.4-dev zlib1g-dev libxext-dev libxi-dev libice-dev libxmu-dev libboost1.37-dev

cd ~/Desktop
wget http://sourceforge.net/projects/fgrun/files/fgrun/1.5.1/fgrun-1.5.1.tar.gz/download
tar zxfv fgrun-1.5.1.tar.gz
cd fgrun-1.5.1
./configure 
make
sudo make install
```

Something like this.

---

### Post by ubudog on 2009-09-16
> **Artificial Intelligence said:**
> ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential plib1.8.4-dev zlib1g-dev libxext-dev libxi-dev libice-dev libxmu-dev 

cd ~/Desktop
wget http://sourceforge.net/projects/fgrun/files/fgrun/1.5.1/fgrun-1.5.1.tar.gz/download
tar zxfv fgrun-1.5.1.tar.gz
cd fgrun-1.5.1
./configure 
make
sudo make install
```

Something like this.

Sweet!  Thanks, just what I was looking for.

---

### Post by ubudog on 2009-09-16
Thanks for the reply, but when I got to make, it said "make: *** No targets specified and no makefile found.  Stop."  Any ideas?

---

### Post by Perfect Storm on 2009-09-17
Give me the output of **./configure**

---

### Post by ubudog on 2009-09-17
> **Artificial Intelligence said:**
> Give me the output of **./configure**

This is quite long, but here it is.

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for boostlib >= 1.34.0... configure: error: We could not detect the boost libraries (version 1.34 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option.  If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.

---

### Post by Perfect Storm on 2009-09-17
> checking for boostlib >= 1.34.0... configure: error: We could not detect the boost libraries (version 1.34 or higher). If you have a staged boost library (still not installed) please specify $BOOST_ROOT in your environment and do not give a PATH to --with-boost option. If you are sure you have boost installed, then check your version number looking in <boost/version.hpp>. See [http://randspringer.de/boost](http://randspringer.de/boost) for more documentation.

```
sudo apt-get install libboost1.37-dev
```

---

### Post by ubudog on 2009-09-19
> **Artificial Intelligence said:**
> ```
sudo apt-get install libboost1.37-dev
```

Alright, downloading.  Will post back later.  Thanks!

---

### Post by ubudog on 2009-09-19
Ok, got it installed, at the end of configure, it said it couldn't find simgear.  I've heard of that before, but where can I get it?

---

### Post by ubudog on 2009-09-19
Nevermind about my last post, I installed simgear, just need to install a couple other things and I think I have it working!  Thanks for the help so much!

---

### Post by Perfect Storm on 2009-09-19
My pleasure.

---

### Post by ubudog on 2009-09-19
Actually, the ./configure finally worked but now when I do make, it gives me a lot of errors like "No such file or directory"  Can you help?  Thanks.

---

### Post by Perfect Storm on 2009-09-19
please attach a txt with both configure and make

Remember to run

**make clean **

before re-configure

---

### Post by ubudog on 2009-09-19
> **Artificial Intelligence said:**
> please attach a txt with both configure and make

Remember to run

**make clean **

before re-configure

Thanks for the help, but I'll just get the deb.  Should've done that first.

---

### Post by ubudog on 2009-09-19
Ok, got the deb and opened it, it says this "Error: Dependency is not satisfiable: simgear0 (>= 1.0.0-1)"  Can you help? Thanks.

---

### Post by Perfect Storm on 2009-09-19
> **ubudog said:**
> Ok, got the deb and opened it, it says this "Error: Dependency is not satisfiable: simgear0 (>= 1.0.0-1)"  Can you help? Thanks.

uninstall the old one you got and install simgear1.0.0 from synaptic.

---

### Post by ubudog on 2009-09-19
> **Artificial Intelligence said:**
> uninstall the old one you got and install simgear1.0.0 from synaptic.

I currently have simgear1.0.0.

---

