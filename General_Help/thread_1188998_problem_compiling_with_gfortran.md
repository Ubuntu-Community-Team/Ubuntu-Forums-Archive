---
title: "problem compiling with gfortran"
date: 2009-06-16
forum: General Help
---

### Post by lilsalsa74 on 2009-06-16
I am an absolute beginner when it comes to Ubuntu and Fortran. I recently installed Ubuntu and the gfortran compiler. I am trying to compile the following simple hello world program:

    program hello
    write(*,*)'Hello, world!'
    end

When I try to compile in my terminal I get:

lilsalsa74-laptop:~$ gfortran -c hello.f95
gfortran: hello.f95: No such file or directory
gfortran: no input files

Since I'm a beginner at this I really have no idea what I'm doing wrong. Please help!

---

### Post by lilsalsa74 on 2009-06-16
Nevermind! I figured out my own problem. I was in the wrong directory when I was attempting to compile.

---

