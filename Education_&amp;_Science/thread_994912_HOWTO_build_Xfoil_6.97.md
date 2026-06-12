---
title: "HOWTO build Xfoil 6.97"
date: 2008-11-27
forum: Education &amp; Science
---

### Post by Icarosaurus on 2008-11-27
I built a deb package for Ubuntu 32 bit, that's available here:
[http://giuschet.altervista.org/Ubuntu/]("http://giuschet.altervista.org/Ubuntu/")

Anyways... these are the instructions for building it, in double precision.
I'm Using Ubuntu 8.04 32 bit

**1)**
a) Get the program from here:
[http://web.mit.edu/drela/Public/web/xfoil/xfoil6.97.tar.gz]("http://web.mit.edu/drela/Public/web/xfoil/xfoil6.97.tar.gz")
b) Unpack the tarball and open a terminal in the created directory.

**2)**
```
cd orrs
pwd
cd src
gedit osmap.f
```

find this line in the file:

```
DATA OSFILE / '/var/local/codes/orrs/osmap.dat' /
```

and substitute **/var/local/codes/orrs** with the output of the pwd command.

**3)**
a)
```
cd ../bin
gedit Makefile_DP
```

look for
```
FLG = -O -r8
```
in the very first lines, and change it into:

```
FLG = -O -dbl
```

comment the intel fortran related flags, between the #=== marks

b)save the changes and
```
 make -f Makefile_DP osgen
 make -f Makefile_DP osmap.o
```

**4)**
```
cd ..
bin/osgen osmaps_ns.lst 

```

**5)**
a)
```
cd ../plotlib
gedit Makefile

```
comment  PLTLIB = libPlt.a and uncomment PLTLIB = libPltDP.a
```
#PLTLIB = libPlt.a
PLTLIB = libPltDP.a

```
comment **include ./config.make**
```
#include ./config.make
```
Look for
```
#DP = -r8
```
and change it into:
```
DP = -dbl
```
b)save the changes and
```
make
```
[B]
6)[/B]
```
cd ../bin
gedit Makefile
```
change:
```
BINDIR = .
```
into:
```
BINDIR = /usr/bin/
```
find this line
```
PLTOBJ = ../plotlib/libPlt.a 
``` 
and turn it into:
```
PLTOBJ = ../plotlib/libPltDP.a
```
look for:
```
FFLAGS  = -O 
```
and turn it into:
```
FFLAGS  = -O -dbl
```

comment all the lines after **### Intel Fortran Compiler** until the **all:** line (leave it uncommented).
[B]
7)[/B]
```
cd ../src
gedit pplot.f
```

look for
```
LOGICAL ERROR, LGETFN
```
and change it into:
```
LOGICAL ERROR, LGETFN, LERR
```
This solves a type mismatch error 

**8 )**
```
cd ../bin
make all
```

**9)**
If you want to install, just:
```
sudo make install
```

That's all folks.
You can start Xfoil by typing **./bin/xfoil** in the main directory or by typing **xfoil** anywhere if you installed it.
**Tips:**
**1** - you can start xfoil with
```

rlwrap -a -c xfoil

```
for preserving command completion and the correct behaviour of the keyboard
**2** - The display window tends to be cancelled when any other window moves over it.
A workaround for this is inserting in the Display section of your Xorg.conf the following:
```

Option "Backingstore" "true"

```
This tells the video driver to store the image hidden behind the windows.Thanks to Leandro from the Xfoil mailing list.

Let me know for problems and suggestions.

---

### Post by NiteSoul on 2009-10-23
I get the following error in Step 3 b):

Code: make -f Makefile_DP osgen

f77 -c -O -dbl ../src/osgen.f
/usr/bin/f77: Illegal option: -dbl
make: *** [osgen.o] Error 255

I appreciate your advice to solve it.

Thanks!

---

### Post by gabrielitos on 2011-05-23
Thanks a lot man! You solve my problems and now I can start my thesis without agonizing pain!
If I will meet you somewhere in the world, I will offer you a beer for sure!

---

### Post by zhanfei on 2012-09-19
I have the similar problem. F77 seems to have been properly installed on my laptop. I can compile a source code with it, no problem, but when I install other softwares that depend on F77, it doesn't work. Especially, I got the error message:
/usr/bin/f77: Illgegal option: --version,
 
when I checked its version.
 
What is the problem here?
 
> **NiteSoul said:**
> I get the following error in Step 3 b):
 
Code: make -f Makefile_DP osgen
 
f77 -c -O -dbl ../src/osgen.f
/usr/bin/f77: Illegal option: -dbl
make: *** [osgen.o] Error 255
 
I appreciate your advice to solve it.
 
Thanks!

---

### Post by overdrank on 2012-09-19
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

