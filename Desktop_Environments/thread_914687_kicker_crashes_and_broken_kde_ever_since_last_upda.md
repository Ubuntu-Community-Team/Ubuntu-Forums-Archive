---
title: "kicker crashes and broken kde ever since last update"
date: 2008-09-09
forum: Desktop Environments
---

### Post by trawler on 2008-09-09
A few days ago I noticed there was a major upgrade to many kde packages and many more, and so I performed the upgrade using adept_updater, as I usually do. However, ever since the update, kicker crashes and some applications stopped working altogether.
I would like to mention, however, that I'm running kde with a separate X configuration. I.E. I have 2 separate desktops. The main one is connected to my PC and the secondary is connected to my TV. For whatever reason, kicker crashes on my main screen, but not on the TV desktop.
This is the crash handler's output:
```

[KCrash handler]
#6  0xb7298c8d in QTimer::stop () from /usr/lib/libqt-mt.so.3
#7  0xb6586acb in Panner::reallyUpdateScrollButtons ()
   from /usr/lib/libkickermain.so.1
#8  0xb6586d53 in Panner::setOrientation () from /usr/lib/libkickermain.so.1
#9  0xb60d5849 in TaskBar::setOrientation () from /usr/lib/libmtaskbar.so
#10 0xb60da8c3 in MTaskBarContainer::orientationChange ()
   from /usr/lib/libmtaskbar.so
#11 0xb60d979a in MTaskbarApplet::orientationChange ()
   from /usr/lib/libmtaskbar.so
#12 0xb6c9b266 in KPanelApplet::positionChange () from /usr/lib/libkdeui.so.4
#13 0xb6c4df89 in KPanelApplet::setPosition () from /usr/lib/libkdeui.so.4
#14 0xb667b1f6 in AppletContainer::setPopupDirection ()
   from /usr/lib/libkdeinit_kicker.so
#15 0xb6672f61 in BaseContainer::configure ()
   from /usr/lib/libkdeinit_kicker.so
#16 0xb6694605 in ContainerArea::addContainer ()
   from /usr/lib/libkdeinit_kicker.so
#17 0xb669aa3b in ContainerArea::loadContainers ()
   from /usr/lib/libkdeinit_kicker.so
#18 0xb669bc7f in ContainerArea::initialize ()
   from /usr/lib/libkdeinit_kicker.so
#19 0xb669bda4 in PanelExtension::populateContainerArea ()
   from /usr/lib/libkdeinit_kicker.so
#20 0xb668f838 in PanelExtension::qt_invoke ()
   from /usr/lib/libkdeinit_kicker.so
#21 0xb7271704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#22 0xb7600aba in QSignal::signal () from /usr/lib/libqt-mt.so.3
#23 0xb72907b2 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#24 0xb7298936 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#25 0xb7205c36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#26 0xb7207a5f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#27 0xb790b9b2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#28 0xb719628d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#29 0xb71f8b19 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#30 0xb71ab64b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#31 0xb7220f02 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb720784a in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#33 0xb7207875 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#34 0xb669cdd4 in ExtensionManager::initialize ()
   from /usr/lib/libkdeinit_kicker.so
#35 0xb669d724 in ExtensionManager::qt_invoke ()
   from /usr/lib/libkdeinit_kicker.so
#36 0xb7271704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#37 0xb7600aba in QSignal::signal () from /usr/lib/libqt-mt.so.3
#38 0xb72907b2 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#39 0xb7298936 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#40 0xb7205c36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb7207a5f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb790b9b2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb719628d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#44 0xb71f8b19 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#45 0xb71ab64b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#46 0xb7220f90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0xb7220c8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0xb72077df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0xb66971a7 in kdemain () from /usr/lib/libkdeinit_kicker.so
#50 0xb7f7d454 in kdeinitmain () from /usr/lib/kde3/kicker.so
#51 0x0804ee20 in ?? ()
#52 0x0804f541 in ?? ()
#53 0x0804fa7b in ?? ()
#54 0x0805057d in ?? ()
#55 0xb7cd7450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#56 0x0804bb91 in ?? ()

```

Also, weird thing is that cooldock is not able to launch any applications anymore. I tried launching applications from the kooldock *.desktop files folder and they work from there. I can't however launch the application from kooldock itself.

I would prefer to avoid reinstalling kde altogether... Hopefully someone might be able to make sense from the kicker's output above? :confused:

---

