---
title: "FFTW and linking"
date: 2007-06-30
forum: Education &amp; Science
---

### Post by DaBigEd on 2007-06-30
Hey all. I am admin of a debian system that is used by our quantum dynamics research group (i know its not ubuntu but its close and i am desperate). Last night i broke the system severely and now I really need to get it back to the way it was. 

A long story short, I need to recompile the FFTW 2.1.5 library files.

after downloading the Tar file and extracting it. It did a

./configure --prefix /home/user/fftw22 -enable float
make
make install

However after running my code i get the following errors.

ifc -g -C -DFFTW -fpp -module ./obj/Linux-x86 -I./obj/Linux-x86 -I./obj/Linux-x86  obj/Linux-x86/precision.o obj/Linux-x86/globals.o obj/Linux-x86/mpi.o obj/Linux-x86/interpreter.o obj/Linux-x86/fft.o obj/Linux-x86/conversion.o obj/Linux-x86/misc.o obj/Linux-x86/potential.o obj/Linux-x86/setup.o obj/Linux-x86/hamiltonian.o obj/Linux-x86/propagate.o obj/Linux-x86/p.o  -o bin/Linux-x86/p -L/home/cdinneen/fftw22/lib/ -L/usr/lib -lfftw -lPEPCF90 -lIEPCF90
obj/Linux-x86/fft.o(.text+0x62d): In function `s_c2dfft':
/home/cdinneen/fft.f90:258: undefined reference to `fftwnd_f77_destroy_plan_'
obj/Linux-x86/fft.o(.text+0x71d):/home/cdinneen/fft.f90:266: undefined reference to `fftwnd_f77_create_plan_'
obj/Linux-x86/fft.o(.text+0x870):/home/cdinneen/fft.f90:274: undefined reference to `fftwnd_f77_one_'
obj/Linux-x86/fft.o(.text+0xb1f): In function `s_c1dfft':
/home/cdinneen/fft.f90:310: undefined reference to `fftwnd_f77_destroy_plan_'
obj/Linux-x86/fft.o(.text+0xc7a):/home/cdinneen/fft.f90:318: undefined reference to `fftwnd_f77_create_plan_'
obj/Linux-x86/fft.o(.text+0xce4):/home/cdinneen/fft.f90:324: undefined reference to `fftwnd_f77_one_'
make: *** [bin/Linux-x86/p] Error 1

It seems to be a linking error but i cannot find a problem with my compile line. 

If you can help me I swear to god I will have your children.

Thanks
DaBigEd

---

### Post by PaulFr on 2007-06-30
It appears you are using Intel's Fortran Compiler to compile (ifc ?). If so, should your configure line be  ```
F77=ifc ./configure --prefix /home/user/fftw22 -enable-float
```See question 2.6 in FAQ/fftw-faq.ascii file. Good luck.

---

