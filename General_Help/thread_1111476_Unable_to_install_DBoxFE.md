---
title: "Unable to install DBoxFE"
date: 2009-03-30
forum: General Help
---

### Post by peyre on 2009-03-30
I'm setting up a machine with Xubuntu 8.10, and I want to run my old DOS games.  DOSBox installed like a charm, but now I'd like to set up DBoxFE so I can have a nice GUI front end.

I downloaded the source, ran ./configure, and it said it was missing qmake.  So I opened Synaptic and installed qt3-dev-tools and qt3-designer.  Now ./configure runs fine, but make -f Makefile returns 
```
/usr/share/qt3/bin/uic ui/dboxfe.ui -o .unix/ui/dboxfe.h
uic: Could not open output file '.unix/ui/dboxfe.h
make: *** [.unix/ui/dboxfe.h] Error 1
```

Any idea what's going on?

---

### Post by ashmew2 on 2009-04-16
You need to install libqt4-core , build-essential for it to successfully compile. Just do that..

---

### Post by peyre on 2009-04-17
No good, libqt4core is already installed.  :(

I also tried installing qt4-dev-tools.  Still no go.

And I've installed qt3-dev-tools-compat, but no good.

But looking at it again, somewhere along the way, the error I'm getting changed.  Now it says:

```
/usr/share/qt3/bin/uic ui/profile.ui -o .unix/ui/profile.h
uic: File generated with too recent version of Qt Designer (4.0 vs. 3.3.8b)
make: *** [.unix/ui/profile.h] Error 1
```

---

### Post by ashmew2 on 2009-04-19
Just take a look here : [http://ubuntuforums.org/showthread.php?t=1126563](http://ubuntuforums.org/showthread.php?t=1126563)
Maybe itll help you..

---

### Post by peyre on 2009-04-19
Thanks!  I tried that, but I'm still erroring out:
```
/usr/share/qt3/bin/uic ui/dboxfe.ui -o .unix/ui/dboxfe.h
uic: Could not open output file '.unix/ui/dboxfe.h'
make: *** [.unix/ui/dboxfe.h] Error 1
```

---

