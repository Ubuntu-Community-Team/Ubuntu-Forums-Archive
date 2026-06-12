---
title: "KDE and PyQt4 conflicting - how to resolve?"
date: 2007-05-31
forum: Desktop Environments
---

### Post by MagisterJoe on 2007-05-31
I'm trying to install python-qt4 and python-qt4-dev so that I can build a few PyQt4 GUIs from some Qt Designer 4 files.  When I run apt, I get:

```
sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-qt4: Depends: libqt4-core (>= 4.2.2) but it is not going to be installed
              Depends: libqt4-gui (>= 4.2.2) but it is not going to be installed
E: Broken packages
```

It turns out that I have libqt4-core-kdecopy installed (using Kubuntu), which is blocking the installation of libqt4-core.  Same for all other libqt4 files.  That seems fine, except that the package manager isn't smart enough to tell python-qt4 to use these libqt4 files instead.  What can I do so that I don't screw up my KDE desktop but still get PyQt4?

---

### Post by mlind on 2007-05-31
Does substituting apt-get with aptitude produce the same result?

---

### Post by MagisterJoe on 2007-05-31
Synaptic, Adept, and aptitude all produce the same results.

Ok, using the aptitude ui I get this message when I try to install libqt4-core:

libqt4-core-kdecopy [universe] conflicts with libqt4-core

python-qt4 still won't install without libqt4-core, and I'd really like to avoid breaking kde.

---

### Post by mlind on 2007-06-01
From *libqt4-core-kdecopy* description
> 
The -kdecopy version of Qt 4 is for KDE 4 developers only.  It is a build
of qt-copy from KDE's SVN and will always conflict with the normal Qt 4
packages.  No binary compatibility is guaranteed.


By looking the reverse depends
```

apt-cache rdepends libqt4-core-kdecopy 
libqt4-core-kdecopy
Reverse Depends:
  qt4-qtconfig-kdecopy
  qt4-dev-tools-kdecopy
  qt4-designer-kdecopy
  libqt4-sql-kdecopy
  libqt4-qt3support-kdecopy
  libqt4-gui-kdecopy
  libqt4-dev-kdecopy

```
can't you just remove this package and replace it with libqt4-core ?

```

sudo aptitude install python-qt4 libqt4-core libqt4-core-kdecopy-

```
(Notice the override specifier after the last package)

---

### Post by MagisterJoe on 2007-06-01
Huh.  I don't know what boneheaded install I ran that put that stuff on my computer - I'll try the replacement method when I get home today.  Thanks!

---

