---
title: "kaffeine"
date: 2005-04-30
forum: Desktop Environments
---

### Post by [pl]ice on 2005-04-30
hi,the kaffeine  continous crashes on me, eg. when i play one file, then i open another one and it crashes
kaffeine is 0.6
SIGSEGV 11


Any ideas? 

thanks


debug: 
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1230222912 (LWP 11383)]
[New Thread -1315050576 (LWP 11392)]
[New Thread -1306657872 (LWP 11391)]
[New Thread -1298064464 (LWP 11390)]
[New Thread -1287783504 (LWP 11389)]
[New Thread -1275290704 (LWP 11388)]
[New Thread -1266627664 (LWP 11387)]
[New Thread -1258198096 (LWP 11386)]
[New T(no debugging symbols found)
(no debugging symbols found)
.
.
.
(no debugging symbols found)
(no debugging symbols founhread -1245353040 (LWP 11385)]
(no debugging symbols found)
.
.
.
(no debugging symbols found)
[KCrash handler]
#7  0xb6de65ed in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#8  0xb6d60c51 in _XUnregisterFilter () from /usr/X11R6/lib/libX11.so.6
#9  0xb6d4ae45 in XrmEnumerateDatabase () from /usr/X11R6/lib/libX11.so.6
#10 0xb6d34ff9 in XKeysymToString () from /usr/X11R6/lib/libX11.so.6
#11 0xb77f8db9 in KKeyServer::Sym::toString () from /usr/lib/libkdecore.so.4
#12 0xb77f8f27 in KKeyServer::Sym::toStringInternal ()
   from /usr/lib/libkdecore.so.4
#13 0xb77f5bb8 in KKey::toStringInternal () from /usr/lib/libkdecore.so.4
#14 0xb77f67f9 in KKeySequence::toStringInternal ()
   from /usr/lib/libkdecore.so.4
#15 0xb77f7cec in KShortcut::toStringInternal () from /usr/lib/libkdecore.so.4
#16 0xb7a47087 in KAction::initPrivate () from /usr/lib/libkdeui.so.4
#17 0xb7a45dff in KAction::KAction () from /usr/lib/libkdeui.so.4
#18 0xb7a4c12a in KStdAction::create () from /usr/lib/libkdeui.so.4
#19 0xb7a4d036 in KStdAction::back () from /usr/lib/libkdeui.so.4
#20 0xb7e561ba in KDirOperator::setupActions () from /usr/lib/libkio.so.4
#21 0xb7e50fd6 in KDirOperator::KDirOperator () from /usr/lib/libkio.so.4
#22 0xb7e486d8 in KFileDialog::init () from /usr/lib/libkio.so.4
#23 0xb7e44329 in KFileDialog::KFileDialog () from /usr/lib/libkio.so.4
#24 0xb7e4b5cf in KFileDialog::getOpenFileNames () from /usr/lib/libkio.so.4
#25 0x080710bb in QGList::count ()
#26 0x08066af5 in QGList::count ()
#27 0xb71ce067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb71cdeae in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#29 0x0808e8ce in KComboBox::itemSelected ()
#30 0x080904e2 in KComboBox::itemSelected ()
#31 0x0808ea51 in KComboBox::itemSelected ()
#32 0xb71ce067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#33 0xb7af5587 in KIconView::executed () from /usr/lib/libkdeui.so.4
#34 0xb7af373a in KIconView::emitExecute () from /usr/lib/libkdeui.so.4
#35 0xb7af3943 in KIconView::slotMouseButtonClicked ()
   from /usr/lib/libkdeui.so.4
#36 0xb7af58b8 in KIconView::qt_invoke () from /usr/lib/libkdeui.so.4
#37 0xb71ce067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#38 0xb7512863 in QIconView::mouseButtonClicked () from /usr/lib/libqt-mt.so.3
#39 0xb73834d6 in QIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#40 0xb7af3976 in KIconView::contentsMouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#41 0xb72d80fc in QScrollView::viewportMouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#42 0xb72d7a10 in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#43 0xb7387e4b in QIconView::eventFilter () from /usr/lib/libqt-mt.so.3
#44 0xb71cbb01 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#45 0xb71cba5d in QObject::event () from /usr/lib/libqt-mt.so.3
#46 0xb720176f in QWidget::event () from /usr/lib/libqt-mt.so.3
#47 0xb7176370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#48 0xb7175ac7 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#49 0xb777e960 in KApplication::notify () from /usr/lib/libkdecore.so.4
#50 0xb710f12f in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#51 0xb710ce1c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#52 0xb7122ec2 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#53 0xb718774c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#54 0xb718760e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#55 0xb717657b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#56 0x08066803 in ?? ()
#57 0xbffff960 in ?? ()
#58 0x00000000 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x00000001 in ?? ()
#63 0x080e7c9c in _IO_stdin_used ()
#64 0x00000000 in ?? ()
#65 0x080e7f60 in _IO_stdin_used ()
#66 0x080e7ec0 in _IO_stdin_used ()
#67 0xbffff988 in ?? ()
#68 0xb6cd22ee in operator new () from /usr/lib/libstdc++.so.5
#69 0xb6afb8c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#70 0x08066571 in ?? ()

---

### Post by ceti on 2005-04-30
ok, follow this thread to download a replacement for your buggy Kaffeine:D

[http://www.ubuntuforums.org/showthread.php?t=27670](http://www.ubuntuforums.org/showthread.php?t=27670)

cheers
ceti

---

