---
title: "Configuring R to use ACML"
date: 2010-08-23
forum: Education &amp; Science
---

### Post by szembek on 2010-08-23
I am trying to get R to use the ACML BLAS, specifically the 'mp' version for multithreading. 

I have installed acml-4-4-0-gfortran-64bit

I added /opt/acml4.4.0/gfortran64_mp/lib to $LD_LIBRARY_PATH and exported the path. 

I then ran: configure --with-blas="-L/opt/acml4.4.0/gfortran64_mp/lib -lacml_mp"

At the end of the configuration, the only external library listed is readline, and I get the following clues in config.log


> configure:28567: checking for dgemm_ in -L/opt/acml4.4.0/gfortran64_mp/lib -lacml_mp
configure:28588: gcc -std=gnu99 -o conftest -g -O2  -I/usr/local/include  -L/usr/local/lib64 conftest.c -L/opt/acml4.4.0/gfortran64_mp/lib -lacml_mp  -lgfortran -lm -ldl -lm  >&5
conftest.c: In function 'main':
conftest.c:193: warning: implicit declaration of function 'dgemm_'
configure:28588: $? = 0
configure:28595: result: yes
configure:29120: checking whether double complex BLAS can be used
./conftest: error while loading shared libraries: libacml_mp.so: cannot open shared object file: No such file or directory


Any ideas what I'm missing here? It seems like it has to be something simple. I've tried some other methods also for getting acml_mp to work, but this one seems like it should be foolproof if I can figure it out.

I'm running Ubuntu Server 10, Thanks

---

### Post by szembek on 2010-08-24
This part of the error is throwing me off, 

> ./conftest: error while loading shared libraries: libacml_mp.so: cannot open shared object file: No such file or directory

I've triple checked that the path to the libs has been added properly to LD_LIBRARY_PATH.

---

