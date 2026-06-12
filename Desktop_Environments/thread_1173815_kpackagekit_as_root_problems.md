---
title: "kpackagekit as root problems"
date: 2009-05-30
forum: Desktop Environments
---

### Post by mirons on 2009-05-30
Hi everybody. I have a strange issue with kpackagekit: when I strat it from the menu (lancelot) it doesn't start kdesudo, so I run it as a normal user. to install software so I went to a shell and typed in ```
kdesudo kpackagekit
```
In this case a blank window appears, showing just the buttons at the bottom, and I get this shell output:
```
KPackageKit(12504) kpackagekit::KPackageKit::newInstance: SHOW UI!
KPackageKit(12504) kpackagekit::KPackageKit::showUi: GO UI!
KPackageKit(12504) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kpk_addrm.desktop not found"
KPackageKit(12504) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath: kpk_settings.desktop not found"
```
just running it with sudo seems to work despite some other errors:
```
Error: "/var/tmp/kdecache-andrea" is owned by uid 1000 instead of uid 0.                                             
Error: "/tmp/kde-andrea" is owned by uid 1000 instead of uid 0.                                                      
KPackageKit(12642) kpackagekit::KPackageKit::newInstance: SHOW UI!                                                   
KPackageKit(12642) kpackagekit::KPackageKit::showUi: GO UI!                                                          
KPackageKit(12642) KpkAddRm::setCurrentAction:                                                                       
enumFromString ( Group ) : converted "unknown" to "Unknown" , enum value -1                                          
KPackageKit(12642) KpkTransactionBar::setBehaviors: Hide! 1 
```

Does anybody had this issue/ know how to run kpackagekit automatically from menu via kdesudo?

---

### Post by skullmunky on 2009-05-30
my suggestion - use synaptic.  wait a little while for kpackagekit's support for debian to mature.

---

### Post by krazyd on 2009-05-31
Don't run kpackagekit as root!
It will ask for your password when you need to actually install/remove packages!

---

