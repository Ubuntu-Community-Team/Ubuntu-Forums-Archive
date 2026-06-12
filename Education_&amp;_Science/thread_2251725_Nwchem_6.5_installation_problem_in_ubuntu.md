---
title: "Nwchem 6.5 installation problem in ubuntu"
date: 2014-11-06
forum: Education &amp; Science
---

### Post by ramadavid on 2014-11-06
Dear Friends,
        I am novice to the Nwchem. I am using ubuntu 12.04 LTS 32 bit version.
I tried to install nwchem 6.5 by using the ./contrib/distro-tools/build_nwchem | tee build_nwchem.log as mentioned in 
[http://www.nwchem-sw.org/index.php/Compiling_NWChem](http://www.nwchem-sw.org/index.php/Compiling_NWChem)



 I got following out put : 

```
gfortran: error: unrecognized command line option ‘-q64’
gcc: error: unrecognized command line option ‘-q64’
g++: error: unrecognized command line option ‘-q64’
gcc: error: unrecognized command line option ‘-q64’
/usr/bin/ld: cannot find -lmkl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lacml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcxml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscs
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcomplib.sgimath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lsunmath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -latlas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto2
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lessl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscalapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -llapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lf77blas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lmkl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lacml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcxml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscs
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcomplib.sgimath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lsunmath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -latlas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto2
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lessl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscalapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -llapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lf77blas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lmkl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lacml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcxml
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscs
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcomplib.sgimath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lsunmath
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -latlas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto2
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lgoto
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lessl
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lscalapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -llapack
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lcblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lblas
collect2: error: ld returned 1 exit status
/usr/bin/ld: cannot find -lf77blas
collect2: error: ld returned 1 exit status
=== Initial guesses for linear algebra libraries ===
BLAS      =   integer-size =  8
LAPACK    =   integer-size =  8
SCALAPACK =   integer-size =  0
=== Working out how to proceed =====================
No ScaLAPACK found, so no ScaLAPACK will be used
BLAS and LAPACK are OK
===============
Building NWChem
===============

NWCHEM_TOP         = /home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10
NWCHEM_TARGET      = LINUX
NWCHEM_MODULES     = all python
NWCHEM_MPIF_WRAP   = /usr/bin/mpif90
NWCHEM_MPIC_WRAP   = /usr/bin/mpicc
NWCHEM_MPICXX_WRAP = /usr/bin/mpicxx
NWCHEM_LONG_PATHS  = Y
USE_NOFSCHECK      = Y
USE_MPI            = y
USE_MPIF           = y
USE_MPIF4          = y
MPI_INCLUDE        = -I/usr/lib/openmpi/include -I/usr/lib/openmpi/lib
MPI_LIB            = -L/usr//lib -L/usr/lib/openmpi/lib
LIBMPI             = -lmpi_f90 -lmpi_f77 -lmpi -ldl -lhwloc
MPI_F90            = gfortran
MPI_CC             = gcc
MPI_CXX            = g++
ARMCI_NETWORK      =
MSG_COMMS          = MPI
PYTHON_EXE         = /usr/bin/python
PYTHONVERSION      = 2.7
PYTHONPATH         = ./:/home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/contrib/python/
PYTHONHOME         = /usr /usr
PYTHONLIBTYPE      = so
=== configure GA ===

_
_
- ( a lot of output )
-
-
Making all in pfftwrap
gfortran -c -m32 -march=pentium4 -mtune=pentium4 -O2 -ffast-math -Wuninitialized -fno-aggressive-loop-optimizations -I.  -I/home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/src/include -I/home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/src/tools/install/include -DLINUX -DGFORTRAN -DGFORTRAN -DCHKUNDFLW -DGCC4 -DGCC46 -DPARALLEL_DIAG -DEMSLFFT  nwfft3d.F
Got lock on /home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/lib/LINUX/libpfft.lock
ar r /home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/lib/LINUX/libpfft.a nwfft3d.o
ranlib /home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/lib/LINUX/libpfft.a
Making libraries in python
/home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/bin/LINUX/depend.x -I/usr
$(LIBRARY_PATH)(nwchem_wrap.o):    $(INCDIR)/typesf2c.h $(INCDIR)/macdecls.h $(INCDIR)/ga.h 
$(LIBRARY_PATH)(python_input.o):    $(INCDIR)/rtdb.fh $(INCDIR)/inp.fh $(INCDIR)/errquit.fh 
$(LIBRARY_PATH)(task_python.o):    $(INCDIR)/typesf2c.h $(INCDIR)/macdecls.h $(INCDIR)/ga.h 
$(LIBRARY_PATH)(nw_inp_from_string.o):    $(INCDIR)/ga.h 
/usr/include/python2.7 -I/usr
/bin/sh: 1: /usr/include/python2.7: Permission denied
gfortran -c -m32 -march=pentium4 -mtune=pentium4 -O2 -g -fno-aggressive-loop-optimizations  -I. -I/usr
gfortran: fatal error: no input files
compilation terminated.
make[1]: *** [/home/prashant/Software/nwchem/Nwchem-6.5.revision26243-src.2014-09-10/lib/LINUX/libnwpython.a(python_input.o)] Error 4
make: *** [libraries] Error 1
gfortran -c -fno-second-underscore -I../../src/tools/install/include             mov2asc.F
gfortran -fno-second-underscore -I../../src/tools/install/include             -o mov2asc mov2asc.o -L../../src/tools/install/lib -lga -larmci     -L../../lib/LINUX -lnwcutil -L/usr//lib -L/usr/lib/openmpi/lib -lmpi_f90 -lmpi_f77 -lmpi -ldl -lhwloc  
gfortran -c -fno-second-underscore -I../../src/tools/install/include             asc2mov.F
gfortran -fno-second-underscore -I../../src/tools/install/include             -o asc2mov asc2mov.o -L../../src/tools/install/lib -lga -larmci     -L../../lib/LINUX -lnwcutil -L/usr//lib -L/usr/lib/openmpi/lib -lmpi_f90 -lmpi_f77 -lmpi -ldl -lhwloc  
=== all done ===

```

when I change directory to the ,.../bin/Linux I get file depend.x ..

Is it right or any problem in compilation ??/

I really dont know what I HAVE TO DO ?? Is there any wrong in my command or system ??

I will be thankfull for help and suggestion..

I think  same problem also mentioned here

[http://www.nwchem-sw.org/index.php/Special:AWCforum/st/id495/Problems_compiling_nwchem_with_o....html](http://www.nwchem-sw.org/index.php/Special:AWCforum/st/id495/Problems_compiling_nwchem_with_o....html)
 

With regards,
RamaDavid

---

### Post by gordintoronto on 2014-11-06
Why don't you install it from Software Center? Also, please look up "code" tags for posting command-line output.

---

### Post by ramadavid on 2014-11-07
This is the 6.5 version and sofware centre has old version.
 For my work I need the latest version 6.5.
 

I will be thankful for the help and suggestion 




RamaDavid

---

### Post by Sef on 2014-11-08
> [COLOR=#000000] Also, please look up "code" tags for posting command-line output.[/COLOR]

Done.

---

