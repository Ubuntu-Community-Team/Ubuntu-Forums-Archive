---
title: "fgrun in Ubuntu 10.10"
date: 2010-11-04
forum: Gaming &amp; Leisure
---

### Post by ubudog on 2010-11-04
So, I downloaded and compiled FlightGear 2.0 and Fgrun, both from their websites.  FlightGear compiled fine, same with FGrun.  It starts fine using the command:
```
fgrun
```

What should I put for the options?  I can't find the root FG directory, is this because I compiled from source?  Thanks.

---

### Post by hihihi100 on 2010-12-14
FGFS 2.0 or 1.9?  THe one I installed a couple of days ago was the one found in the software center, 1.9 not 2.0. Did u install 2.0 from their official site? I thought the newest version for Ubuntu was still 1.9 

How did u compile fgrun? I am trying to do that, and I am told by the system that I need PLIB, I googled, found it and downloaded, extracted and the terminal keeps saying: read the last lines:

```
Making install in src
make[1]: Entering directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src'
Making install in util
make[2]: Entering directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src/util'
make[3]: Entering directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src/util'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /usr/bin/install -c -m 644 'libplibul.a' '/usr/lib/libplibul.a'
/usr/bin/install: cannot create regular file `/usr/lib/libplibul.a': Permission denied
make[3]: *** [install-libLIBRARIES] Error 1
make[3]: Leaving directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src/util'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src/util'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/share/games/FlightGearPlib/plib-1.8.5/src'
make: *** [install-recursive] Error 1
hihihi100@hihihi100-laptop:/usr/share/games/FlightGearPlib/plib-1.8.5$ 

```

The most interesting part:

```
 /usr/bin/install -c -m 644 'libplibul.a' '/usr/lib/libplibul.a'
/usr/bin/install: cannot create regular file `/usr/lib/libplibul.a': Permission denied
```

Do u know any particular user that may have a .deb FGFRun file? Or if there r plans to develop one?

cya

---

### Post by ubudog on 2010-12-15
I compiled FlightGear 2.0 from source from the official FG website.  PLIB can be installed using synaptic, you don't need to compile from source for that.  Also, check out PlayDeb, that can get you the latest version of FG.  That's what I did, and all is well.

---

