---
title: "plasma-desktop crashing"
date: 2011-04-10
forum: Desktop Environments
---

### Post by EngMAF on 2011-04-10
this morning new updates available
i've installed the updates
when i restart the labtop
plasma-desktop crashed it give that error when i start it from the konsole
```

maf@maf-Lenovo-G560:~$ plasma-desktop 
QDBusObjectPath: invalid path ""
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::AppletPrivate::mainConfigGroup: requesting config for "Qalculate!" without a containment! 
I/O warning : failed to load external entity "/home/maf/.qalculate/eurofxref-daily.xml"
I/O warning : failed to load external entity "/home/maf/.qalculate/eurofxref-daily.xml"
plasma-desktop(3545)/libplasma Plasma::Applet::itemChange: Configuration object was requested prior to init(), which is too early. Please fix this item: QGraphicsItem(0) DefaultDesktop (this = 0x879d360 , parent = 0x0 , pos = QPointF(0, 0) , z = 0 , flags =  ( ItemIsFocusable | ItemUsesExtendedStyleOption | ItemSendsGeometryChanges ) ) "Qalculate!" 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGridLayoutEngine::addItem: Cell (1, 1) already taken
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/maf/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Object::connect: No such signal QDBusAbstractInterface::Changed()
plasma-desktop(3545)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3545)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3545) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(3545) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
KCrash: Attempting to start /usr/bin/plasma-desktop from kdeinit
sock_file=/home/maf/.kde/socket-maf-Lenovo-G560/kdeinit4__0
KCrash: Application 'plasma-desktop' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/maf/.kde/socket-maf-Lenovo-G560/kdeinit4__0
QSocketNotifier: Invalid socket 30 and type 'Read', disabling...
QSocketNotifier: Invalid socket 25 and type 'Read', disabling...
plasma-desktop(3544): Communication problem with  "plasma-desktop" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasma-desktop was not provided by any .service files" " 

maf@maf-Lenovo-G560:~$ sudo apt-get remove plasma-d
plasma-dataengines-addons     plasma-dataengines-workspace  plasma-desktop                
maf@maf-Lenovo-G560:~$ sudo apt-get remove plasma-desktop 
[sudo] password for maf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-notify python-gconf openoffice.org-l10n-common libtextcat-data-utf8 firefox-4.0-globalmenu recordmydesktop
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kubuntu-desktop plasma-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 2,408kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 265881 files and directories currently installed.)
Removing kubuntu-desktop ...
Removing plasma-desktop ...
maf@maf-Lenovo-G560:~$ sudo apt-get install plasma-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-notify python-gconf openoffice.org-l10n-common libtextcat-data-utf8 firefox-4.0-globalmenu recordmydesktop
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  plasma-desktop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 569kB of archives.
After this operation, 2,351kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ maverick/main plasma-desktop i386 4:4.6.2a-0ubuntu1~maverick1~ppa3 [569kB]
Fetched 569kB in 11s (51.6kB/s)                                                                                                            
Selecting previously deselected package plasma-desktop.
(Reading database ... 265812 files and directories currently installed.)
Unpacking plasma-desktop (from .../plasma-desktop_4%3a4.6.2a-0ubuntu1~maverick1~ppa3_i386.deb) ...
Setting up plasma-desktop (4:4.6.2a-0ubuntu1~maverick1~ppa3) ...
maf@maf-Lenovo-G560:~$ plasma-desktop 
QDBusObjectPath: invalid path ""
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::AppletPrivate::mainConfigGroup: requesting config for "Qalculate!" without a containment! 
I/O warning : failed to load external entity "/home/maf/.qalculate/eurofxref-daily.xml"
I/O warning : failed to load external entity "/home/maf/.qalculate/eurofxref-daily.xml"
plasma-desktop(3738)/libplasma Plasma::Applet::itemChange: Configuration object was requested prior to init(), which is too early. Please fix this item: QGraphicsItem(0) DefaultDesktop (this = 0x8ce46b0 , parent = 0x0 , pos = QPointF(0, 0) , z = 0 , flags =  ( ItemIsFocusable | ItemUsesExtendedStyleOption | ItemSendsGeometryChanges ) ) "Qalculate!" 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QGridLayoutEngine::addItem: Cell (1, 1) already taken
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(127, 0) 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/maf/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
link XMLID_34_ hasn't been detected!
link XMLID_34_ hasn't been detected!
link XMLID_36_ hasn't been detected!
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
Object::connect: No such signal QDBusAbstractInterface::Changed()
plasma-desktop(3738)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
plasma-desktop(3738)/libplasma Plasma::FrameSvg::resizeFrame: Invalid size QSizeF(0, 0) 
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
plasma-desktop(3738) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
plasma-desktop(3738) MessageIndicator::adjustViewSize: No parentWidget for applet widget()! 
KCrash: Attempting to start /usr/bin/plasma-desktop from kdeinit
sock_file=/home/maf/.kde/socket-maf-Lenovo-G560/kdeinit4__0
plasma-desktop(3737): Communication problem with  "plasma-desktop" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasma-desktop was not provided by any .service files" " 

maf@maf-Lenovo-G560:~$ KCrash: Application 'plasma-desktop' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/maf/.kde/socket-maf-Lenovo-G560/kdeinit4__0
QSocketNotifier: Invalid socket 21 and type 'Read', disabling...
QSocketNotifier: Invalid socket 30 and type 'Read', disabling...




```

---

