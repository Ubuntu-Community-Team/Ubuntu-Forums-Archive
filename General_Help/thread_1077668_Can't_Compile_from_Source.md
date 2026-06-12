---
title: "Can't Compile from Source"
date: 2009-02-22
forum: General Help
---

### Post by jack24 on 2009-02-22
I can't get anything to compile from source.  Always get this:
> Making all in tools
make[2]: Entering directory `/home/l/Download/tracker_related/gmime-2.4.0/tools'
Making all in .
make[3]: Entering directory `/home/l/Download/tracker_related/gmime-2.4.0/tools'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/l/Download/tracker_related/gmime-2.4.0/tools'
'
I'm using Intrepid 64-bit and recently upgraded to the 2.6.28-8-generic kernel.  Does anybody know if that could be the problem?

---

### Post by jpeddicord on 2009-02-22
Don't run make from inside the tools directory, run it from the top of the source: gmime-2.4.0.

If make still does nothing, then try cleaning and reconfiguring:
```
make distclean
./configure
make
```

---

