---
title: "Problems installing debian package (Portabase)"
date: 2005-11-21
forum: Desktop Environments
---

### Post by bengtfalke on 2005-11-21
I am trying to install Portabase from a debian package that are supposed to work on Ubuntu. I get the following error:

dpkg: depedency problem
portabase is depending on libqt3c102-mt
If I remember correctly this package is replaced by something else. How do I point the installation to this new package?

Portabase is using Trolltechs interface if that gives you any clue

All help is welcome as I need this great program (Portabase).... ;o)

regrads/falke

---

### Post by Xian on 2005-11-22
It was replaced by the libqt3-mt package. However, if you are not using KDE or dependent applications then you can still swap out libqt3c102-mt on Breezy and it will run just fine. If there are any KDE apps on your system you will get more dep errors. AFAIK you can't point the deb package to another library without altering the spec file.

---

### Post by bengtfalke on 2005-11-23
Do you know where I can find and download this package (libqt3c102-mt)?
regards/falke

---

### Post by Xian on 2005-11-23
[QUOTE=bengtfalke]Do you know where I can find and download this package (libqt3c102-mt)?
[/QUOTE]
Sure, here you go: [libqt3c102-mt_3.3.3-7](http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3c102-mt_3.3.3-7ubuntu3_i386.deb).
Remember, you have to replace the current libqt3 with this version.

---

### Post by bengtfalke on 2005-11-24
What do you mean "replace"? How do I do that?
regards/falke

---

### Post by Xian on 2005-11-24
[QUOTE=bengtfalke]What do you mean "replace"? How do I do that?
[/QUOTE]
I simply mean that you can't install one on top of the other. If you aren't using any KDE category apps then you can remove the current libqt3 package on your system since nothing will depend upon it in the base system. Afterwards, you can then install the libqt3c102-mt deb file.

---

### Post by bengtfalke on 2005-11-24
Hmmm, I am using AmaroK.... and like it a lot. Do you think it will stop working.
regards/falke

---

### Post by Xian on 2005-11-24
It is possible since it is built against the KDE libraries.

---

