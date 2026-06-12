---
title: "PerlQt make problem"
date: 2006-02-17
forum: Desktop Environments
---

### Post by tauro on 2006-02-17
Hi ,

In order to get mail strainer properly working (superkaramba widget)  , i must install perlqt 

I already did: ( instruction from the site [www.cpan.org](www.cpan.org) )

1) Decompress and unpacked the module.tar.gz ->was successful
2) Trying to Build :
    perl Makefile.PL -> was successful
    make  -> errors

The errors that i get in make are the following (has to do with not finding -lsmokeqt)
```

Running Mkbootstrap for Qt ()
chmod 644 Qt.bs
rm -f blib/arch/auto/Qt/Qt.so
LD_RUN_PATH=":/usr/lib" g++  -shared -L/usr/local/lib Qt.o handlers.o -Wl,--rpath -Wl,/usr/lib -o blib/arch/auto/Qt/Qt.so   -lsmokeqt -L/usr/lib -L/usr/X11R6/lib -lcrypt -lqt-mt -lpng -lz -lm -lXext -lX11 -lSM -lICE -lpthread
/usr/bin/ld: cannot find -lsmokeqt
collect2: ld returned 1 exit status
make[2]: *** [blib/arch/auto/Qt/Qt.so] Error 1
make[2]: Leaving directory `/home/jay/perlqt/PerlQt-3.009/PerlQt'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jay/perlqt/PerlQt-3.009'
make: *** [all] Error 2

```

Does anyone know a solution /workaround for this problem ?

---

