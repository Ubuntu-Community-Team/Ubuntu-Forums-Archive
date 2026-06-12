---
title: "Widget crashes Plasma after login"
date: 2013-09-20
forum: Desktop Environments
---

### Post by Stansilav_Radionov on 2013-09-20
Hello! I faced rather serious problem with KDE Plasma and desperately need help. The thing is I installed several widgets for Plasma, and one of them, namely "Remember the milk", behaved strangely and crashed taking the whole Plasma desktop with it. I rebooted, but saw an error message after login and found myself with no Plasma desktop but with other applications like Opera working. I opened a terminal and runned plasma-desktop. The output is following:

QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
QDBusObjectPath: invalid path ""
plasma-desktop(4019): ""geometry" - conversion of "58,2,0,25" to QRectF failed" 
plasma-desktop(4019): ""geometry" - conversion of "58,2,0,25" to QRectF failed" 
plasma-desktop(4019): ""geometry" - conversion of "58,2,0,25" to QRectF failed" 
plasma-desktop(4019): ""geometry" - conversion of "58,2,0,25" to QRectF failed" 
plasma-desktop(4019)/libplasma Plasma::isPluginVersionCompatible: unversioned plugin detected, may result in instability 
QGraphicsLinearLayout::insertItem: cannot insert null item
QGraphicsLinearLayout::insertItem: cannot insert null item
plasma-desktop(4019)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "" not found
invalid literal for int() with base 10: '' : Setting default geometry (600x300).
plasma-desktop(4019)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
QPainter::begin: Paint device returned engine == 0, type: 2
QPainter::setRenderHint: Painter must be active to set rendering hints
QPainter::setPen: Painter not active
QPainter::setFont: Painter not active
Request ready. Url is: "https://api.rememberthemilk.com/services/rest/?&api_key=631e881f0e5671d237c1a2a0a64d5b98&api_sig=72f3414004a1843860626f285fd7e44d&method=rtm.auth.getFrob" 
stanislav@debian:~$ KCrash: Attempting to start /usr/bin/plasma-desktop from kdeinit
sock_file=/home/stanislav/.kde/socket-debian/kdeinit4__0
KCrash: Application 'plasma-desktop' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/stanislav/.kde/socket-debian/kdeinit4__0
QSocketNotifier: Invalid socket 21 and type 'Read', disabling...

As far as I can see, the problem is indeed caused by Remember the milk widget. So could you please tell me how to completely remove it and fix this bug.

---

