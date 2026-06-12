---
title: "library not recognized?!"
date: 2009-02-23
forum: General Help
---

### Post by Timtro on 2009-02-23
Hi all,

I have a frustrating problem.

I'm trying to compile gnuplot complete with pdf support. I got pdflib lite and build it and installed it, but now when I compile gnuplot,

```

make[2]: Entering directory `/home/timtro/Downloads/gnuplot-4.2.4/demo'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/timtro/Downloads/gnuplot-4.2.4/demo'
Making all in tutorial
make[2]: Entering directory `/home/timtro/Downloads/gnuplot-4.2.4/tutorial'
if test -x ../src/gnuplot ; then GNUPLOT_PS_DIR=../term/PostScript GNUPLOT_LIB=. GNUTERM=latex ../src/gnuplot eg1.plt ; else gnuplot eg1.plt ; fi
../src/gnuplot: error while loading shared libraries: libpdf.so.6: cannot open shared object file: No such file or directory
make[2]: *** [eg1.tex] Error 127
make[2]: Leaving directory `/home/timtro/Downloads/gnuplot-4.2.4/tutorial'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/timtro/Downloads/gnuplot-4.2.4'
make: *** [all] Error 2

```


it actually let me build and install at some point, but when I tried to run, it said it couldn't find the same lib. I'm thinking one of my PATHs is off.

I'm not sure if I'm barking up the wrong tree, but LD_LIBRARY_PATH echos null.

Any ideas?

Thanks!

---

### Post by geraldm on 2009-02-23
You could have set the LD_LIBRARY_PATH environment variable to point to the library directory.
linux works out of the cache.  After you installed, you may still need to flush the cache so the newly installed lib will be seen. 
Code:
sudo ldconfig

---

### Post by Timtro on 2009-02-23
> **geraldm said:**
> You could have set the LD_LIBRARY_PATH environment variable to point to the library directory.
linux works out of the cache.  After you installed, you may still need to flush the cache so the newly installed lib will be seen. 
Code:
sudo ldconfig

Worked like a charm. I restarted my computer (I actually got back out of bed because it was bugging me so much), and I did the ldconfig, so I'm not sure which, but I'm relatively confident you were correct about the problem. I wasn't aware of this. Thanks a million!

Out of curiosity, why did I not have to do this when I do the exact same thing on Debian?

Cheers,


Tim.

---

