---
title: "K3B in GNOME dies"
date: 2005-11-06
forum: Desktop Environments
---

### Post by BorgHunter on 2005-11-06
Right, so I upgraded to Breezy a couple weeks ago. Everything works beautifully, except one program: K3B. Right when I start it up, I get a KDE error message about bookmarks.xml, but I'm not too worried because it's always done that and worked fine anyway. But as soon as I click OK, the little penguin-with-torch splash disappears and I get a window telling me K3B "crashed and caused the signal 11 (SIGSEGV)." The backtrace, if it will help, is as follows:
```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233529152 (LWP 9299)]
[KCrash handler]
#4  0x08094570 in QValueList<KURL>::detachInternal ()
#5  0x0809bc7e in QValueList<int>::detachInternal ()
#6  0x0809bd11 in QValueList<int>::detachInternal ()
#7  0xb78659e4 in KMainWindow::shuttingDown () from /usr/lib/libkdeui.so.4
#8  0xb79a1e86 in KMainWindow::qt_invoke () from /usr/lib/libkdeui.so.4
#9  0xb79a1edc in KDockMainWindow::qt_invoke () from /usr/lib/libkdeui.so.4
#10 0xb7d4ab30 in KParts::DockMainWindow::qt_invoke ()
   from /usr/lib/libkparts.so.2
#11 0x0809f248 in QValueList<int>::detachInternal ()
#12 0xb6fb9a56 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#13 0xb6fba3c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#14 0xb75d7ea0 in KApplication::shutDown () from /usr/lib/libkdecore.so.4
#15 0xb75ec976 in KApplication::qt_emit () from /usr/lib/libkdecore.so.4
#16 0xb75ec9ab in KUniqueApplication::qt_emit () from /usr/lib/libkdecore.so.4
#17 0x0808bddb in QValueListPrivate<QString>::QValueListPrivate ()
#18 0xb6fb9a2a in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#19 0xb6fba3c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb7311437 in QApplication::aboutToQuit () from /usr/lib/libqt-mt.so.3
#21 0xb6f68dba in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#22 0xb6f4fc3f in QApplication::enter_loop () from /usr/lib/libqt-mt.so.3
#23 0xb716a320 in QDialog::exec () from /usr/lib/libqt-mt.so.3
#24 0xb796ec70 in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#25 0xb796f41d in KMessageBox::createKMessageBox ()
   from /usr/lib/libkdeui.so.4
#26 0xb796f91f in KMessageBox::errorListWId () from /usr/lib/libkdeui.so.4
#27 0xb799a1d5 in KMessageBox::error () from /usr/lib/libkdeui.so.4
#28 0xb7c3091a in KBookmarkManager::saveAs () from /usr/lib/libkio.so.4
#29 0xb7c30a18 in KBookmarkManager::save () from /usr/lib/libkio.so.4
#30 0xb7c4343b in KBookmarkManager::importDesktopFiles ()
   from /usr/lib/libkio.so.4
#31 0xb7c439b7 in KBookmarkManager::KBookmarkManager ()
   from /usr/lib/libkio.so.4
#32 0xb7c43a90 in KBookmarkManager::managerForFile ()
   from /usr/lib/libkio.so.4
#33 0xb7c43bbc in KBookmarkManager::userBookmarksManager ()
   from /usr/lib/libkio.so.4
#34 0xb7c469f0 in KBookmarkManager::setShowNSBookmarks ()
   from /usr/lib/libkio.so.4
#35 0x0808d4f7 in QPtrList<K3bDevice::Device>::~QPtrList ()
#36 0x080938c1 in endl ()
#37 0x08095970 in QValueList<KURL>::detachInternal ()
#38 0x0809b840 in QValueList<int>::detachInternal ()
#39 0x0809c155 in QValueList<int>::detachInternal ()
#40 0x0808bfc3 in QValueListPrivate<QString>::QValueListPrivate ()
#41 0x0809face in QPtrList<K3bPlugin>::~QPtrList ()
#42 0xb67f5ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#43 0x08086eb1 in ?? ()
```
I have already tried apt-get removing and re apt-get installing it. No change in its behavior.

---

