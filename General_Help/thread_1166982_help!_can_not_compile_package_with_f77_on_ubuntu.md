---
title: "help! can not compile package with f77 on ubuntu"
date: 2009-05-22
forum: General Help
---

### Post by adameye on 2009-05-22
I'm trying to compile a package on Ubuntu, errors:

f77 -fast -c -o contour2.o contour2.f
MAIN contour2:
sum:
ssort:
cc1: error: unrecognized command line option "-fast"
/usr/bin/f77: aborting compilation
make[1]: *** [contour2.o] Error 25
make[1]: Leaving directory `/home/wyf/Desktop/Package/Source'
make: *** [everything] Error 2

please help me, thanks

---

### Post by aJayRoo on 2009-05-22
I don't think -fast is a valid compiler flag for GNU compilers. It looks like you are compiling this using a Makefile. If so you will need to  remove the -fast flag from the Makefile. It is hard to give any specific advice without seeing the Makefile/source code. What program are you attempting to compile?

Hope that helps.

---

### Post by adameye on 2009-05-22
makefile: please tell me how to edit it! thanks




BINDIR=../Bin
FC= f77
FLINK=f77
FFLAGS=-fast
CC=cc
CLINK=cc
CFLAGS=-O
FLIB=
CLIB=

everything:  Makefile
	make contour2
	make contour3
	make contour6
	make gsmooth
	make cicden
	make delrho
	make multi
	make divide 
	make rhostats
	make mrhostats
	make rmask
	make poisson_den
	make scalar

thebasics:  Makefile
	make contour3
	make gsmooth
	make multi
	make divide
	make scalar

OBJS1=	contour2.o
contour2:	$(OBJS1) Makefile
	$(FLINK) $(FFLAGS) -o $(BINDIR)/contour2 $(OBJS1) $(FLIB)

OBJS2=	contour3.o
contour3:	$(OBJS2) Makefile
	$(FLINK) $(FFLAGS) -o $(BINDIR)/contour3 $(OBJS2) $(FLIB)

OBJS3=	gsmooth.o src3ft.o
gsmooth:	$(OBJS3) Makefile
	$(FLINK) $(FFLAGS) -o $(BINDIR)/gsmooth $(OBJS3) $(FLIB)

OBJS4=	cicden.o
cicden:	$(OBJS4) Makefile
	$(FLINK) $(FFLAGS) -o $(BINDIR)/cicden $(OBJS4) $(FLIB)

OBJS5=	delrho.o ftread.o ftwrite.o ssumc.o
delrho:	$(OBJS5) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/delrho $(OBJS5) $(CLIB)

OBJS6=	multi.o ftread.o ftwrite.o alloc.o
multi:	$(OBJS6) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/multi $(OBJS6) $(CLIB)

OBJS7=	divide.o ftread.o ftwrite.o alloc.o
divide:	$(OBJS7) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/divide $(OBJS7) $(CLIB)

OBJS8=	rhostats.o ftread.o ftwrite.o alloc.o
rhostats:	$(OBJS8) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/rhostats $(OBJS8) $(CLIB)

OBJS9=	mrhostats.o ftread.o ftwrite.o alloc.o
mrhostats:	$(OBJS9) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/mrhostats $(OBJS9) $(CLIB)

OBJS10=	rmask.o ftread.o ftwrite.o alloc.o
rmask:	$(OBJS10) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/rmask $(OBJS10) $(CLIB)

OBJS11=	poisson_den.o ranc.o alloc.o ftwrite.o
poisson_den:	$(OBJS11) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/poisson_den $(OBJS11) $(CLIB)

OBJS12=	scalar.o alloc.o ftread.o ftwrite.o
scalar:	$(OBJS12) Makefile
	$(CLINK) $(CFLAGS) -o $(BINDIR)/scalar $(OBJS12) $(CLIB)

OBJS13=	contour6.o
contour6:	$(OBJS13) Makefile
	$(FLINK) $(FFLAGS) -o $(BINDIR)/contour6 $(OBJS13) $(FLIB)




> **aJayRoo said:**
> I don't think -fast is a valid compiler flag for GNU compilers. It looks like you are compiling this using a Makefile. If so you will need to  remove the -fast flag from the Makefile. It is hard to give any specific advice without seeing the Makefile/source code. What program are you attempting to compile?

Hope that helps.

---

### Post by aJayRoo on 2009-05-22
Try removing -fast from the FFLAGS definition, ie. change this line:
```
FFLAGS=-fast
```
to:
```
FFLAGS=
```
See what happens then...

---

### Post by adameye on 2009-05-22
thanks, still not work..

make[1]: Entering directory `/home/wyf/Desktop/Package/Source'
f77   -c -o contour2.o contour2.f
   MAIN contour2:
   sum:
   ssort:
f77  -o ../Bin/contour2 contour2.o 
make[1]: Leaving directory `/home/wyf/Desktop/Package/Source'
make contour3
make[1]: Entering directory `/home/wyf/Desktop/Package/Source'
f77   -c -o contour3.o contour3.f
   MAIN contour3:
   sum:
   ssort:
   erfcc:
f77  -o ../Bin/contour3 contour3.o 
make[1]: Leaving directory `/home/wyf/Desktop/Package/Source'
make contour6
make[1]: Entering directory `/home/wyf/Desktop/Package/Source'
f77   -c -o contour6.o contour6.f
   MAIN contour6:
   sum:
   ssort:
   erfcc:
f77  -o ../Bin/contour6 contour6.o 
make[1]: Leaving directory `/home/wyf/Desktop/Package/Source'
make gsmooth
make[1]: Entering directory `/home/wyf/Desktop/Package/Source'
f77   -c -o gsmooth.o gsmooth.f
   MAIN:
f77   -c -o src3ft.o src3ft.f
   src3ft:
   realfft:
   cxfft3:
Warning on line 216: inconsistent calling sequences for cxfft3,
	arg 1: here complex variable, previously real variable.
	arg 6: here complex variable, previously real variable.
   cfft99:
Warning on line 513: inconsistent calling sequences for cfft99,
	arg 1: here real variable, previously complex variable.
	arg 2: here real variable, previously complex variable.
   cftfax:
   fact:
   cftrig:
   vpassm:
/tmp/fort77-9102-1.c:353: error: conflicting types for ‘cxfft3_’
/tmp/fort77-9102-1.c:173: error: previous declaration of ‘cxfft3_’ was here
/tmp/fort77-9102-1.c:434: error: conflicting types for ‘cfft99_’
/tmp/fort77-9102-1.c:370: error: previous declaration of ‘cfft99_’ was here
/usr/bin/f77: aborting compilation
make[1]: *** [src3ft.o] Error 25
make[1]: Leaving directory `/home/wyf/Desktop/Package/Source'
make: *** [everything] Error 2

---

