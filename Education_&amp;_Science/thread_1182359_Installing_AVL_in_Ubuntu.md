---
title: "Installing AVL in Ubuntu"
date: 2009-06-08
forum: Education &amp; Science
---

### Post by Eezyville on 2009-06-08
Ok this is the first time I've tried to make a how-to so bear with me. I will try to help you install AVL (Athena Vortex Lattice Program) in Ubuntu.
The setup that I am using is Ubuntu 8.10 (Intrepid Ibex) 64bit.

Now most of my how-to is based off of another how-to made by Icarosaurus. He made a how-to on installing Xfoil which was really useful on a recent project I had and I feel that AVL will be useful for future projects now that I will start my senior year come September '09. Icarosaurus' how-to is located here if you're wondering. [HTML]http://ubuntuforums.org/showthread.php?t=994912[/HTML]

First things first. You download the program from the MIT website here: [HTML]http://web.mit.edu/drela/Public/web/avl/[/HTML]
Extract the file in you home directory and open a shell in the folder ~/Avl. We need to edit some makefiles so lets get started in the plotlib directory.

**1)**
```
cd plotlib
gedit Makefile
```

we're gonna edit this so that its in double precision so look for the following lines and edit them.

look for:
```
PLTLIB = libPlt.a
```

and comment that line. Uncomment the line below it so that its:
```
PLTLIB = libPltDP.a
```

look for where it chooses the fortran compiler: 
```
FC = f77
```
and you can change f77 to g77 if you have g77 installed. In my experience g77 works best. If you're wondering how I installed g77 on Intrepid the look into this thread: [HTML]http://ubuntuforums.org/showthread.php?t=969198&page=2[/HTML]

Now right below the FC=f77 line you need to edit the double precision to turn it on. 

look for this line:
```
#DP = -r8
```
and change it to 
```
DP = -dbl
```

then look for
```
include ./config.make
```
and comment it out so that it looks like:
```
#include ./config.make
```
Now save and type in
```
make
```
to get libPltDP.a.

**2)**
Type in 
```
cd ../eispack
gedit Makefile
```

Change this:
```
#FC = f77
FC = ifort
FLG = -O
```
into this
```
FC = g77
#FC = ifort
FLG = -O -dbl
```
save and 
```
make
```

**3)**
Finally 
```
cd ../bin
gedit Makefile
```
look for 
```
BINDIR = .
```
and turn to
```
BINDIR = /usr/bin/
```
turn 
```
PLTOBJ = ../plotlib/libPlt.a
```
into
```
PLTOBJ = ../plotlib/libPltDP.a
```
Change the fortran compiler if you want.
Look for 
```
FFLAGS = -O
```
and change to 
```
FFLAGS = -O -dbl
```
Comment out everything between 
```
### Intel Fortran Compiler 8.x
```
and 
```
all:	 $(PROGS)
```
leave ```
all:	 $(PROGS)
```
uncommented. Keep it in the program.
Next just type in
```
make all
```
and wait a second. Then theoretically you should just type in sudo make install to install it but it gives me an Error 127. So just type in 
```
sudo mv avl /usr/bin
```

You can leave the directory and delete it now (keep the "runs" directory and the text documents to learn how to use it) because avl is installed. Just type in AVL to run it. 

This is what works for me and I'm sure I did something wrong so please correct me if I did.

---

### Post by ematwix on 2011-01-01
Hi all,
I have successfully installed AVL on MAC OSX 10.4 following the above instructions by Eezyville.

I know that this is an Ubuntu forum but I hope nobody will be hurt by this post (I beg your pardon in advance if it happens) but Unix is in the core of both OSs! 

Compilers:
**fortran** g77
**C** gcc

Pre-requisite: having installed X11.

All the make operations have been made in the X11 terminal, according to [http://www.whittlesey.us/misc/avl.php]("http://www.whittlesey.us/misc/avl.php")

the program can be launched both from the OSX terminal or by X11 terminal by typing ***avl***. The former does not work graphics, the latter works good for all the features.

Bye

---

