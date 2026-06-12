---
title: "trouble compiling Atomeye"
date: 2009-10-21
forum: Education &amp; Science
---

### Post by mathyou on 2009-10-21
Hello,

I am trying to compile [Atomeye 3]("http://mt.seas.upenn.edu/Archive/Graphics/A3/A3.html") from the source code using using gcc and gfortran. It is a program for visualizing MD simulations.

Essentially I can get to the point where I cd to A3 and "make", and I get some errors due to a missing mpi.h. I have mpi installed.

I am not so good with makefiles so maybe doing this sort of thing is easy for someone here?

I would really appreciate any help.
Matt

---

### Post by hubie on 2009-10-21
How did you install mpi?  More specifically, do you know if the header files (*.h) and libraries got installed to the usual locations (/usr/local/include, /usr/local/lib, etc.)?  If those files are not where the compiler knows where to normally look, then you need to tell the compiler where to find those files, which you can do by editing the make file.

Could you post the output you get when you run make?

---

### Post by mathyou on 2009-10-21
I installed mpi using synaptic - first trying 'mpi-default-dev' but have also tried installing a few of the other packages.

If I search for mpi.h I get two entries: 

/usr/lib/openmpi/include/openmpi/ompi/mpi/f77
/usr/lib/openmpi/include

When I run make I get some warnings, which I think are ok, and then these errors:

```
In file included from p3dp.h:12,
                 from A.c:13:
P3D.h:7:17: error: mpi.h: No such file or directory
In file included from p3dp.h:12,
                 from A.c:13:
P3D.h:112: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘p3d_global_comm’
P3D.h:160: error: expected declaration specifiers or ‘...’ before ‘MPI_Comm’
P3D.h:167: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘p3d_comm’
P3D.h:177: error: expected declaration specifiers or ‘...’ before ‘MPI_Datatype’
P3D.h:177: error: expected declaration specifiers or ‘...’ before ‘MPI_Comm’
P3D.h:186: error: expected declaration specifiers or ‘...’ before ‘MPI_Datatype’
P3D.h:188: error: expected declaration specifiers or ‘...’ before ‘MPI_Datatype’
P3D.h:188: error: expected declaration specifiers or ‘...’ before ‘MPI_Op’
make: *** [A.o] Error 1

```

The bit I think is relevant in the Makefile is:

```
ifeq ($(SYS), Linux)
 CC = gcc
 LD = gcc
 CCFLAGS = -O3
#  CC = /usr/local/pgcc/bin/gcc #
#  LD = /usr/local/pgcc/bin/g77 -static #
#  CCFLAGS = -Wall -O6 -mpentiumpro -march=pentiumpro -mmx -ffast-math \ #
#     -funroll-loops -inline-functions -s #
# CC = icc -w
# LD = icc -static
#  CCFLAGS = -g #
# CCFLAGS = -O2 -axKWNBP
# USE_MY_LIB = -lAX -lpng -lz -ljpeg -lAtoms -lVecMat3 -lVecMat -lIO -lScalar \
#    -lTimer -L/opt/intel/mkl70/lib/32/ -lmkl_lapack -lmkl_ia32 \
#    -lguide -lXpm -lreadline -lhistory -ltermcap -lsvml -ldl
 USE_MY_LIB = -lAX -lpng -lz -ljpeg -lAtoms -lVecMat3 -lVecMat -lIO -lScalar \
    -lTimer -lmkl_lapack -lmkl_ia32 \
    -lguide -lXpm -lreadline -lhistory -ltermcap -lsvml -ldl \
    -L/usr/lib/openmpi/lib -lmpi
```

which I have tried to edit, but to be honest I'm not a Makefile expert by any means.

Thanks for helping me with this.
m

---

### Post by hubie on 2009-10-21
For gcc, the -I and -L options are for adding custom header and library directories to the header and library default search paths.  In the USE_MY_LIB line in the makefile, add in
```
-I/usr/lib/openmpi/include
```
You'll notice that you already have the mpi library directory added to the library search path (-L/usr/lib/openmpi/lib).

Note:  If there is something like a USE_MY_INCLUDE part of the makefile, or any other part where you see other -I options, add it there instead.

---

### Post by mathyou on 2009-10-21
Thanks, but still no joy :(

Still get the "error: mpi.h: No such file or directory".

mpi is definitely there though so not sure why it isn't found. I actually added the -L/usr/lib/openmpi/lib -lmpi, the original makefile is the bit that is commented out. 

cheers,
m

---

### Post by mathyou on 2009-10-22
If I add ```
-I/usr/lib/openmpi/include
``` to the CFLAGS then I no longer get the 'mpi.h: No such file or directory' error.

However I now get a bunch of this:

```
P3DCore.c:(.text+0x7427): undefined reference to `ompi_mpi_int'
P3DCore.c:(.text+0x74f0): undefined reference to `ompi_mpi_char'
P3DCore.c:(.text+0x7682): undefined reference to `ompi_mpi_comm_world'
P3DCore.c:(.text+0x76d7): undefined reference to `ompi_mpi_op_sum'
P3DCore.c:(.text+0x76df): undefined reference to `ompi_mpi_int'
P3DCore.c:(.text+0x77b0): undefined reference to `ompi_mpi_comm_world'
P3DCore.c:(.text+0x7859): undefined reference to `ompi_mpi_comm_world'

```

any ideas?

---

### Post by mathyou on 2009-10-22
A friend has helped me with this so thread can be closed. :P

---

### Post by akotha on 2009-11-17
I am having a similar problem when working with the hpcc suite. Can u tell me how you fixed it?

---

### Post by mathyou on 2009-11-18
We edited out the p3d objects as we didn't need them, not sure that will help you...

---

