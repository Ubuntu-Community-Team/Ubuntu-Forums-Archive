---
title: "How to install D2X-XL"
date: 2012-07-28
forum: Gaming &amp; Leisure
---

### Post by Rhemat on 2012-07-28
Heya All,

I tried to install D2X-XL following the instructions posted here:

[http://www.descent2.de/install-frames.html](http://www.descent2.de/install-frames.html)

However, all I get in the end, with the make command is this:

```


make  all-recursive
make[1]: Entering directory `/opt/d2x-xl-src-1.16.14/d2x-xl-makefiles'
Making all in 2d
make[2]: Entering directory `/opt/d2x-xl-src-1.16.14/d2x-xl-makefiles/2d'
make[2]: *** No rule to make target `bitblt.o', needed by `lib2d.a'.  Stop.
make[2]: Leaving directory `/opt/d2x-xl-src-1.16.14/d2x-xl-makefiles/2d'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/d2x-xl-src-1.16.14/d2x-xl-makefiles'
make: *** [all] Error 2

```

I had a hard time interpreting his instructions (since he doesn't state exactly which directory he wants the user in), but all seemed well until the make command.

I tried getting the files via svn, but I get this weird error:

```

svn: Non-numeric change argument (o) given to -c

```

I've also tried installing the Windows version of D2X-XL in WINE, but that doesn't work either.  It seems to install fine, but I'm left without an executable.  I've also tried running just the Descent II installer via Wine, but that didn't work either.

What am I doing wrong, or is there a better way to play Descent II?

---

### Post by donkyhotay on 2012-07-28
Have you tried D2X rebirth? There is a deb file available for it [here](http://files.crnatural.net/pool/contrib/d/d2x-rebirth-full/). But if you really need D2X-XL then the folder doesn't matter when compiling. Did you make certain you installed all the prerequisites? The instructions state it has it's own special version of SDL.

---

### Post by Rhemat on 2012-07-29
I installed the DEB package, without issue.  I placed all of the files from the Descent II disc to /usr/local/games/d2x-rebirth/data, /usr/local/share/games/d2x-rebirth/data, but I get this message:

```

Incomplete or Missing Descent 2 Data files.
You need either the demo data files (from package d2x-rebirth-demo), or the data files from the (purchased) Descent 2 game.
TO RUN THE DEMO LEVELS, you are missing d2demo.pig d2demo.hog d2demo.ham . TO RUN THE FULL VERSION, you are missing descent2.ham descent2.s11 water.pig alien2.pig ice.pig groupa.pig fire.pig alien1.pig descent2.s22 descent2.hog .
Either reinstall d2x-rebirth-demo, or copy the missing full version files as administrator to /usr/local/games/d2x-rebirth/data/.
See installation instructions in /usr/share/d2x-rebirth/NSTALL.txt.
Purchase the Descent 2 game at http://www.gog.com/en/gamecard/descent_1_descent_2. 

```

I also tried re-installing it.  The files I copied are:

ben-h.mve
hmidet.386
hmimdrv.386
intro-l.mvl
other-l.mvl
robots-h.mvl
setup.exe
descent2.sow
hmidrv.386
intro-h.mvl
other-h.mvl
README.txt
robots-l.mvl

Am I supposed to extract the contents of the descent2.sow file?

Thanks in advance.

---

