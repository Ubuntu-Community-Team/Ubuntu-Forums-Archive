---
title: "Help installing OOF2: Finite Element Analysis of Microstructures"
date: 2008-05-15
forum: Education &amp; Science
---

### Post by Erbium on 2008-05-15
Hello,  

I am trying to install OOF: Finite Element Analysis of Microstructures ([http://www.ctcms.nist.gov/oof/](http://www.ctcms.nist.gov/oof/)), version 2.0.5a3.  I keep running into problems building the source with python.  I believe I have installed all of the required packages using apt-get.  In the end of the build( sudo python setup.py build) I get the error "error: can't link blas!".  

Any help would be appreciated.

---

### Post by thisxcantxexist on 2008-10-23
I'm having the same issue trying to install oof2 in ubuntu hardy, just wondering if you ever solved this issue?

---

### Post by Erbium on 2008-10-24
Hey,

I was originally trying to install the 2.0.4 version within a virtual machine for portability.  I kept getting compiling errors after installing every conceivable library needed.  I had a friend that had some background in python, that went through the code for about 30 minutes in order to get it to compile.

Anyhow,  I have since upgraded(recompiling from the source code) to 2.0.5a5 since then, myself too.  I had no problems compiling or running the new version.  I am not sure if the new version fixed the problems of the past version or not.  I believe there had been an issue of a library oof2 needed but couldn't find while compiling.

Anyhow,  since then I haven't used oof2 much since running into a problem figuring out a problem with my simulation of residual stresses developed from CTE mismatch involving an unsolved stiffness matrix.  It was more of a side project for my thesis work anyways.

So my recommendations would be for you to try one of the newer versions of oof2, use NanoHub([http://www.nanohub.org/)email](http://www.nanohub.org/)email) the oof2 list(very inactive, but seems rather responsive when questions are asked).  Or for me to send you the 2.0.4 modified source code or even the entire virtual machine

good luck,

---

### Post by thisxcantxexist on 2008-11-04
please send me anything you've got, not being able to install oof2 is really holding up my research. The virtual machine would be incredible. If you can send the stuff by email i can be reached at [email]rtourtel@umich.edu[/email]

if not maybe a file hosting site such as filedropper.com would work. otherwise i am even willing to pay you postage for a cd with the files if it comes to it.

thanks a ton

Richard Tourtellotte

---

### Post by spoilingmyself on 2010-02-05
hi everyone!
i have been installing oof2.0.5a9 the latest release where they say most of the bugs have been fixed. but i am not able to correctly link blas and thus oof2 cannot be installed. please tell me what to do. following is the result i get.. please help me.
thanks in advance!
sudo python setup.py build --blas-libraries='lapack blas gfortran m' --skip-swig install --prefix=/usr/local
[sudo] password for vineet: 
running build
running build_shlib
running makedepend on .C files.
Testing if blas links correctly
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -Ibuild/temp.linux-i686-2.6-2d/SRC -ISRC -c tmpAq1Uoq/blastest.c -o tmpAq1Uoq/blastest.o
gcc -pthread tmpAq1Uoq/blastest.o -Lbuild/temp.linux-i686-2.6-2d/shlib -llapack -lblas -lgfortran -lm -o tmpAq1Uoq/blastest
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
gcc -pthread tmpAq1Uoq/blastest.o -L/usr/local/lib -Lbuild/temp.linux-i686-2.6-2d/shlib -llapack -lblas -lgfortran -lm -lg2c -o tmpAq1Uoq/blastest
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
gcc -pthread tmpAq1Uoq/blastest.o -L/usr/local/lib -Lbuild/temp.linux-i686-2.6-2d/shlib -llapack -lblas -lgfortran -lm -lgfortran -o tmpAq1Uoq/blastest
/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status
removing 'tmpAq1Uoq' (and everything under it)
error: can't link blas!

---

### Post by Xnst on 2010-02-17
Hi spoilingmyself,

I managed to compile oof2.0.5a9 on my Hardy box. I used the same command line as you so it can be done.
```

sudo python setup.py build --blas-libraries='lapack blas gfortran m' --skip-swig install --prefix=/usr/local

```

I am not an expert on compiling code but I think, a lot of the time you need the dev packages in your library to succeed. In your case you can check if you have installed liblapack-dev and libblas-dev.

Hope it works for you.

---

