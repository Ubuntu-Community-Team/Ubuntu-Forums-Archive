---
title: "How can I install KDE 4.2.3 under Hardy Heron?"
date: 2009-05-09
forum: General Help
---

### Post by u'b'u'n't'u on 2009-05-09
I have Harry Heron and I do not want to upgrade to jaunty because of performance issues, but can i install Kde 4.2.3 under Herdy


Thanks, 
 u'b'u'n't'u

---

### Post by u'b'u'n't'u on 2009-05-09
not necesarily 4.3.2, but 4.2

---

### Post by aschwerin.moses on 2009-05-10
even i would like to know this.. someone please help...

---

### Post by douglett on 2009-05-26
ditto that

---

### Post by u'b'u'n't'u on 2009-07-28
anyone???:(

---

### Post by jonobe on 2009-07-28
perhaps you could download kubuntu hardy - which is basically ubuntu with kde already installed as part of it.

---

### Post by hibliss on 2009-07-28
> Alternatively, you could use KDE Nightly, which is a nightly build of the development trunk.

Simply add

Code: Select all
    # Neon Nightly Builds
    deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main



to your sources.list and install the following packages:

Code: Select all
    kde-nightly-kdepim - runtime components from the official KDE release
    kde-nightly-kdeutils - runtime components from the official KDE release
    kde-nightly-kdenetwork - KDE network applications (nightly build)
    kde-nightly-kdegraphics - KDE graphic applications (nightly build)
    kde-nightly-kdeplasma-addons - runtime components from the official KDE release
    kde-nightly-kdebase - runtime components from the official KDE release
    kde-nightly-kdepimlibs - core libraries for KDE PIM 4 applications
    kde-nightly-kdelibs - core libraries for all KDE 4 applications
    kde-nightly-kdesupport - KDESupport stuff
    kde-nightly-kdemultimedia - KDE multimedia applications (nightly build)
    kde-nightly - Project Neon (KDE Nightly)
    kde-nightly-strigi - fast indexing and searching tool for your personal data (daemon)
    kde-nightly-taglib - TagLib Audio Meta-Data Library



And simply choose KDE-Nightly in KDM

BUT this might be very unstable ! For instance, I cannot unlock my computer after the screensaver gets activated ! So use with caution ! You you do not know what you are doing, do not use this version !
Alternatively, you could use KDE Nightly, which is a nightly build of the development trunk.

Simply add

```
# Neon Nightly Builds
deb http://ppa.launchpad.net/project-neon/ubuntu hardy main
```

to your sources.list and install the following packages:

```
kde-nightly-kdepim - runtime components from the official KDE release
kde-nightly-kdeutils - runtime components from the official KDE release
kde-nightly-kdenetwork - KDE network applications (nightly build)
kde-nightly-kdegraphics - KDE graphic applications (nightly build)
kde-nightly-kdeplasma-addons - runtime components from the official KDE release
kde-nightly-kdebase - runtime components from the official KDE release
kde-nightly-kdepimlibs - core libraries for KDE PIM 4 applications
kde-nightly-kdelibs - core libraries for all KDE 4 applications
kde-nightly-kdesupport - KDESupport stuff
kde-nightly-kdemultimedia - KDE multimedia applications (nightly build)
kde-nightly - Project Neon (KDE Nightly)
kde-nightly-strigi - fast indexing and searching tool for your personal data (daemon)
kde-nightly-taglib - TagLib Audio Meta-Data Library
```

And simply choose KDE-Nightly in KDM

[color=red]**BUT**[/color] this might be very unstable ! For instance, I cannot unlock my computer after the screensaver gets activated ! So use with caution ! You you do not know what you are doing, do not use this version !
One moment...
Last edited by Cypher on Mon Oct 13, 2008 4:25 pm, edited 1 time in total.
Cypher, proud to be a member of KDE forums since 2008-Oct.


I use KDE nightly, which is the development branch, and seems to be what you want.

Add the line above for Hardy to your software sources and get the kde-nightly package.

Next time you boot, pick KDE Nightly as you session choice.

[http://amarok.kde.org/wiki/User:Apachelogger/Project_Neon/KDE/Info]("http://amarok.kde.org/wiki/User:Apachelogger/Project_Neon/KDE/Info")

---

