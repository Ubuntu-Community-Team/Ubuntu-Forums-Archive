---
title: "PWscf, ABINIT installation on Ubuntu -help"
date: 2007-01-10
forum: Education &amp; Science
---

### Post by jlawrence on 2007-01-10
Hi all,

 I am a newbie to Ubuntu. I have been trying to install two quantum computational programs, ABINIT and PWscf without success. I have followed the instructions in the manual, but got problem to run PWGUI for PWscf and abinis command for ABINIT.

PWscf: 
[http://www.pwscf.org/downloads/PWcodes/codes/3.2/espresso-3.2.tar.gz](http://www.pwscf.org/downloads/PWcodes/codes/3.2/espresso-3.2.tar.gz)

ABINIT: 
[www.abinit.org](www.abinit.org)
[ftp://ftp.abinit.org/pub/abinitio/ABINIT_v5.2.4/pclinux_g95_seq-5.2.4.tar.gz](ftp://ftp.abinit.org/pub/abinitio/ABINIT_v5.2.4/pclinux_g95_seq-5.2.4.tar.gz)

Can somebody who has experiences on installing this program kindly post his/her steps ?
Is it possible for you to have packages created for these 2 programs ?

Thank you in advance,

---

### Post by Panta on 2007-01-19
Hi jlawrence,

I am also a newbie to Ubuntu and I the same problem as you. I only tried to install ABINIT and, as you can see on its websitehave, you should know your platform and processor (compiler). I am not very good on it, but I have the Ubuntu - Edgy Linux installed and my processor is a intel pentium 4. The only version of ABINIT that worked on my PC is Linux - Intel - PGI version 4.6.5. I have tried to install the recent ones, but it didn't work, but I'm happy with that one. 
So, if you have a PC similar to mine, go to [http://www.abinit.org/package/](http://www.abinit.org/package/)   and download the package containing sequential binaries:

Linux - Intel - PGI  4.6.5

then, you make

tar xvfz NameOfDownloadedFile

it will create a folder containing all you need to use Abinit... every time you use ABINIT, you have to go to this folder using a terminal... 

then you follow the instructions that you have tried to follow, it should work.
If you need more help and I can do it, don't hesitate to write me. Sorry I didn't try yet to install PWscf, but I will do it soon.

Thiago

---

### Post by aranyakam on 2007-05-28
Once you have downloaded and extracted the files in a suitable folder, you have to set the path for various compilers. Once this is done, you can compile it with out much difficulty.

From my experience, pwscf is easier to install comapared to ABINIT (I compile parallel code, serial code is much easier to compile in both cases)
:)

---

### Post by p.nilgoon on 2007-12-16
Hi,aranyakam
If it is possible send your commands and methods for
installation of PWscf and abinit
becase I can't install them,
and I receive some errors for example :
C Compiler can not create executable

thanks.

---

### Post by Dodelijk on 2008-01-12
Hello, 

This is a bit late but i thought i'd add it for consistency for other users who stumble across this thread from google as i keep doing. 

You needs to have a fortran compiler. I recommend opening synaptic package manager and installing gfortran. 
You might also need a C compiler i'm not sure. I'd install g++ as well just to be safe.

Once you have done this download the source files for pwscf from [http://www.pwscf.org/downloads/PWversion/4.0cvs/espressocvs.tar.gz](http://www.pwscf.org/downloads/PWversion/4.0cvs/espressocvs.tar.gz) (this is actually the Quantum Espresso package which includes the pwscf stuff) 

You unpack the file to a location and then via the terminal navigate to the unpacked directory. once there type

```

./configure
make install all 

```

and this should compile the code. Once done you'll hava a /bin directory your current directory containing the binaries.

---

### Post by mathsou on 2008-01-30
I'm certainly late, but I have installed abinit yesterday on my ubuntu PC, and I have just downloaded the package for ubuntu on the abinit.org website.
the package was a .deb file, and when I wanted to install it, ubuntu indicate to me the packages I have to install (Libc6, ans so on)
after, I haven't encountered any problem, abinit works correctly (4 times faster than my mac,)

---

### Post by jlawrence on 2008-02-18
Dodelijk, mathsou,

Your suggestion worked perfect. Thank you very much !

---

### Post by raamesh123 on 2008-03-13
Hi friends

i also have the same problem what mr. lawrence has (installation of pwscf. i have installed ifort complier but i think i make mistake in setting up the path can anybody give command for setting the path

the make all gives error like

command line remark #10148: option '-tp' not supported


thanks
ramesh

---

### Post by min4 on 2008-11-14
Hi all,

I am new in ABINIT,
Anyone here know where got the ABINIT forum?
As the forum provide by [www.ABINIT.org](www.ABINIT.org) is by email base.

Thanks
CM

---

### Post by musafir on 2009-03-05
I was trying to install PWSCF and after doing make all, but i  got following errors :
test -d bin || mkdir bin
if test -d iotk ; then \
	( cd iotk ; if test "make" = "" ; then make  TLDEPS= lib+util ; \
	else make  TLDEPS= lib+util ; fi ) ; fi
make[1]: Entering directory `/root/Desktop/espresso-4.0.4/iotk'
cd src ; make lib+util
make[2]: Entering directory `/root/Desktop/espresso-4.0.4/iotk/src'
mpif90 -O2 -assume byterecl -nomodule -fpp -D__INTEL -D__FFTW -D__USE_INTERNAL_FFTW -I../include  -I./  -I../Modules  -I../iotk/src -I../PW  -I../PH -c iotk_base.f90
f95: byterecl: No such file or directory
f95: unrecognized option '-nomodule'
f951: error: unrecognized command line option "-assume"
f951: error: unrecognized command line option "-fpp"
make[2]: *** [iotk_base.o] Error 1
make[2]: Leaving directory `/root/Desktop/espresso-4.0.4/iotk/src'
make[1]: *** [lib+util] Error 2
make[1]: Leaving directory `/root/Desktop/espresso-4.0.4/iotk'
make: *** [libiotk] Error 2

Please help me out........

TIA.

---

### Post by Ambesh on 2009-03-23
Hi All
After configuring succesfully espresso in ubuntu, making use of "make install all" it shows the following error-

test -d bin || mkdir bin
if test -d iotk ; then \
( cd iotk ; if test "make" = "" ; then make TLDEPS= lib+util ; \
else make TLDEPS= lib+util ; fi ) ; fi
make[1]: Entering directory `/root/Desktop/espresso-4.0.4/iotk'
cd src ; make lib+util
make[2]: Entering directory `/root/Desktop/espresso-4.0.4/iotk/src'
mpif90 -O2 -assume byterecl -nomodule -fpp -D__INTEL -D__FFTW -D__USE_INTERNAL_FFTW -I../include -I./ -I../Modules -I../iotk/src -I../PW -I../PH -c iotk_base.f90
f95: byterecl: No such file or directory
f95: unrecognized option '-nomodule'
f951: error: unrecognized command line option "-assume"
f951: error: unrecognized command line option "-fpp"
make[2]: *** [iotk_base.o] Error 1
make[2]: Leaving directory `/root/Desktop/espresso-4.0.4/iotk/src'
make[1]: *** [lib+util] Error 2
make[1]: Leaving directory `/root/Desktop/espresso-4.0.4/iotk'
make: *** [libiotk] Error 2

Please help me in shorting out this error.

Thanks in advance
Ambesh

---

### Post by aeftimia on 2011-08-18
I know this is an old thread, but I spent a long time writing a script that installs quantum chemistry software on Ubuntu, and I am trying to circulate it so others do not have to spend weeks tweaking configure options, reinstalling, etc.

This: [https://sourceforge.net/projects/aeftimiamisc/files/installstuff/](https://sourceforge.net/projects/aeftimiamisc/files/installstuff/)

Will install a LOT of popular software, including quantum espresso and the latest (at least the time of this post) abinit.

---

