---
title: "KDE ... blew up or something?"
date: 2010-03-20
forum: Desktop Environments
---

### Post by Hawk__0 on 2010-03-20
This is my first time giving KDE and honest shot.  I'm usually a gnome user, but anyways here is my problem I can't figure out:

Firstly, running 9.10 kubuntu.

I rebooted my computer, and plasma-desktop has died or something.  the command is no longer found... and this makes no sense:
```
steve@steve-kubuntu:~$ plasmma-desktop
No command 'plasmma-desktop' found, did you mean:
 Command 'plasma-desktop' from package 'kdebase-workspace-bin' (main)
plasmma-desktop: command not found
steve@steve-kubuntu:~$ sudo apt-get install kdebase-workspace-bin
[sudo] password for steve:
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdebase-workspace-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.

```

So I guessed maybe plasma-overlay is the plasma stuff so I tried this:
```
steve@steve-kubuntu:~$ plasma-overlay 
<unknown program name>(2096)/ checkComposite: Plasma has an argb visual 0x9927aa0 44040193                                                                      
<unknown program name>(2096)/ checkComposite: Plasma can use COMPOSITE for effects on 0x991cb90                                                                 
plasma-overlay(2097)/plasma PlasmaApp::PlasmaApp: Setting the pixmap cache size to 20617 kilobytes                                                              
plasma-overlay(2097)/plasma SaverCorona::init: unlock action                    
plasma-overlay(2097)/plasma SaverCorona::loadDefaultLayout:
plasma-overlay(2097)/plasma SaverCorona::loadDefaultLayout:      screen geometry is QRect(0,0 1440x900)
plasma-overlay(2097)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-steve/ksycoca4"
plasma-overlay(2097)/plasma PlasmaApp::createView: Containment name: "SaverDesktop Activity" | type 127 | screen: -1 | geometry: QRectF(0,0 200x200) | zValue: 0
plasma-overlay(2097)/plasma PlasmaApp::createView: creating a view for -1 and we have 1 screens
plasma-overlay(2097)/plasma PlasmaApp::createView: view created
plasma-overlay(2097)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::instance: instance(): ... initialised
plasma-overlay(2097)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readConfig: readConfig(): local zone= "America/Vancouver"
plasma-overlay(2097)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readZoneTab: readZoneTab( "/usr/share/zoneinfo/zone.tab" )
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "holidaysRegions"
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "holidaysRegions"
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "holidaysRegions"
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "holidaysRegions"
plasma-overlay(2097)/plasma PlasmaApp::createView: Containment name: "SaverDesktop Activity" | type 127 | screen: 0 | geometry: QRectF(0,0 1440x900) | zValue: 0
plasma-overlay(2097)/plasma PlasmaApp::setup: false
plasma-overlay(2097)/plasma PlasmaApp::setup: checking lockprocess is still around
plasma-overlay(2097)/plasma PlasmaApp::setup: bailing out
plasma-overlay(2097)/libplasma Plasma::ViewPrivate::updateSceneRect: !!!!!!!!!!!!!!!!! setting the scene rect to QRectF(0,0 1440x900) associated screen is 0
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "isHoliday::2010-03-20"
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "isHoliday"
plasma-overlay(2097)/plasma CalendarEngine::sourceRequestEvent: "2010-03-20"
steve@steve-kubuntu:~$

```

Basically when KDE logs in I can access krunner to launch apps and stuff but I get no background/kde menu

---

### Post by Hawk__0 on 2010-03-20
Fixed after installing plasma-workspace

---

