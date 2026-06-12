---
title: "Plasma-desktop freezes"
date: 2011-08-28
forum: Desktop Environments
---

### Post by Nemeczek on 2011-08-28
Kubuntu 11.04 on MSI fx620dx, kernel 3.0.3 (installed few days ago)
+ bumblebee. After install system works fine a few days but now after loging plasma is freezes. Plasma is loading long time and i can't use any elemt of desktop. Like a screenshot. But works fine. And top shows me:
Plasma-desktop is using 100% CPU. And if I star plasma by Konsole:

```

 
radush@radush-laptop:/media/46BBD8FC46523DAD/Dokumenty$ plasma-desktop
QDBusObjectPath: invalid path ""
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Nie ma takiego pliku ani katalogu
QFileSystemWatcher: failed to add paths: /home/radush/.config/ibus/bus
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QGridLayoutEngine::addItem: Cell (1, 1) already taken
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
Object::connect: No such signal QDBusAbstractInterface::Changed()
Warning: QGraphicsLinearLayout::insertItem: cannot insert null item
Warning: QGraphicsLinearLayout::insertItem: cannot insert null item
Warning: Object::connect: No such slot AbstractItemView::iconSettingsChanged(int)
radush@radush-laptop:/media/46BBD8FC46523DAD/Dokumenty$ Warning: QPainter::begin: Paint device returned engine == 0, type: 2
Warning: QPainter::setCompositionMode: Painter not active
Warning: QPainter::end: Painter not active, aborted
Warning: QPainter::begin: Paint device returned engine == 0, type: 2
Warning: QPainter::setCompositionMode: Painter not active
Warning: QPainter::end: Painter not active, aborted

``` 

Any help?

---

### Post by schnelle on 2011-08-29
Hm... you can try with renaming ~/.kde directory and then restart system. After reboot kde will be back to its default settings (brand new .kde folder will be made).

---

