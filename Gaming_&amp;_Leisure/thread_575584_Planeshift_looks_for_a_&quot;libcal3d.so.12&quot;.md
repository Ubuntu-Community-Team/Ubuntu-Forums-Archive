---
title: "Planeshift looks for a &quot;libcal3d.so.12&quot;"
date: 2007-10-14
forum: Gaming &amp; Leisure
---

### Post by almkglor on 2007-10-14
I'm running on an AMD64 version of Ubuntu (I probably shouldn't have, it gives more headaches than x86 and it's not like I actually use my Linux box for serious numbercrunching) and attempting to run PlaneShift gives:
```
./psc: error while loading shared libraries: libcal3d.so.12: cannot open shared object file: No such file or directory

```

I've looked up "libcal" on synaptic, and installed the repository version, "libcal3d11c2a".  However, it still doesn't work (same message as above).

Looking at libcal3d11c2a's installed files shows that it installs under "/usr/lib/libcal3d.so.11", not 12.

Additional details:
PlaneShift Setup and PlaneShift Updater work.  I've already run Updater, still the same problem.
I installed the 64-bit version of PlaneShift.  I might decide to uninstall it and try installing the 32-bit version to see if it helps.

---

### Post by almkglor on 2007-10-14
That's right, I'm stupid.  Those of you who had the same problem, look for a file named "fixlibs.sh" in the PlaneShift installation folder.  Just go to that directory and run ./fixlibs.sh

---

