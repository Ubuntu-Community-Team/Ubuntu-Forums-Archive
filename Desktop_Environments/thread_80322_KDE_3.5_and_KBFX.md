---
title: "KDE 3.5 and KBFX?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by pistoli on 2005-10-21
I have tried several times and with several versions to install KBFX on 3.5 with no success.  Everything seems to compile correctly, but when I go to "add appletts", KBFX is not listed.  Has anyone else with KDE 3.5 tried installing this?

---

### Post by Jonathan2007 on 2005-10-21
I am running the latest version of KBFX (or at least I think I have the latest version) on KDE 3.5 Beta 1.

---

### Post by pistoli on 2005-10-21
Did you ./configure with any special options?

---

### Post by theFallen on 2006-04-16
It didn't appear also and I did only ./configure. But on the HP's HowTo the commands are listed as follows:

    * make -f Makefile.cvs
    * ./configure --prefix=`kde-config --prefix`
    * make
    * make install (AS ROOT)

and it works then.

---

### Post by gingermark on 2006-04-16
Attached is a KBFX deb file I made ages ago. It seems to work ok on my system (with KDE 3.5.2). Anyways, it's there if you want to give it a go, although I make no promises - I'm hardly an expert packager, just a user of checkinstall!

---

### Post by gingermark on 2006-04-16
Just popped onto kde-apps.org, and whaddya know? There is a deb for Breezy for KBFX 0.4.9.1 [here](http://kde-apps.org/content/show.php?content=37958).

---

