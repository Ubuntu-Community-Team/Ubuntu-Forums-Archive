---
title: "jre comsol matlab"
date: 2009-03-28
forum: General Help
---

### Post by ehsaan_sh on 2009-03-28
Hi,

I am using comsol and matlab on my intrepid machine. 

At first i was constantly getting an error message until I updated the path in /usr/matlab/bin/matlab file as such:

Error:
> "Locking assertion failure. Backtrace:"
"#0 /usr/lib/libxcb-xlib.so.0 [0xb5581767]"

Fix: 
> #!/bin/sh
export MATLAB_JAVA=/usr/java/jre1.6.0_13
#export AWT_TOOLKIT=MToolkit
export LIBXCB_ALLOW_SLOPPY_LOCK=1
#
#  Name:
#     matlab    script file for invoking MATLAB
#

comsol runs (prob without the correct java path) but when i run a comsol generated m-file in matlab I get a segmentation fault and both of them close without a trace of the kind of error which might have happened

please help....I don't  wanna go back to M$

Ehsan

---

### Post by ehsaan_sh on 2009-03-29
bump!

---

### Post by 3Miro on 2009-03-29
I am using Matlab and when I start it I get error, but Matlab runs despite the error so I have done nothing to fix it.

I have not run comsol on my computer. Can you use matlab itself?

Start it from the command line (Apps -> Accessories -> Terminal) and see if it gives any error messages.

---

### Post by ehsaan_sh on 2009-03-29
well each of them run separately. When you wanna run an FEM simulation from matlab, you need to call comsol to use its models.

My other solution would be writing a complete FEM program in matlab which i think is not less painfull than M$

---

### Post by nutsy.ben on 2010-04-01
Well, One year old and no more ideas ?

I have to admit that I face the same problem.
I run Matlab + COMSOL on 3 different PC, all with Ubuntu 9.04.

On two of them I have Matlab 2008a and on the last the 2009.
I also run different architecture 64 and 32 bits .... 

PC 1         MATLAB2008a             AMD64         COMSOL35        Works
PC 2         MATLAB2008a             Intel            COMSOL35        **Segmentation Fault*
PC 3         MATLAB2009a             AMD64         COMSOL35        Crash when application starts

The only reason why the PC1 might work ??? the ATI graphic card ????....
If I had the solution I would show off .... but I don't 
help is welcome as this issue is more than 4 years old and still not fixed .... :s

---

### Post by nutsy.ben on 2010-04-11
> **nutsy.ben said:**
> Well, One year old and no more ideas ?

PC 1         MATLAB2008a             AMD64         COMSOL35        Works
PC 2         MATLAB2008a             Intel            COMSOL35        **Segmentation Fault*
PC 3         MATLAB2009a             AMD64         COMSOL35        Crash when application starts



PC 3 works with Matlab2008a ....

---

