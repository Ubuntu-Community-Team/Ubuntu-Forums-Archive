---
title: "Compiling latest Xephem from source (Edgy)"
date: 2007-01-01
forum: Education &amp; Science
---

### Post by navneeth on 2007-01-01
Hi,
 I would like to use Xephem. I see a few HowTo's here and elsewhere on the internet, but they seem to be pretty old, considering that they were written for older versions of Xephem and Ubuntu.

Can someone help me compile 3.7.2 in Edgy?

Thanks.

---

### Post by ssam on 2007-01-03
try with an old howto, and post any error messages you get.

---

### Post by kleeman on 2007-01-03
sudo apt-get install libmotif3 libmotif-dev

cd xephem-3.7.2/GUI/xephem
make  MOTIF=/usr/lib

worked on my AMD64 system. Nice software.....

---

### Post by navneeth on 2007-01-09
Hi,
  The e-mail notification doesn't work, I guess. That's the reason for the late reply. Thanks for your input.

I tried what kleeman said, and the output is pasted below. I had installed all motif files when I tried to install the program using the How-To available in this forum. 

```
navneeth@Tuxic:~$ sudo apt-get install libmotif3 libmotif-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmotif3 is already the newest version.
libmotif-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
navneeth@Tuxic:~$ cd xephem-3.7.2/GUI/xephem
navneeth@Tuxic:~/xephem-3.7.2/GUI/xephem$ make MOTIF=/usr/lib
cd ../../libastro; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libastro'
make[1]: `libastro.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libastro'
cd ../../libip; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libip'
make[1]: `libip.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libip'
cd ../../libjpegd; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libjpegd'
make[1]: `libjpegd.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libjpegd'
cd ../../liblilxml; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/liblilxml'
make[1]: `liblilxml.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/liblilxml'
cd ../../libpng; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libpng'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libpng'
cd ../../libz; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libz'
make[1]: `libz.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libz'
gcc -I../../libastro -I../../libip -I../../liblilxml -I../../libjpegd -I../../libpng -I../../libz -g -O2 -Wall -I/usr/lib -I/usr/X11R6/include   -c -o aavso.o aavso.c
In file included from aavso.c:12:
/usr/include/Xm/Xm.h:59:34: error: X11/extensions/Print.h: No such file or directory
In file included from aavso.c:12:
/usr/include/Xm/Xm.h:827: error: expected specifier-qualifier-list before ‘XPContext’
make: *** [aavso.o] Error 1
navneeth@Tuxic:~/xephem-3.7.2/GUI/xephem$ xephem
bash: xephem: command not found

```

---

### Post by kleeman on 2007-01-09
The error message shows a missing header file (Print.h) from a subdirectory X11/extensions/
If you go to this site:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

you can search for this header file and you find it is probably in

x11proto-print-dev

so do this:

sudo apt-get install x11proto-print-dev

and try to compile again

---

### Post by navneeth on 2007-01-10
*Arrgghh...I think Xephem could win the Most Irritating Installing Experience Award.*

I installed print-dev and compiled. There was a long list of what was being done, but for some reason I had to turn off the computer as soon as it was over, and I didn't make a copy of the things, too. :( Anyway, I tried running the command again, I think the error messages are the same as the last time(i.e. after installing that print.h). 


```
navneeth@Tuxic:~/xephem-3.7.2/GUI/xephem$ make MOTIF=/usr/lib
cd ../../libastro; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libastro'
make[1]: `libastro.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libastro'
cd ../../libip; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libip'
make[1]: `libip.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libip'
cd ../../libjpegd; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libjpegd'
make[1]: `libjpegd.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libjpegd'
cd ../../liblilxml; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/liblilxml'
make[1]: `liblilxml.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/liblilxml'
cd ../../libpng; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libpng'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libpng'
cd ../../libz; make
make[1]: Entering directory `/home/navneeth/xephem-3.7.2/libz'
make[1]: `libz.a' is up to date.
make[1]: Leaving directory `/home/navneeth/xephem-3.7.2/libz'
gcc -L../../libastro -L../../libip -L../../liblilxml -L../../libjpegd -L../../libpng -L../../libz -g -L/usr/lib -L/usr/X11R6/lib -o xephem aavso.o annotmenu.o broadcast.o calmenu.o closemenu.o compiler.o coordsmenu.o datamenu.o db.o dbmenu.o earthmap.o earthmenu.o fallbacks.o favmenu.o formats.o fsmenu.o gallerymenu.o glance.o gsc.o gscnet.o helpmenu.o homeio.o hznmenu.o indimenu.o imregmenu.o jpeg2pm.o jupmenu.o listmenu.o mainmenu.o marsmenu.o marsmmenu.o moonmenu.o moviemenu.o msgmenu.o netmenu.o objmenu.o obslog.o patchlevel.o plot_aux.o plotmenu.o preferences.o progress.o ps.o query.o rotated.o satmenu.o saveres.o scope.o sites.o skybinary.o skyeyep.o skyfifos.o skyfiltmenu.o skyfits.o skyhist.o skyip.o skylist.o skytoolbar.o skyviewmenu.o solsysmenu.o splash.o srchmenu.o sunmenu.o time.o tips.o trailmenu.o uranusmenu.o ucac.o usno.o versionmenu.o webdbmenu.o xe2.o xe3.o xephem.o xmisc.o /usr/lib/libXm.a -lXp -lXt -lXext -lXmu -lX11 -lastro -lip -llilxml -ljpegd -lpng -lz -lm
/usr/bin/ld: cannot find -lXp
collect2: ld returned 1 exit status
make: *** [xephem] Error 1

```

The last line says something about xlp, and after a simple search in google, I came up with this, although I don't understand what it means. 

> # When I build XEphem why do I see lots of errors about undefined references to symbols starting with Xp?

With some versions of Motif (including OpenMotif) you must link with the Xp library. In the link line of your Makefile just add -lXp after -lXm. The set of X libraries ends up looking something like this:

    -lXm -lXp -lXt -lXext -lX11

It is correct in the Linux section of the sample Makefile.smple included in the tar file distribution.


[http://www.maa.mhn.de/Tools/xephem-faq.html](http://www.maa.mhn.de/Tools/xephem-faq.html)

Thanks for your help.

---

### Post by kleeman on 2007-01-10
Looks like you are still missing some X11 development libraries. Try the following:

sudo apt-get install libxp-dev

and try to recompile

---

### Post by navneeth on 2007-01-10
Woohoo! I am in. :D

I installed the other file, too, and compiled (no error messages) but it wouldn't recognise
the 'xephem' command.

I had actually noted the INSTALL file previously in the xephem-3.7.2 directory. I guess even that didn't work because of all these "missing" files. 

```
 make MOTIF=../../libXm/linux86

```

This was the step after untarring. No error message here also and at last I was able to open xephem for the first time. There were a few more steps, and after fiddling around with the pathname of a directory containing some important files, I am finally able to run the program.

Thanks a lot, kleeman. You've been a great help!

---

### Post by kleeman on 2007-01-10
> **navneeth said:**
> Woohoo! I am in. :D

I installed the other file, too, and compiled (no error messages) but it wouldn't recognise
the 'xephem' command.

I had actually noted the INSTALL file previously in the xephem-3.7.2 directory. I guess even that didn't work because of all these "missing" files. 

```
 make MOTIF=../../libXm/linux86

```

This was the step after untarring. No error message here also and at last I was able to open xephem for the first time. There were a few more steps, and after fiddling around with the pathname of a directory containing some important files, I am finally able to run the program.

Thanks a lot, kleeman. You've been a great help!

I had to use the 

make MOTIF=/usr/lib

because I have an x86_64 system so the libraries in ../../libXm/linux86
did not work.
Glad to help!

---

### Post by Astrodan on 2007-02-24
Please help.  I'm trying to compile Xephem 3.7.2 on Ubuntu 6.10 and keep getting this error:

/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status
make: *** [xephem] Error 1
root@ubuntu:/home/dan/Xephem/xephem-3.7.2/GUI/xephem#  

Can someone tell me what I am missing?   I am truly an end user.  Computer is a plain clone, pentium 4.

Thanks,
Dan

---

### Post by kleeman on 2007-02-24
You are missing libraries. Try

sudo apt-get install libxmu-dev

and recompile.

---

### Post by Astrodan on 2007-02-25
Thanks ever so much Kleeman.    This was driving this newbie crazy, and, you proved why it was well worth the change to Linux.  

Best wishes,:)

---

### Post by Astrodan on 2007-03-13
A postscript to Xephem-3.7.2 and those attempting to compile the program from source.  Although I was successful in compiling the program, I did not get the files into the correct directories, and, problems were encountered, with the program wanting to close every time I went to the Sky View screen.  

Since I have a registered copy, I approached the Xephem User Group for assistance.  The original CD, Install routine, was also closing in a manner similar to the compiled version.  This was caused by the presence of some compiled code from my previous attempts.

Whether compiling Xephem from source, or, loading from the CDs, the builder must be certain that critical utilities are loaded first.  Csh, or Tcsh, must be working and selected to run the Install routine from CD.  If compiling from source, the previous libraries are a vital portion of the install.  But, equally important, is seeing the data and program exist in the proper directories.  

Clear skies,
Dan

---

