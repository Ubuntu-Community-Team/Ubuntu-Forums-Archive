---
title: "CRASH:  System Settings -&gt; Appearance"
date: 2006-08-08
forum: Desktop Environments
---

### Post by rosh1182 on 2006-08-08
This is under kubuntu (kubuntu-desktop 0.86), KDE 3.5.4.  Here is the KDE Crash Handler output:

```

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
[Thread debugging using libthread_db enabled]
[New Thread -1232558400 (LWP 6408)]
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
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb68dc9a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb68de2b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb68d5f51 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0xb780a9fe in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#11 0xb7809ff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#12 0xb7809ff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#13 0xb7809ff1 in KConfigDialogManager::parseChildren ()
   from /usr/lib/libkdecore.so.4
#14 0xb780c3f3 in KConfigDialogManager::init () from /usr/lib/libkdecore.so.4
#15 0xb780c500 in KConfigDialogManager::KConfigDialogManager ()
   from /usr/lib/libkdecore.so.4
#16 0xb7a1cf57 in KCModule::addConfig () from /usr/lib/libkdeui.so.4
#17 0xb624cb23 in kcmkbfx::kcmkbfx () from /usr/lib/kde3/kcm_kcmkbfx.so
#18 0xb624d3b0 in KGenericFactory<kcmkbfx, QWidget>::createObject ()
   from /usr/lib/kde3/kcm_kcmkbfx.so
#19 0xb7720b2f in KLibFactory::create () from /usr/lib/libkdecore.so.4
#20 0xb7f33e03 in KCModuleLoader::load () from /usr/lib/libkutils.so.1
#21 0xb7f346c5 in KCModuleLoader::loadModule () from /usr/lib/libkutils.so.1
#22 0xb7f3aaa3 in KCModuleProxy::realModule () from /usr/lib/libkutils.so.1
#23 0xb7f3b684 in KCModuleProxy::buttons () from /usr/lib/libkutils.so.1
#24 0x0805b874 in KLineEdit::setContextMenuEnabled ()
#25 0x0805e4b6 in QPtrDict<QStringList>::deleteItem ()
#26 0x0805f2ba in QPtrDict<QStringList>::deleteItem ()
#27 0xb70aaeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0x0806026a in KAboutApplication::~KAboutApplication ()
#29 0x080602bf in KAboutApplication::~KAboutApplication ()
#30 0xb70aae8d in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#31 0xb7472e0b in QIconView::clicked () from /usr/lib/libqt-mt.so.3
#32 0xb72a1916 in QIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#33 0xb79d1828 in KIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#34 0xb71df499 in QScrollView::viewportMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#35 0xb71e205c in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#36 0xb72962fc in QIconView::eventFilter () from /usr/lib/libqt-mt.so.3
#37 0xb70a8002 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#38 0xb70a8080 in QObject::event () from /usr/lib/libqt-mt.so.3
#39 0xb70e55aa in QWidget::event () from /usr/lib/libqt-mt.so.3
#40 0xb7040e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb70413e0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb77d67ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb6fd21c5 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#44 0xb6fcd873 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#45 0xb6fcbd59 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#46 0xb6fe54db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#47 0xb7059947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#48 0xb705986a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#49 0xb703f965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#50 0x0805db80 in QPtrDict<QStringList>::deleteItem ()
#51 0xb68c8ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#52 0x080579e1 in ?? ()


```

---

### Post by rosh1182 on 2006-08-08
I am also getting crashes when I try to use the Keyboard Shortcuts application.

Here is the trace:
```

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
[Thread debugging using libthread_db enabled]
[New Thread -1232763200 (LWP 6637)]
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
#7  0xb68aa9a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb68ac2b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb68a3f51 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0xb61e6455 in KHotKeys::init_global_data ()
   from /usr/lib/libkhotkeys_shared.so.1
#11 0xb6259c59 in KHotKeys::khotkeys_init ()
   from /usr/lib/kde3/kcm_khotkeys.so
#12 0xb6259ca1 in khotkeys_init () from /usr/lib/kde3/kcm_khotkeys.so
#13 0xb5a8df52 in KHotKeys::init () from /usr/lib/kde3/kcm_keys.so
#14 0xb5a8e004 in KHotKeys::getMenuEntryShortcut ()
   from /usr/lib/kde3/kcm_keys.so
#15 0xb5a9ca24 in AppTreeView::fillBranch () from /usr/lib/kde3/kcm_keys.so
#16 0xb5a9cc4f in AppTreeView::fill () from /usr/lib/kde3/kcm_keys.so
#17 0xb5a9cc94 in CommandShortcutsModule::showing ()
   from /usr/lib/kde3/kcm_keys.so
#18 0xb5aab55e in CommandShortcutsModule::qt_invoke ()
   from /usr/lib/kde3/kcm_keys.so
#19 0xb7078eb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb742e28c in QTabWidget::currentChanged () from /usr/lib/libqt-mt.so.3
#21 0xb71c8d0f in QTabWidget::showTab () from /usr/lib/libqt-mt.so.3
#22 0xb742e42a in QTabWidget::qt_invoke () from /usr/lib/libqt-mt.so.3
#23 0xb7078eb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#24 0xb70797c8 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#25 0xb742da59 in QTabBar::selected () from /usr/lib/libqt-mt.so.3
#26 0xb71c5fed in QTabBar::setCurrentTab () from /usr/lib/libqt-mt.so.3
#27 0xb71c2f22 in QTabBar::mousePressEvent () from /usr/lib/libqt-mt.so.3
#28 0xb70b364e in QWidget::event () from /usr/lib/libqt-mt.so.3
#29 0xb71c516f in QTabBar::event () from /usr/lib/libqt-mt.so.3
#30 0xb700ee56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb700f3e0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb77a47ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb6fa01c5 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#34 0xb6f9b873 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#35 0xb6f99d59 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#36 0xb6fb34db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#37 0xb7027947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#38 0xb702786a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#39 0xb700d965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#40 0x0805db80 in QPtrDict<QStringList>::deleteItem ()
#41 0xb6896ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#42 0x080579e1 in ?? ()


```

---

### Post by Orval on 2006-08-09
Ah, I have exactly the same problem: [see this thread]("http://ubuntuforums.org/showthread.php?t=232332"). But no resultion yet. :( 

Are you using KDE 3.5.4 too?

---

### Post by rosh1182 on 2006-08-09
Yes, I am also using KDE 3.5.4.

---

### Post by Chareos on 2006-08-20
Same problem using Keyboard Shortcuts application.

I've also lost my hotkeys !
[http://www.ubuntuforums.org/showthread.php?p=1400039#post1400039](http://www.ubuntuforums.org/showthread.php?p=1400039#post1400039)

---

