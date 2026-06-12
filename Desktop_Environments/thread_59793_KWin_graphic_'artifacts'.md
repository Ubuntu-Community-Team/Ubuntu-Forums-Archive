---
title: "KWin graphic 'artifacts'"
date: 2005-08-25
forum: Desktop Environments
---

### Post by syntruth on 2005-08-25
Hiya, 

Long time KDE user, recently migrated from Gentoo to Kubuntu.  I've noticed something strange that is happening on my user-installed styles and windecs: I'm getting 'stippled' graphic artifacts along the bottom part of the window decoration and, sometimes, along the top window title bar.  Depending on which style/windec I am installing, I've had to feed configure the --prefix arg, but otherewise, I've done nothing different.  Normally, if configure does not use kde-config to figure out the correct install dir, I use --prefix=`kde-config --prefix` for configure.  I say this, because I thought perhaps it's a pathing issue of some sort regarding KDE and/or Qt.

Anyone else have this issue?

---

### Post by syntruth on 2005-08-25
...as an update to this, this only happens with windecs I install.  All windecs that come with the Kubuntu KDE do *not* exhibit this behavior, leading me to believe it has something to do with the Qt paths and such.  I'm gonna try to remove all Qt installations and reinstall them, then try to recompile, but does anyone know what Qt paths the default KDE package maintainers are using when compiline KDE for Kubuntu?

UPDATE:

They use /usr/share/qt3  (--with-qt-dir=/usr/share/qt3) 

I have rebuilt the Grover (my fave) windec and restarted my machine, and now all seems to be better.  My *guess* is that because I had loaded qtlibs from another directory that there was some corrupted memory floating around.

Bah, spoke too soon...still getting the stipples, but now they are not nearly as big or pronounced...could be still leaks from my self-compiled style (QtCurve) however, so off to redo that as well.

---

