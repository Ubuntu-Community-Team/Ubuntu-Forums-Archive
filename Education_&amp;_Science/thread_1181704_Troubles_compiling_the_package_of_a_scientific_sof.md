---
title: "Troubles compiling the package of a scientific software (OASES)"
date: 2009-06-08
forum: Education &amp; Science
---

### Post by angel84 on 2009-06-08
Hi Everybody,

This is my first post here so please be kind with me, I'm also a newbie so I need someone really patient! 8-[ 
(I hope that my english is good enough)

This is my story: 

I want to install a scientific software called OASES and at present I cannot compile the OASES package.[I follow an installation guide for the installation procedure, the compiling step is a part of the installation] When I type the command:

> make all

which calls the file Makefile, it fails to compile and returns a list of errors like this:

angelo@angelo-laptop:~/Oases$ make all
./objdir.sh 
 rm -f objdir.done
mkdir -p /home/angelo/Oases/bin/- /home/angelo/Oases/lib/-
>>> Entering oases/src
cd src ; make all 'OASES_BIN = /home/angelo/Oases/bin/-' 'OASES_LIB = /home/angelo/Oases/lib/-' 'SYSXLIB = ' 'FC_STM = f77 ' 'CC_STM = ' 'RANLIB = ranlib' 'FFLGS = -O ' 'CFLGS = ' 'LFLGS = ' 
 make[1]: Entering directory `/home/angelo/Oases/src'
f77   -c -o ./-/oasgun21.o oasgun21.f
   plintgr:
Warning on line 96: local variable cexpt never used
Warning on line 96: local variable sqrtt never used
    plinlog:
Warning on line 185: local variable cexpt never used
Warning on line 185: local variable sqrtt never used
   ploglog:
Warning on line 249: local variable cexpt never used
Warning on line 249: local variable sqrtt never used
    preqv:
Warning on line 291: local variable cexpt never used
Warning on line 291: local variable sqrtt never used
   condrb:
   plprof:
Warning on line 395: inconsistent calling sequences for pltwri,
    arg 6: here real variable, previously complex variable.
     arg 8: here real variable, previously complex variable.
Warning on line 419: local variable opt2 never used
Warning on line 419: local variable cexpt never used
Warning on line 419: local variable sqrtt never used
    intcon:
Warning on line 494: inconsistent calling sequences for vclr,
    arg 1: here real variable, previously complex variable.
   autoax:
   plpwri:
   pltwri:
   pldetm:
Warning on line 734: local variable cexpt never used
 Warning on line 734: local variable sqrtt never used
   confaw:
Warning on line 825: local variable lab never used
Warning on line 825: local variable cexpt never used
Warning on line 825: local variable sqrtt never used
 Warning on line 825: local variable heading never used
   confr:
Warning on line 918: local variable lab never used
Warning on line 918: local variable cexpt never used
Warning on line 918: local variable sqrtt never used
 Warning on line 918: local variable heading never used
   confab:
Warning on line 942: local variable cexpt never used
Warning on line 942: local variable sqrtt never used
   lenstr:
/tmp/fort77-13286-1.c:2167: error: conflicting types for ‘pltwri_’
 /tmp/fort77-13286-1.c:831: error: previous declaration of ‘pltwri_’ was here
/usr/bin/f77: aborting compilation
make[1]: *** [-/oasgun21.o] Error 25
make[1]: Leaving directory `/home/angelo/Oases/src'
make: *** [oases.done] Error 2


I don't understand the meaning of the error report, so I'd really appreciate any help by someone which understand that. I only have some guessing. 
These are my naive ideas: :-s

1 the file Makefile doesn't work for my HOSTTYPE-OSTYPE combination, that can be if it is not what I guess it is (i386-linux-linux)

2 my compilers are not correctly installed (which I think not because the installation of the compilers is done automatically by Synaptic Package Manager)

3 maybe I have conflicting compilers (this can be because I manually downloaded [by the Synaptic Package manager] the compiler f2c and fort77 and I already have gcc and gfortran)

4 maybe there is an error in the Makefile (as example it is not updated to the new versions of the compilers, as example it uses g77 instead of gfortran)

[B]These are just guessing and I'd really heartily appreciate any help,idea or suggestion, because basically so far I don't know what to do!:shock:
[/B]

I post here the part of the *Makefile* which I think is the part that regards me:

  	 	 	 	 	 	  ############################################################################## 
 # 
 # PC HARDWARE RUNNING i386-linux 
 # 
 ############################################################################## 
 # 
 # Compiler flags 
 # 
 # 
 # For the ABSOFT FORTRAN compiler, uncomment out the following 
 # lines: 
 # 
 # FC.i386-linux-linux       = f77  -f -s -N2 -N9 -N51 
 # FFLAGS.i386-linux-linux   = 
 # LIB_MISC.i386-linux-linux = -lV77 -lU77 
 # MISC.i386-linux-linux     = 
 # 
 # For the standard F2C FORTRAN compiler, uncomment out the following 
 # lines: 
 # 
 # FC.i386-linux-linux       = fort77 
 # FFLAGS.i386-linux-linux   = -O3 -m486 -fexpensive-optimizations -malign-double 
 # LIB_MISC.i386-linux-linux = 
 # MISC.i386-linux-linux     = 
 # 
 # For the Portland Group's pgf77 FORTRAN compiler, uncomment out the 
 # following lines: 
 # 
 # FC.i386-linux-linux       = pgf77 
 # FFLAGS.i386-linux-linux   = -fast -O2 -Mdalign 
 # LIB_MISC.i386-linux-linux = 
 # MISC.i386-linux-linux     = 
 # 
 # For the native g77 FORTRAN compiler, uncomment out the following 
 # lines: 
 # 
 FC.i386-linux-linux       = f77 
 FFLAGS.i386-linux-linux   = -O3 -m486 -malign-double -fstrength-reduce \ 
                 -fexpensive-optimizations 
 LIB_MISC.i386-linux-linux = 
 MISC.i386-linux-linux     = 
 # 
 CC.i386-linux-linux       = gcc 
 CFLAGS.i386-linux-linux   = -I/usr/X11R6/include 
 LFLAGS.i386-linux-linux   = -L/usr/X11R6/lib 
 RANLIB.i386-linux-linux   = ranlib 
 # 
 # 
 # Fortran definitions 
 # 
 FC_STMNT = $(FC.$(HOSTTYPE)-$(OSTYPE)) 
 CC_STMNT = $(CC.$(HOSTTYPE)-$(OSTYPE)) 
 RANLB = $(RANLIB.$(HOSTTYPE)-$(OSTYPE)) 
 MISC_LIB = $(LIB_MISC.$(HOSTTYPE)-$(OSTYPE)) 
 MISC = $(MISC.$(HOSTTYPE)-$(OSTYPE)) 
 FFLAGS = $(FFLAGS.$(HOSTTYPE)-$(OSTYPE)) 
 CFLAGS = $(CFLAGS.$(HOSTTYPE)-$(OSTYPE)) 
 LFLAGS = $(LFLAGS.$(HOSTTYPE)-$(OSTYPE)) 
 # 
 # 
 MKE_STR = 'OASES_BIN = ${BIN}' 'OASES_LIB = ${LIB}' 'SYSXLIB = ${MISC_LIB}' \ 
           'FC_STM = ${FC_STMNT}' 'CC_STM = ${CC_STMNT}' 'RANLIB = ${RANLB}' \ 
           'FFLGS = ${FFLAGS}' 'CFLGS = ${CFLAGS}' 'LFLGS = ${LFLAGS}' 
 #          'OSTYPE = ${OSTYPE}' 'HOSTTYPE = ${HOSTTYPE}' 
 # 
 

If it can be of any help I also have a part of the installation guide of OASES (30 kb) which is related to the compiling step.

Thanks a lot!:-)

 
  Angelo

---

### Post by stevencrocker on 2012-12-20
Angelo,

Did you ever find a solution to this problem?

Steve

---

### Post by overdrank on 2012-12-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

