---
title: "krunner breaking"
date: 2010-06-14
forum: Desktop Environments
---

### Post by dabrowsa on 2010-06-14
Can anyone explain why krunner keeps breaking?  Sometimes it runs, sometimes it doesn't.  Here's the error message.


```
dabrowsa$ krunner
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/dabrowsa/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
krunner(18978)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/dabrowsa/.kde/share/apps/kabc" 
krunner(18978)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
```

---

### Post by Raffles10 on 2010-06-14
Krunner crashes are usually related to plugins, try disabling the ones you don't need or disable one by one to try and diagnose the troublesome plugin.

---

### Post by dabrowsa on 2010-06-14
> **Raffles10 said:**
> Krunner crashes are usually related to plugins, try disabling the ones you don't need or disable one by one to try and diagnose the troublesome plugin.

Plugins?  What plugins?  Krunner plugins?  How do I disable them?

---

