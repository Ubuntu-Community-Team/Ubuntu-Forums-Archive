---
title: "Superkaramba widgets not working in Lucid"
date: 2010-05-19
forum: Desktop Environments
---

### Post by davidmb on 2010-05-19
Hi,

I have recently installed Kubuntu Lucid and all seems to be fine except for not being able to add Superkaramba widgets to my plasma desktop.

To add support for Superkaramba widgets, I installed plasma-scriptengine-superkaramba.
Then, at the plasma desktop, installed the widget from a local SKZ file and once added to the desktop all that can be seen is the message "Could not create this object because: Could not find the package sk_28165-cm9 required by the graphic component CrystalMonitor 9" (in Spanish):
[CENTER][IMG]http://img35.imageshack.us/img35/9595/superkarambaerror.png[/IMG]
[LEFT]
I have tried other widgets downloaded from kde-look.org with the same luck.

Also tried:

[LIST]
[*]When run from the command line (plasmoidviewer "CrystalMonitor 9"), the result is the same and some log info is displayed:
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el fichero ó directorio
QFileSystemWatcher: failed to add paths: /home/david/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasmoidviewer(4209)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
plasmoidviewer(4209)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
plasmoidviewer(4209)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0)
[*]When run inside Superkaramba's desktop application, all widgets work fine, but they are not plasmoids and Superkaramba itself consumes quite a lot of CPU.
[/LIST]
What am I missing?
Can anyone provide any clues? Is this a bug?

Thanks!
[/LEFT]
[/CENTER]

---

### Post by davidmb on 2010-05-19
After digging a bit, I have managed to fix this issue (yes, I reckon this is a KDE bug).

So, first of all, it seems **only** SKZ (ZIP format) widgets are accepted by the Superkaramba plasma engine.
In addition, to see them on plasmoidviewer, their name must be prefixed with **sk_**. If unsure, you can list all installed plasmoids with:
```
plasmapkg -l
```

Anyway, the bug that prevents running these widgets on plasma is that the Superkaramba installer doesn't create the **metadata.desktop** file in the plasmoid's directory.
Luckily, the fix is easy because the very same file is created in a different location:
```
cp ~/.kde/share/kde4/services/plasma-applet-sk_*YOURWIDGET*.desktop ~/.kde/share/apps/plasma/plasmoids/sk_*YOURWIDGET*/metadata.desktop
```

---

### Post by Blue Rose on 2010-05-20
Thanks :D it worked for me :-)

---

### Post by mihas on 2010-06-08
Wow :) topic about my plasmoid. : proud :

Btw ... If anyone (still) interested I'm developing new version, fully customizable via web interface.

---

### Post by davidmb on 2010-06-08
Hey mihas, that's great!

I found your Crystal Monitor 9 widget cool, stylish and compact, even though I had to tweak it a bit... ;-)

[CENTER][IMG]http://img695.imageshack.us/img695/415/crystalmonitor.png[/IMG]
[/CENTER]
 
Anyway, thanks a lot and keep the good work! :-)

---

