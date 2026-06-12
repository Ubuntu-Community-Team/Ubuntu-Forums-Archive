---
title: "Gnuplot does not produce plots under Kubuntu"
date: 2014-02-18
forum: Education &amp; Science
---

### Post by lotharlorraine on 2014-02-18
Hello folks. 


I have the following problem. 


I have no difficulty whatsoever using Gnuplot with ubuntu, everything works perfectly. 


But when installed on Kubuntu, it seems impossible to get plots. 
For instance writing "plot sin(x) " spawns no graphic or plot, nothing additional shows up. 

I suppose this likely lies in required libraries not naturally present in a Kubuntu or KDE environment. 


Where could I find them? 


Many thanks in advance!

---

### Post by tgalati4 on 2014-02-18
tgalati4@Mint14-Extensa ~ $ apt-cache depends gnuplot
gnuplot
 |Depends: gnuplot-nox
    gnuplot-qt
    gnuplot-x11
 |Depends: gnuplot-x11
    gnuplot-qt
  Depends: gnuplot-qt
  Suggests: gnuplot-doc

tgalati4@Mint14-Extensa ~ $ apt-cache depends gnuplot-x11
gnuplot-x11
  Depends: libc6
  Depends: libcairo2
  Depends: libedit2
  Depends: libgcc1
 |Depends: libgd2-noxpm
  Depends: libgd2-xpm
  Depends: libglib2.0-0
  Depends: liblua5.1-0
  Depends: libpango1.0-0
  Depends: libstdc++6
  Depends: libwxbase2.8-0
 ** Depends: libwxgtk2.8-0**
  Depends: libx11-6
  Suggests: gnuplot-doc
  Conflicts: gnuplot-nox
    gnuplot-qt
  Conflicts: gnuplot-nox:i386
    gnuplot-qt:i386
  Conflicts: gnuplot-qt
  Conflicts: gnuplot-qt:i386
  Conflicts: gnuplot-x11:i386

---

