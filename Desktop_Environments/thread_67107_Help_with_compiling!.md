---
title: "Help with compiling!"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Sophisto on 2005-09-19
Hi! Im really new to compiling (since you can get away with quite alot using the apt-get install...
Anyway downloaded a source and when I compile with ./configure; make; #make install. I get the following error messages. It seams like I have no c++ compiler.. is that the case? Any suggestions?

finn@cpc2-leic4-3-0-cust165:~/Desktop/mac-3.99-u4-b4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
finn@cpc2-leic4-3-0-cust165:~/Desktop/mac-3.99-u4-b4$ make
make: *** No targets specified and no makefile found.  Stop.

Thanks

---

### Post by macgyver2 on 2005-09-19
You're right, no compiler.  Type

sudo apt-get install build-essential

...then try again.

---

### Post by Sophisto on 2005-09-19
Ok.. that was it... thanks a lot

---

