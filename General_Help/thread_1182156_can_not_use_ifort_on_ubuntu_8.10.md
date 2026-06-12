---
title: "can not use ifort on ubuntu 8.10"
date: 2009-06-08
forum: General Help
---

### Post by adameye on 2009-06-08
when I try to install a package I got following errors:
[COLOR="Red"]**/bin/sh: ifort: command not found**[/COLOR]
I found a post here:
[http://ubuntuforums.org/showthread.php?t=556169&highlight=%2Fbin%2Fsh%3A+ifort%3A](http://ubuntuforums.org/showthread.php?t=556169&highlight=%2Fbin%2Fsh%3A+ifort%3A)
after installing Intel_fortran:
*The Intel(R) Fortran Compiler Professional Edition for Linux* 11.0 is already installed.*
and I also added those lines into my .bashrc: 

[I]Note: I found right path using "locate" command, in that post they have a different path: wyf@wyf-desktop:/opt/intel/Compiler/11.0/083$ locate ifort
/opt/intel/Compiler/11.0/083/Documentation/compiler_f/main_for/mergedProjects/bldaps_for/common/bldaps_exifort.htm
/opt/intel/Compiler/11.0/083/Documentation/compiler_f/main_for/mergedProjects/bldaps_for/common/bldaps_synifort.htm
/opt/intel/Compiler/11.0/083/bin/ifortvars.csh
/opt/intel/Compiler/11.0/083/bin/ifortvars.sh
/opt/intel/Compiler/11.0/083/bin/ia32/ifort
/opt/intel/Compiler/11.0/083/bin/ia32/ifort.cfg
/opt/intel/Compiler/11.0/083/bin/ia32/ifortbin
/opt/intel/Compiler/11.0/083/bin/ia32/ifortvars_ia32.csh
/opt/intel/Compiler/11.0/083/bin/ia32/ifortvars_ia32.sh
/opt/intel/Compiler/11.0/083/lib/ia32/ifort_libFNP.so
/opt/intel/Compiler/11.0/083/man/man1/ifort.1
[/I]

[COLOR="Red"]PATH="/opt/intel/Compiler/11.0/083/bin/ia32:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/Compiler/11.0/083/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

source /opt/intel/Compiler/11.0/083/bin/ia32/ifortvars_ia32.sh
source /opt/intel/Compiler/11.0/083/bin/ia32/idbvars_ia32.sh[/COLOR]

but I still have no "ifort" command and can not install that package, anyone tell me? thank you very much!

Notice:
 I restarted my computer, and when I opened a terminal, it says :[COLOR="Red"]"ERROR: Unknown switch ''. Accepted values: ia32, intel64, ia64"[/COLOR] so what happened? thanks

---

### Post by newagelink on 2009-06-10
I wish I could help, but I'm trying to figure out how to install ifort or whether gfortran is a good compiler for FORTRAN 77. I'd recommend formatting your post to make it more legible; it was a bit confusing trying to understand what you were saying, and it appeared a comment blended with your terminal output. Use quote and code tags.

---

### Post by adameye on 2009-06-11
thanks for your reply, I think I have figured put the problem of "ifort" problem by adding the line "alias ifort=/opt/intel/Compiler/11.0/083/bin/ia32/ifort" into .bashrc file.

but now I have another concern, I'm not sure if I have installed a package correctly:
 
[COLOR="Red"]wyf@wyf-desktop:~/software$ make futil
ifort -ftz -mp1 -posixlib -Vaxlib -c gasdev.for ran1.f src3ft.f snrsq.f scopy.f sscal.f && ar -rlv \
libfutil.a gasdev.o ran1.o src3ft.o snrsq.o scopy.o sscal.o
ifort: command line warning #10156: ignoring option '-p'; no argument required
src3ft.f(656): (col. 10) remark: LOOP WAS VECTORIZED.
src3ft.f(599): (col. 12) remark: LOOP WAS VECTORIZED.
src3ft.f(41): (col. 5) remark: LOOP WAS VECTORIZED.
src3ft.f(66): (col. 5) remark: LOOP WAS VECTORIZED.
src3ft.f(145): (col. 10) remark: LOOP WAS VECTORIZED.
src3ft.f(228): (col. 16) remark: LOOP WAS VECTORIZED.
src3ft.f(229): (col. 16) remark: LOOP WAS VECTORIZED.
src3ft.f(230): (col. 16) remark: LOOP WAS VECTORIZED.
snrsq.f(10): (col. 10) remark: LOOP WAS VECTORIZED.
r - gasdev.o
r - ran1.o
r - src3ft.o
r - snrsq.o
r - scopy.o
r - sscal.o
[/COLOR]
looks installation fail?

> **newagelink said:**
> I wish I could help, but I'm trying to figure out how to install ifort or whether gfortran is a good compiler for FORTRAN 77. I'd recommend formatting your post to make it more legible; it was a bit confusing trying to understand what you were saying, and it appeared a comment blended with your terminal output. Use quote and code tags.

---

### Post by adameye on 2009-06-15
I think I have ifort command now

[COLOR="Red"]wyf@wyf-desktop:~/weinberg_genus/Package/Source$ if
if ifconfig ifdown ifort ifup[/COLOR]

but when I try to complie package:

[COLOR="Red"]wyf@wyf-desktop:~/weinberg_genus/Package/Source$ make everything
make contour2
make[1]: Entering directory `/home/wyf/weinberg_genus/Package/Source'
ifort -fast -c -o contour2.o contour2.f
make[1]: ifort: Command not found
make[1]: *** [contour2.o] Error 127
make[1]: Leaving directory `/home/wyf/weinberg_genus/Package/Source'
make: *** [everything] Error 2[/COLOR]

totally confused, looks "[COLOR="Red"]alias ifort=/opt/intel/Compiler/11.0/083/bin/ia32/ifort[/COLOR]" in .bashrc file is not enough for installing a package, but enough for executing a command in a terminal?
> **adameye said:**
> thanks for your reply, I think I have figured put the problem of "ifort" problem by adding the line "alias ifort=/opt/intel/Compiler/11.0/083/bin/ia32/ifort" into .bashrc file.

but now I have another concern, I'm not sure if I have installed a package correctly:
 
[COLOR="Red"]wyf@wyf-desktop:~/software$ make futil
ifort -ftz -mp1 -posixlib -Vaxlib -c gasdev.for ran1.f src3ft.f snrsq.f scopy.f sscal.f && ar -rlv \
libfutil.a gasdev.o ran1.o src3ft.o snrsq.o scopy.o sscal.o
ifort: command line warning #10156: ignoring option '-p'; no argument required
src3ft.f(656): (col. 10) remark: LOOP WAS VECTORIZED.
src3ft.f(599): (col. 12) remark: LOOP WAS VECTORIZED.
src3ft.f(41): (col. 5) remark: LOOP WAS VECTORIZED.
src3ft.f(66): (col. 5) remark: LOOP WAS VECTORIZED.
src3ft.f(145): (col. 10) remark: LOOP WAS VECTORIZED.
src3ft.f(228): (col. 16) remark: LOOP WAS VECTORIZED.
src3ft.f(229): (col. 16) remark: LOOP WAS VECTORIZED.
src3ft.f(230): (col. 16) remark: LOOP WAS VECTORIZED.
snrsq.f(10): (col. 10) remark: LOOP WAS VECTORIZED.
r - gasdev.o
r - ran1.o
r - src3ft.o
r - snrsq.o
r - scopy.o
r - sscal.o
[/COLOR]
looks installation fail?

---

