---
title: "Kamerka does not have an icon on xubuntu 14.04, and cheese freeze the desctop"
date: 2014-05-13
forum: Desktop Environments
---

### Post by danbuz on 2014-05-13
I installed cheese and it freezes the entire desctop. When I open the app and use it, I'm not able to do anything on the desctop until I close it. So I installed kamerka and it does not appear on menu. When I do it via terminal it shows this:

[HTML]Kamerka version 0.8.1
    Copyright (C) 2011 Sebastian Krzyszkowiak
    Kamerka comes with ABSOLUTELY NO WARRANTY.
    This is free software, and you are welcome to redistribute it
    under certain conditions; type `./kamerka --license' for details.
Error: "/var/tmp/kdecache-***" is owned by uid 1000 instead of uid 0.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-***" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-***" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-***" is owned by uid 1000 instead of uid 0.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
static bool QDeclarativeMetaType::isModule(const QByteArray&, int, int) Qt 4.7 import detected; please note that Qt 4.7 is directly reusable as QtQuick 1.x with no code changes. Continuing, but startup time will be slower. 
kamerka(13091)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
kamerka(13091)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-***" is owned by uid 1000 instead of uid 0.
Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
kamerka(13091) videowidget::setPicture: Could not open .counter file! 
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

[/HTML]


Cheese dont put any message on terminal.

What might be the problem?

---

