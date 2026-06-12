---
title: "Compile From Source"
date: 2011-01-10
forum: Desktop Environments
---

### Post by shadowfax1 on 2011-01-10
/home/marco/iscan-2.10.0  How do I compile this in terminal

---

### Post by Euruxtaringa on 2011-01-10
1. cd iscan-2.10.0 
2. ./configure
3. make
4. sudo make install

---

### Post by shadowfax1 on 2011-01-10
I never have any luck at this....

marco@marco-System-Product-Name:~$ cd iscan-2.10.0 
marco@marco-System-Product-Name:~/iscan-2.10.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
marco@marco-System-Product-Name:~/iscan-2.10.0$ make
make: *** No targets specified and no makefile found.  Stop.
marco@marco-System-Product-Name:~/iscan-2.10.0$ sudo make install
[sudo] password for marco: 
make: *** No rule to make target `install'.  Stop.
marco@marco-System-Product-Name:~/iscan-2.10.0$

---

### Post by Euruxtaringa on 2011-01-10
You have to install dependencies first.

---

### Post by oldos2er on 2011-01-10
Install the package build-essential first, then any needed dependencies.

---

