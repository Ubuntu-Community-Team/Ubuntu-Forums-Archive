---
title: "E17 Compile Error"
date: 2008-05-07
forum: Desktop Environments
---

### Post by The_PhAnT0m on 2008-05-07
I downloaded E17 from CVS. All the EFL libraries seemed to compile fine until I actually got to Enlightenment. When I tried to compile it this error was displayed (Note that I am installing E17 to "/opt/e"),

```
...
...
/opt/e/bin/edje_cc: Wrote      2019 bytes (   2Kb) for "collections/0" collection entry
/opt/e/bin/edje_cc: Wrote       537 bytes (   1Kb) for "collections/1" collection entry
sh: embryo_cc: not found
/opt/e/bin/edje_cc: Warning. Compiling script code not clean.
make[4]: *** [default.edj] Error 255
make[4]: Leaving directory `/home/phantom/usr/src/e17/e17/apps/e/data/init'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/phantom/usr/src/e17/e17/apps/e/data/init'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/phantom/usr/src/e17/e17/apps/e/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/phantom/usr/src/e17/e17/apps/e'
make: *** [all] Error 2

```

Edje and all the other Enlightenment dependencies appeared to compile fine. Anyone have any idea to what is causing the error?

Thanks

---

### Post by smartboyathome on 2008-05-07
Try running a make clean, and then compiling again. Are you installing using Rui Pais's deb file?

---

### Post by The_PhAnT0m on 2008-05-07
Thanks for responding.

First to make things clear, I did NOT take the path of least resistance. I am compiling this in part to act as a learning experience for myself. Anyway, I compiled it by hand. I manually checked out each library from CVS and than compiled each one individually, to make sure I had all the features compiled in that I wanted (no .deb's are involved). I did try to do the 'make uninstall && make clean' cycle on both Enlightenment and Edje. I even tried using the Edje from the official snapshot but I encountered the same error. Just in case it makes any difference, I am using a Turion AMD64 processor and a 64-bit version of Ubuntu(I'm on a laptop). I also used the '-march=athlon64' compile option. Again, I greatly appreciate your help.

---

### Post by The_PhAnT0m on 2008-05-08
Well I figured out by problem. I forget to add '/opt/e/bin' to my path and so it couldn't find the scripts or whatever it needed to finish compiling. After I added it everything went perfectly. Now I get to learn how to use a new window manager. :)

---

