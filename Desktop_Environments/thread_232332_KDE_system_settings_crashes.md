---
title: "KDE system settings crashes"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Orval on 2006-08-08
KDE system settings crashes when I select Apperance (?) to change the theme settings, icons etc.

Backtrace in the crash handler gives me this:

> (no debugging symbols found)
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
[Thread debugging using libthread_db enabled]
[New Thread -1232148800 (LWP 7867)]
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
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb69409a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb69422b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb6939f51 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0xb786f9fe in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#11 0xb786eff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#12 0xb786eff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#13 0xb786eff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#14 0xb78713f3 in KConfigDialogManager::init () from /usr/lib/libkdecore.so.4
#15 0xb7871500 in KConfigDialogManager::KConfigDialogManager ()
   from /usr/lib/libkdecore.so.4
#16 0xb7a80f57 in KCModule::addConfig () from /usr/lib/libkdeui.so.4
#17 0xb63e0b23 in kcmkbfx::kcmkbfx () from /usr/lib/kde3/kcm_kcmkbfx.so
#18 0xb63e13b0 in KGenericFactory<kcmkbfx, QWidget>::createObject ()
   from /usr/lib/kde3/kcm_kcmkbfx.so
#19 0xb7785b2f in KLibFactory::create () from /usr/lib/libkdecore.so.4
#20 0xb7f98e03 in KCModuleLoader::load () from /usr/lib/libkutils.so.1
#21 0xb7f996c5 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#22 0xb7f9faa3 in KCModuleProxy::realModule () from /usr/lib/libkutils.so.1
#23 0xb7fa0684 in KCModuleProxy::buttons () from /usr/lib/libkutils.so.1
#24 0x0805b874 in KLineEdit::setContextMenuEnabled ()
#25 0x0805e4b6 in QPtrDict<QStringList>::deleteItem ()
#26 0x0805f2ba in QPtrDict<QStringList>::deleteItem ()
#27 0xb710feb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0x0806026a in KAboutApplication::~KAboutApplication ()
#29 0x080602bf in KAboutApplication::~KAboutApplication ()
#30 0xb710fe8d in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#31 0xb74d7e0b in QIconView::clicked () from /usr/lib/libqt-mt.so.3
#32 0xb7306916 in QIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#33 0xb7a35828 in KIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#34 0xb7244499 in QScrollView::viewportMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#35 0xb724705c in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#36 0xb72fb2fc in QIconView::eventFilter () from /usr/lib/libqt-mt.so.3
#37 0xb710d002 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#38 0xb710d080 in QObject::event () from /usr/lib/libqt-mt.so.3
#39 0xb714a5aa in QWidget::event () from /usr/lib/libqt-mt.so.3
#40 0xb70a5e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb70a63e0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb783b7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb70371c5 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#44 0xb7032873 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#45 0xb7030d59 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#46 0xb704a4db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#47 0xb70be947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#48 0xb70be86a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#49 0xb70a4965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#50 0x0805db80 in QPtrDict<QStringList>::deleteItem ()
#51 0xb692cea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#52 0x080579e1 in ?? ()


Any clues?

---

### Post by Orval on 2006-08-09
Bumpetibump.

---

