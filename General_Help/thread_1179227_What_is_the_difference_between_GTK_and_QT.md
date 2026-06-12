---
title: "What is the difference between GTK and QT?"
date: 2009-06-05
forum: General Help
---

### Post by demonon on 2009-06-05
Hi,

just a second ago I tried to install Peazip.
But one problem, it comes with QT and GTK.
From what I heard GTK is written in C and QT in C++. Also I heard QT is very ugly.
Which one is the best to get.
And I also would like to know if Peazip is a native x64 software.
I use Ubuntu 9.04 x64
Sincerely,

-Demonon.

---

### Post by Tibuda on 2009-06-05
Qt if you use KDE and Gtk+ if you use anything else.

---

### Post by decoherence on 2009-06-05
Qt and Gtk+ are widget toolkits. Basically they allow you to create (relatively) consistent user interfaces, (relatively) easily.

The difference between them, aside from not being compatible, is mostly historic. At first, Qt was released under a license which many said was not compatible with open source principals. By the time this issue was addressed, GTK+ and GNOME had gained significant traction and so both toolkits are still around.

Qt4 is generally regarded as being nicer to work with than GTK+2. I don't develop for either, so I can't speak from personal experience (and I may have just started a religious war.) Whether it's ugly or not depends on the theme, but Qt4 allows for much slicker themes than Qt3 did.

---

### Post by Yellow Pasque on 2009-06-05
> * DEB (all) packages can be installed on 32 and 64 bit systems, please note that ia32-libs are required to run any 32 bit binary on 64 bit systems.
[third parts packagers: those packages can be transformed in i386 DEB if desired; i386 DEB can anyway be installed on 64 bit systems using dpkg -i --force-architecture]

It's a 32-bit program. Get the GTK2.

---

### Post by Legace on 2009-06-05
[http://www.wikivs.com/wiki/Qt_vs_GTK](http://www.wikivs.com/wiki/Qt_vs_GTK)

---

### Post by hyperdude111 on 2009-06-05
Qt looks native under KDE and gtk looks native under gnome. They each look alien under the wrong environments.

---

### Post by demonon on 2009-06-06
Wow!
Instead of one, I get 5 replies!
Thanks for all your help guys!

---

