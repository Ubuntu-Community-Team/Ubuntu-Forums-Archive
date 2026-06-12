---
title: "Krita without window decoration"
date: 2012-11-03
forum: Desktop Environments
---

### Post by pasdeloup on 2012-11-03
After installing Krita (Qt application) I observed the window decoration is completely missing. I am unable to move or resize the window (except switching to fullscreen and back).

Searching for information I found several issues related to Compiz. But Compiz is not installed on my system.

I would highly appreciate any help. Thank you !

---

### Post by pasdeloup on 2012-11-04
This is the terminal messages:

Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(2325) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(2325) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(2325) kdemain: Emitting notifyDatabaseChanged ()
krita(2314)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (8-bit integer/channel)" , since there are no profiles available 
krita(2314)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (16-bit integer/channel)" , since there are no profiles available 
krita(2314)/koffice (lib pigment) KoColorConversionSystem::insertColorSpace: Cannot add node for  "YCBCR (32-bit float/channel)" , since there are no profiles available 
krita(2314)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/kritahistorydocker.so" does not offer a qt_plugin_instance function.
krita(2314)/koffice (lib kopageapp) KoOdfLoadingContext::KoOdfLoadingContext: could not parse manifest document

---

### Post by pasdeloup on 2012-11-04
Man, this was a really stupid problem ! This would have never come to my mind :confused:

I found the answer in this KDE forum thread:
[http://forum.kde.org/viewtopic.php?f=203&t=106994&p=246656&hilit=lxde#p246656](http://forum.kde.org/viewtopic.php?f=203&t=106994&p=246656&hilit=lxde#p246656)

The Krita window position was just too high, the window decoration was outside the screen. 

Launching Krita with the following option solved the problem:

krita --geometry 100x100+0+0

---

