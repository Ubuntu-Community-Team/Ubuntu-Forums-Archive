---
title: "Skype - installed fine but looks terrible!"
date: 2006-01-11
forum: Desktop Environments
---

### Post by myke on 2006-01-11
I easily installed Skype.  No problem there.  Skype.com even has a repository that you can add directly in to synaptic.  My prob is that it looks awful.  Clearly something is missing or not right in some way and I can't figure out what it is.  It loads terribly slow as well.  The skype gui itself is overly big and looks like it was coded on a commodore 64!     (I just dated myself)

Any suggestions as to anything that I might need to add to make it look graphically the way it's supposed to instead of like I'm running windoze 3.1???

---

### Post by myke on 2006-01-12
[I]Found some help in the wiki following these instructions:

Because Skype is a KDE application, Skype's typeface will appear very large on GNOME desktops. You can use either the kcontrol or the qt3-qtconfig package to configure the appearance of Skype and other KDE/QT applications. Of these two, the QT Configurator (qt3-qtconfig) has far fewer dependencies than kcontrol and may therefore be more convenient for people who mostly use non-KDE software. See also QtGnome for how to make Skype (and other Qt applications) look more like Gnome.

You can start QT Configurator with the "qtconfig" command. On the "Fonts" tab, choosing Font Family Sans Serif and Point Size 10 will give something that resembles Ubuntu's GNOME desktop. [/I]

Looks much better after using QT Configurator to adjust it a bit.  Still a little rough looking but not nearly as bad as before.  It's usable now so that's good.

---

