---
title: "The latest fontconfig upgrade screwed up MS fonts"
date: 2006-08-19
forum: Desktop Environments
---

### Post by justy0 on 2006-08-19
I have performed dist-upgrade as usual,
and noticed that all MS fonts suddenly look ugly.
I am using PC-BSD fonts.conf files from this
how-to [http://www.ubuntuforums.org/showthread.php?t=208396](http://www.ubuntuforums.org/showthread.php?t=208396)
Everything worked for several weeks.
Now it is broken.
I am using Dapper Drake. Kernel 2.6.15-26-386

Thanks

---

### Post by justy0 on 2006-08-19
OK, so I figured it out myself
The problem was caused by packages from
XGL/Compiz repository, which seem to be buggy.
I was able to restore the original Dapper
packages from Ubuntu repository and things turned normal
(btw. if you wonder which packages, then it
was libfreetype6, libfontconfig1 and libvte4
(and all related ones))

---

