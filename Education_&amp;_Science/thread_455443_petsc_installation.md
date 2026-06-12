---
title: "petsc installation"
date: 2007-05-26
forum: Education &amp; Science
---

### Post by ali780 on 2007-05-26
Hello
I want to install petsc 2.3.3 on my ubuntu but I don't know how can i do it. Please if somebody knows help me.
Thank you

---

### Post by u04f061 on 2007-05-29
> **ali780 said:**
> Hello
I want to install petsc 2.3.3 on my ubuntu but I don't know how can i do it. Please if somebody knows help me.
Thank you

do the following steps.> sudo apt-get update

wait for some minutes until it stops fetching. after that > sudo apt-get install petsc-dev

but this is package 2.3.2

---

### Post by arooabba on 2007-05-30
[FONT="Verdana"][SIZE="4"][SIZE="3"][SIZE="2"]I typically get a lot of help here, so ... I want to do something. 
HERE WE GO !!

1. PETSc is built on top of BLAS and Lapack so you need to install them. Without properly installed BLAS and LAPACK, Petsc will be very slow.

-- Open synaptic package manager, search for "atlas" and install them. 
ATLAS is the open-source based BLAS and I beleive it is the fastest, even faster than Intel MKL at least for my FEM applications. 

-- This pre-built BLAS(ATLAS) is not completely optimized version. It is optimized for X86 machine, but not yours like Pentium Moblie, Pentium 4, or AMD Opeteron. I did some tests (mainly BLAS gemm) and found that the pre-compiled version only showed about 85% of its possible peak performance. 

-- So you may want to download source code from [http://math-atlas.sourceforge.net/](http://math-atlas.sourceforge.net/). Current stable version is 3.6.0 (I'm using this). Nice thing about using ATLAS is that it comes with some of the LAPACK routines that are sufficient enough to compile PETSc. I strongly recommend you to compile ATLAS on your machine. It will probably take 1 hour because ATLAS performs huge tests during the compilation.

-- If you use gcc, then use gcc version of[COLOR="Red"] 3.4, not 4.1[/COLOR]. The compiled code using gcc-4.1 will be slower. Install gcc-3.4 using synaptic package manager or apt-get.
 
> >> cd /usr/bin
>> rm gcc
>> ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

After ATLAS and PETSc installation, you can restore. 

> >> cd /usr/bin
>> rm gcc
>> ln -s /usr/bin/gcc-4.1 /usr/bin/gcc


2. I assume you will install PETSc on serial machine. PETSc is originally targeted multiprocess machine, meaning that you need MPI. However, if you install PETSc on you desktop/laptop, you don't need MPI. If you want to make parallel codes and test them on your serial machine, then install lam/mpi (you can install it using synaptic). In this case you are running your code using only one processor (equivalent to using "mpirun -np 1").


3. Download PETSc from the website ([http://www-unix.mcs.anl.gov/petsc/petsc-2/index.html](http://www-unix.mcs.anl.gov/petsc/petsc-2/index.html)). Follow the installation instruction ([http://www-unix.mcs.anl.gov/petsc/petsc-2/documentation/installation.html](http://www-unix.mcs.anl.gov/petsc/petsc-2/documentation/installation.html)). FYI, I will write down what I did. 

> >> cd /usr/local/src

>> tar -xvzf petsc.tar.gz

>> cd petsc

>> export PETSC_DIR=$PWD

>> ./config/configure.py --with-cxx=g++-3.4 --with-c-support=1 --with-fc=g77 CXXOPTFLAGS='-O3 -mtune=pentium-m' FOPTFLAGS='-O3' --with-mpi=0 --with-debugging=0 --with-blas-lapack-dir=/usr/local/src/ATLAS/lib/Linux_PMSSE2 --with-x=1 --with-clanguage=c++

>> export PETSC_ARCH="yours"

>> make all 

>> make test

--with-blas-lapack-dir=/usr/local/src/ATLAS/lib/Linux_PMSSE2 (directory where ATLAS library is installed).
--with-mpi=0 (0 means you don't want MPI).
--with-x=1 (PETSc comes with some of graphic routines such as showing residual norm history of ksp solvers).
--with-clanguage=c++ (default language is C. I used C++ because I'm calling PETSc from my C++ program).
--with-debugging=0 (I want optimized version.)

THIS IS IT. HAVE FUN !!![/SIZE][/SIZE][/SIZE][/FONT]

---

### Post by marcelianooliveira on 2011-05-05
> **ali780 said:**
> Hello
I want to install petsc 2.3.3 on my ubuntu but I don't know how can i do it. Please if somebody knows help me.
Thank you

for PETSC easy way see my video in the youtube:

[http://www.youtube.com/watch?v=sJK6DCrNi0A](http://www.youtube.com/watch?v=sJK6DCrNi0A)

---

