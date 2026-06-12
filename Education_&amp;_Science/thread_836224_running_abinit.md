---
title: "running abinit"
date: 2008-06-21
forum: Education &amp; Science
---

### Post by andika on 2008-06-21
Good morning everyone. My name is Andika, a new user of abinit. I used operating system Ubuntu 8.04

I want to ask about how to run abinit.

As in ab init tutorial, I am asked to make folder " work" with file ,abinis, t1x.files and t11.in in it
I copy file t11.in from tutorial. About file t1.files, the content is

t11.in
t11.out
t1xi
t1xo
t1x
../../../Psps_for_tests/01h.pspgth

I do the command abinis < t1x.files >& log in terminal. But in the end, I do not find output files t1xo_DDB, t1xo_DEN, t1xo_EIG, and t1xo_WFK, as stated in tutorial. I got a strange line in log too:

At line 136 of file iofn2.F90
Fortran runtime error: No such file or directory
  ABINIT
 
  Give name for formatted input file:
t11.in
  Give name for formatted output file:
t11.out
  Give root name for generic input files:
t1xi
  Give root name for generic output files:
t1xo
  Give root name for generic temporary files:
t1x

I want to know if there is something wrong with my abinit

thank you
with regard
Andika Asyuda

---

### Post by rajan on 2008-06-22
Andika,
 Did you try to find the missing file? iofn2.f90 might be mislabeled or something. I'm not familiar with abinit (is it a computational chemistry program?), but this is a fairly common problem people run into when something is missing from the filesystem. do you have a fortran compiler installed?

rajan

---

### Post by benny-lava on 2008-08-26
Hi,


I'm also going through abinit tutorial. I have installed abinit using the ubuntu package and everything works fine. I have tried to use the binaries avalaible on abinit webpage but it didn't worked. 

You can also try to move the pseudopotential file 01h.pspgth  in your work directory.

and change the final line in the t1x.files to 01h.pspgth.

---

### Post by mararama on 2008-09-12
Andika, I just intalled abinit and am having the same issue.  Did you ever find the source of this issue?
*******
Edit: I found the answer in the abinit forums.  I think it was copying the pseudopotential to the working directory, but it could also have been something to do with not writing to the standard output.

---

### Post by jormabe1 on 2008-09-13
[wedding dresses](http://www.jormabridal.com), [wedding dress](http://www.jormabridal.com), [wedding gowns](http://www.jormabridal.com), [bridesmaid dresses](http://www.jormabridal.com/gown.html)

---

### Post by some.hacker on 2009-12-01
Everyone, I just had a similar problem getting this thing to work, and the solution I found was to run it as root. :/ Not the best of solutions, but it seems to work.

---

