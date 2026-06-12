---
title: "Octave 3.6.1 and odepkg 0.8.4"
date: 2013-02-25
forum: Education &amp; Science
---

### Post by rengglian on 2013-02-25
Hi everyone, 
I would like to install the new odepkg into my octave installation. 
I started octave by
```
sudo octave
```
```
GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-pc-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

```

then i tried to install the downloaded package:
```
pkg install odepkg-0.8.4.tar.gz 
cash/mebdfi.f:2932.46:

            CALL I_INTERP(N,JSTART,H,T,Y,TOUT,Y0)                       
                                              1
Warning: Rank mismatch in argument 'y0' at (1) (rank-1 and scalar)
daskr/ddaskr.f:1931.20:

     *   RWORK(LRX),JROOT,IRT,RWORK(LROUND),INFO(3),                    
                    1
Warning: Rank mismatch in argument 'jroot' at (1) (rank-1 and scalar)
daskr/ddaskr.f:1954.20:

     *   RWORK(LRX),JROOT,IRT,RWORK(LROUND),INFO(3),                    
                    1
Warning: Rank mismatch in argument 'jroot' at (1) (rank-1 and scalar)
daskr/ddaskr.f:2182.20:

     *   RWORK(LRX),JROOT,IRT,RWORK(LROUND),INFO(3),                    
                    1
Warning: Rank mismatch in argument 'jroot' at (1) (rank-1 and scalar)
For information about changes from previous versions of the odepkg package, run 'news ("odepkg")'.
```

```
octave:1> pkg list
Package Name  | Version | Installation directory
--------------+---------+-----------------------
      odepkg  |   0.8.4 | /usr/share/octave/packages/odepkg-0.8.4

```
```
help ode45
error: help: Octave provides lsode for solving differential equations.  For more
information try `help lsode'.  Matlab-compatible ODE functions are
provided by the odepkg package.  See `http://octave.sf.net/odepkg/'.

Please read `http://www.octave.org/missing.html' to learn how you can
contribute missing functionality.

```

is there a way to make it running? 
My System:
```
Linux ubuntu 3.5.0-25-generic #38~precise1-Ubuntu SMP Wed Feb 20 09:53:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

Best wishes

---

### Post by ImgPrcSng on 2013-05-08
Hey there rengglian

I think you should have seen the news("odepkg"). It states that it wont load the package automatically. You have to use the pkg load command everytime you need to use or set the option -auto while installing. Use help pkg for more info.

Hope this helps.
Cheers.

Regards,
ImgPrcSng

---

