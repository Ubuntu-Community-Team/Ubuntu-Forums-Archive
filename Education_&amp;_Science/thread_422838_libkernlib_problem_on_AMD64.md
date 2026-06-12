---
title: "libkernlib problem on AMD64"
date: 2007-04-25
forum: Education &amp; Science
---

### Post by Schjoh on 2007-04-25
Hi

I've made a fortrancode to load hbook's, using commands like:

HLIMIT
HROPEN

But when compiling and then running the program I get:

```
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
LOCB/LOCF: address 0x2b9c83e171b8 exceeds the 32 bit address space
or is not in the data segments
This may result in program crash or incorrect results
Therefore we will stop here
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
```

I do believe it is a problem with libkernlib on a AMD64

---

### Post by vampireking on 2008-02-20
I also has similar problem.
My computer has Intel Core2 Duo , Fedora8 x86_64, kernel 2.6.23.15-137.fc8, gcc version 4.1.2 20070925 (Red Hat 4.1.2-33). My compile command line is :

f95   $1.f -o$1.out `cernlib -G kernlib packlib mathlib`

kernlib mathlib packlib are used. My program use the following functions:

hlimit hbook1 hfill hrput histdo dgmlt2 

It compiled well, but upon execution it gives just the same output as yours:

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
LOCB/LOCF: address 0x7fffa93c13cc exceeds the 32 bit address space
or is not in the data segments
This may result in program crash or incorrect results
Therefore we will stop here
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

To check where the problem is, I compiled a simple program with exactly the same command line:
f95   $1.f -o$1.out `cernlib -G kernlib packlib mathlib`
It use function "dgauss" of the mathlib. It works fine!

So I figure it might be the problem of hbook!

The program I used for testing is following:

      implicit double precision(a-h,o-z)
      external f
      a=5.d-7
      b=1.d0
      eps=1.d-9
c      n=8
      ans=dgauss(f,a,b,eps)
      write(*,*) ans
      end
      
      function f(x)
      double precision f,x
      f=sin(1.d0/x)
      return
      end

---

### Post by vampireking on 2009-04-28
At last I give up calling hbook subroutines directly in the fortran program. Instead, the calculated data are saved in a file. The Paw program can read from it using 
ve/re y1,...,yn filename
Then contents of arrays yi can be put into a histogram using
h/put/con histID arrayname
Then you can draw out these histograms.

This way of directly saving data in a file has another advantage, enabling us to read and process them most easily.

---

### Post by nish.des on 2010-03-02
The same problem I had with PAW was solved after statically linking the libraries.

Just add -static before the list of libraries to compile.

Better yet, type
$ cernlib pawlib

And copy whatever output it gives into your Makefile.

HTH,
Nishita

---

### Post by Heyayun on 2012-07-02
Hi, nish.des,

I just did as you said:
#gfortran $1.f -static -lkernlib -lpacklib -lmathlib -o $2.out
It worked well.
But what is the "Makefle" you have mentioned?

---

### Post by overdrank on 2012-07-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

