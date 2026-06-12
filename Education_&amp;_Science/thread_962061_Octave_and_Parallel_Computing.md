---
title: "Octave and Parallel Computing"
date: 2008-10-28
forum: Education &amp; Science
---

### Post by smattiuz on 2008-10-28
Hi all, i'm new on this forum but not new on ubuntu.
I'm on a dell inspiron6400, 1gb ram, Intel Integrated Graphic Device

I tried all day to fetch information on how to parallel compute using octave:

-i looked for tools or packages and found octave-parallel, installed it but crashes on my friend's laptop (a 64bit hp) with a "segmentation fault" error

-downloaded MKL math libraries from Intel, installed and recompiled octave using them, but didn't still figure out how to use them properly in my scripts (and didn't find any howto)

-since i don't have an NVIDIA chipset, cannot use the CUDA cpu+gpu feature for parallel computing and any other search, sends me back to mkl libs.

so, after this, can any of you give me any tip on how to sort out my problem? any solution is really wellcome (i also have matlabR14, but sometimes crashes my entire sys, so i'd prefer to use octave)

thanks you all

sam

---

### Post by smattiuz on 2008-10-29
oh is aswell welcome something to improve octave's power :P

---

### Post by normandin on 2008-10-31
i've never used any of them, but you might want to look at mpitb ([http://atc.ugr.es/javier-bin/mpitb](http://atc.ugr.es/javier-bin/mpitb)) or the parallel and multicore packages from octave-forge ([http://octave.sourceforge.net/packages.html](http://octave.sourceforge.net/packages.html)).

a search of the octave mail-list archives would probably be helpful too.

---

### Post by Proton Soup on 2008-11-01
parallel scilab?

[http://ats.cs.ut.ee/u/kt/hw/scilabpvm/](http://ats.cs.ut.ee/u/kt/hw/scilabpvm/)

---

### Post by zamba on 2010-05-23
HELLO, i HAVE UBUNTU 9.10 AND I HAVE INSTALLED OCTAVE PARALLEL, QTOCTAVE 0.8.1, BUT I CANT GET ANY OF THE FUNCTIONS TO WORK, FOR EXAMPLE SEND(X,SOCKETS) PRODUCES AN ERROR. PLEASE ANYONE CAN TELL ME WHERE TO FIND DETAILED DOCUMENTATION ABOUT HOW TO USE OCTAVE PARALLEL IN A MULTICORE MACHINE, HOW TO CONFIGURE IT ?
I HAVE READ THAT IT CAN BE DONE USING OPENMPI, BUT IT WORKS IN A CLUSTER OF COMPUTERS, AND I NEED IT TO WORK IN A DUAL CORE PROCESSOR, JUST LIKE THE PARALLEL COMPUTING TOOLBOX OF MATLAB

PLEASE HEEEEELLPPPP!!   ILL BE VERY THANKFUL

---

