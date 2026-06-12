---
title: "KDE after an update no long has windows decorations on secondary monitors (13.04)"
date: 2013-08-21
forum: Desktop Environments
---

### Post by egandt on 2013-08-21
I've been running 13.04 for almost 4 months now without issue using KDE, then I installed the lastest updates yesterday including a good number for KDE, now will KDE works on my primary monitor, all secondary monitors (so monitors 2 and 3 in my case) do not work properly.  The Pager and TaskManager are not visiable on the panel, although KDE says they are present.  Any windows opened on the secondary monitors do not contain any windows decorations, AKA controls.  This means they are always in teh upper left corner and can not be resized/closed ....
Basically after the update my KDE install is unusable.  I also tried a new user which has never before logged in with the same results, thus it appears directly related to something updated when I installed updates yesterday, the problem is what and how do I backout the updates (when I can not even determine what they were) as reinstalling to get a frsh install while doable takes hours (which I do not have) and then I would encounter the same issues since the updates would be installed.

Thanks,
ERIC

---

### Post by bra|10n on 2013-08-21
You might run the following command in a konsole and watch for any error output;
```
kbuildsycoca4 && kquitapp plasma-desktop && kstart plasma-desktop
```

---

### Post by QIII on 2013-08-21
I believe I got kernel updates yesterday.  All three of my monitors are working because I watch for kernel updates and take an extra step or two before letting them be installed.

Do you have a proprietary video driver installed from a source other than the repos?

---

### Post by egandt on 2013-08-22
I'm still on amd-driver-installer-catalyst-13-6-beta-x86.x86_64 as I had issues with Video when I first installed.
   I see that 13-8 beta is out, I'll give that a try.

As for the suggested commands, I see these 3 errors, about bad windows:
$ kbuildsycoca4 && kquitapp plasma-desktop && kstart plasma-desktop
kbuildsycoca4 running...
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "Tests.ods.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "Tests.ods.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "stacktrace.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "stacktrace.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "Server_listing.txt.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "Server_listing.txt.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "SimpleServletScaling_Cores.ods.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "XEF_Cores.ods.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "perf stats.ods.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "XEE.ods.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "Exalogic.txt.desktop"  has Type= "Link"  instead of "Application" or "Service" 

kbuildsycoca4(11626) KBuildServiceFactory::createEntry: Invalid Service :  "XED.txt.desktop" 
kbuildsycoca4(11626)/kdecore (services) KServicePrivate::init: The desktop entry file  "Guesstimator.xlsm.desktop"  has Type= "Link"  instead of "Application" or "Service" 
plasma-desktop(11640)/libplasma Plasma::isPluginVersionCompatible: unversioned plugin detected, may result in instability 
QGraphicsLinearLayout::insertItem: cannot insert null item
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QGraphicsLinearLayout::removeAt: invalid index 0
========================>  3 0
static bool QDeclarativeMetaType::isModule(const QByteArray&, int, int) Qt 4.7 import detected; please note that Qt 4.7 is directly reusable as QtQuick 1.x with no code changes. Continuing, but startup time will be slower. 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0GHTSH" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__SD_2fMMC_058F63626476" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__Compact_Flash_058F63626476" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__SM_2fxD_Picture_058F63626476" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/SAMSUNG_SSD_830_Series_S0Z3NEAC828850" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0HVZHH" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__MS_2fMS_Pro_058F63626476" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/hp______BD__B__DH8E2L_306018905184" : property "Drive" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0HVZHH" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0HVZHH" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0HVZHH" : property "Table" does not exist 
"/org/freedesktop/UDisks2/drives/SAMSUNG_SSD_830_Series_S0Z3NEAC828850" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/SAMSUNG_SSD_830_Series_S0Z3NEAC828850" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/SAMSUNG_SSD_830_Series_S0Z3NEAC828850" : property "Table" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0GHTSH" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0GHTSH" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/Hitachi_HDS721050CLA362_JPB570HC0GHTSH" : property "Table" does not exist 
file:///usr/lib/kde4/imports/org/kde/plasma/components/SectionScroller.qml:103: TypeError: Result of expression 'listView' [null] is not an object.
file:///usr/lib/kde4/imports/org/kde/plasma/components/SectionScroller.qml:175: ReferenceError: Can't find variable: sectionsRepeater
file:///usr/lib/kde4/imports/org/kde/plasma/components/SectionScroller.qml:103: Error: Cannot assign [undefined] to QString
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
file:///usr/share/kde4/apps/plasma/plasmoids/notifier/contents/ui/devicenotifier.qml:224:13: QML QDeclarativeListView_QML_62: Possible anchor loop detected on fill.
"/org/freedesktop/UDisks2/drives/Generic__MS_2fMS_Pro_058F63626476" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__MS_2fMS_Pro_058F63626476" : property "Device" does not exist 
QGridLayoutEngine::addItem: Cell (0, 1) already taken
QGridLayoutEngine::addItem: Cell (0, 1) already taken
QGridLayoutEngine::addItem: Cell (0, 1) already taken
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
"/org/freedesktop/UDisks2/drives/Generic__SD_2fMMC_058F63626476" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__SD_2fMMC_058F63626476" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/hp______BD__B__DH8E2L_306018905184" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/hp______BD__B__DH8E2L_306018905184" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__SM_2fxD_Picture_058F63626476" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__SM_2fxD_Picture_058F63626476" : property "Device" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__Compact_Flash_058F63626476" : property "DeviceNumber" does not exist 
"/org/freedesktop/UDisks2/drives/Generic__Compact_Flash_058F63626476" : property "Device" does not exist 
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasmapackage:/ui/NotificationDelegate/NotificationDelegate.qml:208:21: QML TextEdit: Possible anchor loop detected on fill.
plasmapackage:/ui/NotificationDelegate/NotificationDelegate.qml:162:13: QML Item: Binding loop detected for property "height"
plasmapackage:/ui/NotificationDelegate/NotificationDelegate.qml:162:13: QML Item: Binding loop detected for property "height"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/share/kde4/apps/plasma/plasmoids/org.kde.notifications/contents/ui/Notifications.qml:213:17: QML TabButton: Binding loop detected for property "implicitHeight"
file:///usr/share/kde4/apps/plasma/plasmoids/org.kde.notifications/contents/ui/Notifications.qml:213:17: QML TabButton: Binding loop detected for property "implicitHeight"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabButton.qml:111:5: QML QObject_QML_127: Binding loop detected for property "portrait"
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabBar.qml:150:5: QML Item: Possible anchor loop detected on fill.
file:///usr/lib/kde4/imports/org/kde/plasma/components/TabBar.qml:150:5: QML Item: Possible anchor loop detected on fill.
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(11640)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 


There are 3 errors related to bad windows and a null insert, but otherwise everything looks ok to me, however I posted the results in case I'm missing something.

Thanks,
ERIC

---

### Post by Erik1984 on 2013-08-22
That particular output doesn't mean much to me (hopfully it does to people with more KDE and/or Linux usage) but I did see some kernel updates AND an update for 'kscreen' passing by. For the kernel you could try to select an older kernel from GRUB when booting (under Advanced options for *buntu in the GRUB menu).

---

### Post by bra|10n on 2013-08-23
You could also rename your .kde4 folder to .kde4-old for example and see if this is solves the problem. Restarting your machine will generate a new .kde4 folder automatically for you.

---

