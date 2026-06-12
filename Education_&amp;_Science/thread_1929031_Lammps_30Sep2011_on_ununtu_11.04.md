---
title: "Lammps 30Sep2011 on ununtu 11.04"
date: 2012-02-21
forum: Education &amp; Science
---

### Post by omidmd on 2012-02-21
Hi Guys

do you know how to install Lammps 30Sep11 on ubuntu 11.04?

I followed these instructions which is in lammps site:

sudo apt-get install build-essential fftw-dev tcsh mpich2 gfortran

# for parallel binaries
make ubuntu

 
but after installing packages and write make ubuntu

I got an error :

../lmp_ubuntu
/usr/bin/ld: cannot find -lcr
collect2: ld returned 1 exit status
make[1]: *** [../lmp_ubuntu] Error 1
make[1]: Leaving directory `../lammps-30Sep11/src/Obj_ubuntu'
make: *** [ubuntu] Error 2

Do you know what should I do?Should I install some packages for my PC?
My system: motherboard Gigabyte Z68XUD3

---

### Post by Pand5461 on 2012-03-21
Hi!
Do you need that specific LAMMPS version? I have a Makefile for 17Feb12 version which seems to work on my Ubuntu machine (see the attachment).
The error "cannot find -lcr" means you don't have libcr.so installed on your system. Try installing libcr-dev:
```
sudo apt-get install libcr-dev
```

---

### Post by plazaster on 2012-07-23
Hi omidmd, i've just installed LAMMPS latest build, on my workstation. I had trouble installing it initially and received the same(?) looking error as you. I think my problem was that I was trying to install the parallel version, which required all the MPI libraries. From the manual there is an almost hidden "serial" install method towards the end of step 5 in Section 2.

[http://lammps.sandia.gov/doc/Section_start.html#start_2](http://lammps.sandia.gov/doc/Section_start.html#start_2) 

"From the src directory, type "make stubs", or from the STUBS dir, type "make" and it should create a libmpi.a suitable for linking to LAMMPS."

Then instead of "make linux", try "make serial"

Of course, this was on my workstation for testing purposes. Installing on a cluster or high end multi-core machine is less trivial.

---

