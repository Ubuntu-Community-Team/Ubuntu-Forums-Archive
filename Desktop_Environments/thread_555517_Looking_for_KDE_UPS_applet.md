---
title: "Looking for KDE UPS applet"
date: 2007-09-20
forum: Desktop Environments
---

### Post by vidak on 2007-09-20
Hi all!

I've just installed an APC UPS and made the config with apcupsd. I'm now searching for a nice KDE applet showing the battery status. I tried to use guidance-power-manager which said
This is not a laptop, quitting ...
(that's true indeed) I haven't found any KDE applet which would do the job. Tried to download kbatt applet but it wouldn't compile, since it didn't find the Qt libs, which were installed :(

Do you have any ideas? (I have seen a very nice applet for gnome, which was displayed after installing the ups :( )

---

### Post by bunker on 2007-09-20
You need the qt-dev package to compile qt programs.

If that fails, and the daemon it has a corresponding cli client you could try using a system monitor like conky.  You can execute shell commands and display the output with it.  These forums have plenty of info on how to set up conky.

---

### Post by vidak on 2007-09-20
Well, I had libqt3-mt-dev installed, tried to reconfigure kcheckgmail, which also needed the same libraries, that one had no problem at all... It would just be nice to have that applet on the taskbar, now I have to rewrite some superkaramba-theme... :(

---

### Post by bunker on 2007-09-22
Qt-mt is just the multi-threaded part of QT.  You most likely also need qt3-dev-tools, which has things like moc and qmake in it.

If in doubt install kdevelop - it has all these as dependancies.

---

