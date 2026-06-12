---
title: "Processor platform"
date: 2009-06-11
forum: General Help
---

### Post by thilina on 2009-06-11
Hi guyz,
         I currently hve a computer with a Intel Pentium 4 processor.I hve some *.deb packages downloaded from the Internet that works nicely on ma current pc.Im gonna buy a pc based on a AMD Phenom series processor.Will the packages that I've downloaded for ma current pc work with the new pc??will there be any platform complication (i386 & amd x86_64 ??)

---

### Post by WatchingThePain on 2009-06-11
I have done similar to  that and some apps failed to work but most were ok.
It's a bit like if you download an app for a processor that's not right and it says "Wrong Architecture" when it trys to install.
Best to Backup data before changing the CPU though.

Also this might help:

[www.debian-administration.org/article/Using_proprietary_i386_apps_on_an_amd64_system]("www.debian-administration.org/article/Using_proprietary_i386_apps_on_an_amd64_system")

---

### Post by ibuclaw on 2009-06-11
With debs, it matters what architecture you install them on, as they will throw you errors and such. But in a more generic sense, it doesn't really matter running 32bit apps in a 64bit OS, as 64bit is backwards compatible with 32bit, so long as you have the backwards compat libraries installed.

Regards
Iain

---

