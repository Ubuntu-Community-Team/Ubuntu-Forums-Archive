---
title: "krusader under ubuntu 5.04 / gnome"
date: 2006-01-11
forum: General Help
---

### Post by trancephorm on 2006-01-11
trying to install krusader under gnome... i saw on some forum it is enough to install kdelibs, but it seems it's not quite like that... here is what i get:

root@mm:/home/pyc/Desktop/archives # dpkg -i krusader_1.60.1-0ubuntu1_i386.deb
(Reading database ... 63637 files and directories currently installed.)
Preparing to replace krusader 1.60.1-0ubuntu1 (using krusader_1.60.1-0ubuntu1_i386.deb) ...
Unpacking replacement krusader ...
dpkg: dependency problems prevent configuration of krusader:
 krusader depends on kdelibs4c2a (>= 4:3.5.0); however:
  Package kdelibs4c2a is not installed.
 krusader depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 krusader depends on libfontconfig1 (>= 2.3.0); however:
  Version of libfontconfig1 on system is 2.2.3-4ubuntu7.
 krusader depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0-0pre6ubuntu7.
 krusader depends on libidn11 (>= 0.5.18); however:
  Version of libidn11 on system is 0.5.2-3.
 krusader depends on libqt3-mt (>= 3:3.3.5); however:
  Package libqt3-mt is not installed.
 krusader depends on libstdc++6 (>= 4.0.2-4); however:
  Package libstdc++6 is not installed.
dpkg: error processing krusader (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 krusader


.........and  when i try to install kdelibs4c2a, it goes like this:

root@mm:/home/pyc/Desktop/archives # apt-get install kdelibs4c2a
Reading package lists... Done
Building dependency tree... Done
Package kdelibs4c2a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kdelibs4c2a has no installation candidate


i know this problem is probably very stupid, but i'm in real hurry to get this thing working, so i'm asking for help here.

btw, i'm not so much into desktop linux (much much more using it's server side), but ubuntu distribution is already my favorite (installed it just a few hours ago), and i really really like gnome desktop, it's so clean and intuitive if i could just make krusader work... i would throw my WinXP in garbage at once. :)

pls hlp!

---

