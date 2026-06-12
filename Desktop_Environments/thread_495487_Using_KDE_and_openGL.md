---
title: "Using KDE and openGL"
date: 2007-07-08
forum: Desktop Environments
---

### Post by RecyclerMan on 2007-07-08
Haven't really looked in to it yet, I am Having a problem with KDE ( Kubuntu 7.04, Feisty Fawn). Most things seem to work out of the box. Now I have installed the leagicy driver for the nvidia TNTII cards mine is a RIVA 128 TNTII  I have used the tools provided to use the driver nvida in the xorg.conf. and I have good controll of the 2D stuff but when I try to use openGL things crash. When I go to the KinfoCenter and click on the OpenGl I get the error mesage "Could not initialise OpenGL"

Then I get the KDE Crash Handler here is the output from the Back Trace 

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1239336736 (LWP 6684)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb5b9194f in ?? () from /usr/lib/libGL.so.1
#7  0x083e6eb8 in ?? ()
#8  0xb5bc7660 in ?? () from /usr/lib/libGL.so.1
#9  0x083e6eb8 in ?? ()
#10 0xb5b901a6 in ?? () from /usr/lib/libGL.so.1
#11 0x083e6eb8 in ?? ()
#12 0x083e6eb8 in ?? ()
#13 0xb649cb2c in ?? () from /usr/lib/libX11.so.6
#14 0x083e5438 in ?? ()
#15 0xb63c7ebd in XCloseDisplay () from /usr/lib/libX11.so.6
#16 0xb5c81e5b in GetInfo_OpenGL () from /usr/lib/kde3/kcm_info.so
#17 0xb5c72e6a in KInfoListWidget::load () from /usr/lib/kde3/kcm_info.so
#18 0xb5c7a074 in KInfoListWidget::KInfoListWidget ()
   from /usr/lib/kde3/kcm_info.so
#19 0xb5c83c57 in create_opengl () from /usr/lib/kde3/kcm_info.so
#20 0xb796f1a1 in KCModuleLoader::load () from /usr/lib/libkutils.so.1
#21 0xb796fd97 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#22 0xb79727b2 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#23 0xb7f05734 in ConfigModule::module () from /usr/lib/libkdeinit_kcontrol.so
#24 0xb7f05b46 in ModuleWidget::load () from /usr/lib/libkdeinit_kcontrol.so
#25 0xb7f05c04 in DockContainer::loadModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#26 0xb7f05ea8 in DockContainer::dockModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#27 0xb7f0a25e in TopLevel::activateModule ()
   from /usr/lib/libkdeinit_kcontrol.so
#28 0xb7f0e565 in TopLevel::qt_invoke () from /usr/lib/libkdeinit_kcontrol.so
#29 0xb67f888b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#30 0xb7efcf2e in IndexWidget::moduleActivated ()
   from /usr/lib/libkdeinit_kcontrol.so
#31 0xb7f0a551 in IndexWidget::moduleSelected ()
   from /usr/lib/libkdeinit_kcontrol.so
#32 0xb7f0abbe in IndexWidget::qt_invoke ()
   from /usr/lib/libkdeinit_kcontrol.so
#33 0xb67f888b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#34 0xb7efca01 in ModuleIconView::moduleSelected ()
   from /usr/lib/libkdeinit_kcontrol.so
#35 0xb7f09f8c in ModuleIconView::slotItemSelected ()
   from /usr/lib/libkdeinit_kcontrol.so
#36 0xb7f0a0cc in ModuleIconView::qt_invoke ()
   from /usr/lib/libkdeinit_kcontrol.so
#37 0xb67f888b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#38 0xb6b9c8e7 in QListView::clicked () from /usr/lib/libqt-mt.so.3
#39 0xb68f5b85 in QListView::contentsMouseReleaseEventEx ()
   from /usr/lib/libqt-mt.so.3
#40 0xb68f5e60 in QListView::contentsMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#41 0xb7ad9023 in KListView::contentsMouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#42 0xb692df17 in QScrollView::viewportMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0xb692f4ae in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#44 0xb68f775e in QListView::eventFilter () from /usr/lib/libqt-mt.so.3
#45 0xb67f7e38 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#46 0xb67f7eb6 in QObject::event () from /usr/lib/libqt-mt.so.3
#47 0xb682f58f in QWidget::event () from /usr/lib/libqt-mt.so.3
#48 0xb678fa60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#49 0xb6791c1e in QApplication::notify () from /usr/lib/libqt-mt.so.3
#50 0xb74c3ce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#51 0xb672225d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#52 0xb6720ec2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#53 0xb671efac in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#54 0xb6736180 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#55 0xb67aa136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#56 0xb67a9f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#57 0xb6791609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#58 0xb7f0fd0c in kdemain () from /usr/lib/libkdeinit_kcontrol.so
#59 0x080484c2 in ?? ()
#60 0x00000007 in ?? ()
#61 0xbf9def54 in ?? ()
#62 0xbf9deeb8 in ?? ()
#63 0xb7db6ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#64 0xb7f3b7b0 in ?? () from /lib/ld-linux.so.2
#65 0xbf9deed0 in ?? ()
#66 0xbf9def28 in ?? ()
#67 0xb7c8febc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: frame did not save the PC


The Question is a easy problem as I have been using OpenGL on this same hardware using SlackWare and Gentoo the rest of the hard ware is An Athlon 900 (clocked to 990Mhz) on an Irongate chipsetted. motherbord

---

