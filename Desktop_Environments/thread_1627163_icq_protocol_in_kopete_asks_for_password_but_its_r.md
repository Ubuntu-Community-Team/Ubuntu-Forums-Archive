---
title: "icq protocol in kopete asks for password but its right"
date: 2010-11-21
forum: Desktop Environments
---

### Post by danisahne on 2010-11-21
Hello

ICQ in Kopete asks for a password but its right.

I tested it with icq2go.

Output :


Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kopete(2625)/kio (KDirWatch) KDirWatchPrivate::removeEntry: doesn't know "/home/daniel/.kde/share/apps/kabc" 
Calling appendChild() on a null node does nothing.
kopete(2625)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/kopete_history.so" does not offer a qt_plugin_instance function.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
kopete(2625)/libkopete Kopete::PluginManager::loadPluginInternal: Unable to find a plugin named ' "" '! 
Calling appendChild() on a null node does nothing.
daniel@ws:~$ QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/daniel/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

---

### Post by scinti on 2010-12-04
> **danisahne said:**
> Hello
ICQ in Kopete asks for a password but its right.
[...]


Same problem with kubuntu 10.04.1 LTS and kernel Linux 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

Someone have idea?

 Scinti

---

### Post by WebDrake on 2010-12-09
> **scinti said:**
> Same problem with kubuntu 10.04.1 LTS and kernel Linux 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

Someone have idea?

 Scinti

I think this is down to an ownership/server change for ICQ: [http://osdir.com/ml/kopete-bugs/2010-11/msg00113.html](http://osdir.com/ml/kopete-bugs/2010-11/msg00113.html)

Annoying that it's not yet fixed in Kopete itself; this change occurred on 16 November.

---

### Post by WebDrake on 2010-12-09
> **WebDrake said:**
> Annoying that it's not yet fixed in Kopete itself; this change occurred on 16 November.

Oddly, the Launchpad bug for this problem notes a fix being committed on 19 November, but this fix has still not been released:
[https://bugs.launchpad.net/ubuntu/maverick/+source/kdenetwork/+bug/676663](https://bugs.launchpad.net/ubuntu/maverick/+source/kdenetwork/+bug/676663)

---

