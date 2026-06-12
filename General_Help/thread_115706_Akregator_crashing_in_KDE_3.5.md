---
title: "Akregator crashing in KDE 3.5"
date: 2006-01-11
forum: General Help
---

### Post by alphabono on 2006-01-11
After upgrading akregator, I'm having problems.  When it loads, I get the error "Unable to load storage backend plugin "metakit". No feeds are archived."  It then downloads all feeds again (i.e. it has no history).  

When I go to "Configure Akregator" the program crashes citing "signal 11"

If I go to backtrace I get the following, but have little clue as to where to start trouble shooting.  Any suggestions?

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1241123136 (LWP 13766)]
[New Thread -1279419472 (LWP 13770)]
[New Thread -1271026768 (LWP 13769)]
[New Thread -1262634064 (LWP 13768)]
[New Thread -1254241360 (LWP 13767)]
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0xb33a23f8 in Akregator::SettingsAdvanced::SettingsAdvanced ()
   from /usr/lib/kde3/libakregatorpart.so
#5  0xb33a28e6 in Akregator::ConfigDialog::ConfigDialog ()
   from /usr/lib/kde3/libakregatorpart.so
#6  0xb33a2a4e in Akregator::Part::showOptions ()
   from /usr/lib/kde3/libakregatorpart.so
#7  0xb33a2b4b in Akregator::Part::qt_invoke ()
   from /usr/lib/kde3/libakregatorpart.so
#8  0xb72ef929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb72f03c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb68cc5f6 in KAction::activated () from /usr/lib/libkdeui.so.4
#11 0xb6902cfb in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#12 0xb691e96b in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#13 0xb691eca2 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#14 0xb72ef929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb764ee92 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#16 0xb730d344 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#17 0xb7412963 in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#18 0xb68d8aa0 in KPopupMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.4
#19 0xb732a356 in QWidget::event () from /usr/lib/libqt-mt.so.3
#20 0xb7286f80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb7287500 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb6f44c3c in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb7217e25 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#24 0xb7213072 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#25 0xb721166f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#26 0xb722afff in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#27 0xb729ecfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#28 0xb729ec1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#29 0xb7285c13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#30 0x0805aa4d in ?? ()
#31 0xbff73720 in ?? ()
#32 0x00000001 in ?? ()
#33 0x00000001 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000015 in ?? ()
#36 0x0804ea9b in ?? ()
#37 0x00000008 in ?? ()
#38 0x00000004 in ?? ()
#39 0xb79cecd0 in ?? () from /usr/lib/libstdc++.so.6
#40 0xb78c1908 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#41 0x00000002 in ?? ()
#42 0x00000015 in ?? ()
#43 0x08065248 in vtable for QGList ()
#44 0xb7f5e160 in ?? ()
#45 0x080b7428 in ?? ()
#46 0x00000000 in ?? ()
#47 0x080b7088 in ?? ()
#48 0x08167ca8 in ?? ()
#49 0x081677a0 in ?? ()
#50 0x08172140 in ?? ()
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x00000001 in ?? ()
#54 0x0807a178 in ?? ()
#55 0x00000000 in ?? ()
#56 0x00000000 in ?? ()
#57 0x08185098 in ?? ()
#58 0x080865a0 in ?? ()
#59 0x08153b50 in ?? ()
#60 0x08058700 in ?? ()
#61 0x080652cc in vtable for QGList ()
#62 0x08155840 in ?? ()
#63 0x081556a0 in ?? ()
#64 0x081712d8 in ?? ()
#65 0xb77824e0 in vtable for QCString () from /usr/lib/libqt-mt.so.3
#66 0x08078608 in ?? ()
#67 0xbff73804 in ?? ()
#68 0x08155350 in ?? ()
#69 0x0807a2f0 in ?? ()
#70 0x0000012a in ?? ()
#71 0x000001ff in ?? ()
#72 0xb7059ecc in ?? () from /usr/lib/libqt-mt.so.3
#73 0x00000000 in ?? ()
#74 0x0806bd40 in ?? ()
#75 0x08058701 in ?? ()
#76 0x08190518 in ?? ()
#77 0x08191e68 in ?? ()
#78 0xb77a19fc in ?? () from /lib/tls/i686/cmov/libc.so.6
#79 0xb779932c in ?? () from /lib/tls/i686/cmov/libc.so.6
#80 0x08077340 in ?? ()
#81 0x00000049 in ?? ()
#82 0xb7765460 in ?? () from /usr/lib/libqt-mt.so.3
#83 0x00000000 in ?? ()
#84 0xb7f74ca0 in _rtld_global () from /lib/ld-linux.so.2
#85 0xbff737e8 in ?? ()
#86 0xb72dfc5f in QAsciiDict<void>::insert () from /usr/lib/libqt-mt.so.3
#87 0xb77aaea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#88 0x08058561 in ?? ()

```

---

### Post by lippel on 2006-01-11
This looks like a personal installation fsckup or a problem with the kubuntu 3.5 packages. Make sure that you don't use 3.5 RC1 packages, as akregator was broken in there. It should be fixed in 3.5 packages though.

Run

kbuildsycoca

and try again to start akregator. If that does not help, check whether

/usr/lib/kde3/libakregator_mk4storage_plugin.so 

exists.

---

### Post by alphabono on 2006-01-11
Running kbuildsycoca fixed the problem!  Thanks so much!

---

