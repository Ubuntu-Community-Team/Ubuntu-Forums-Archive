---
title: "Cannot move files to the trash again"
date: 2009-06-10
forum: Desktop Environments
---

### Post by bryanbankester on 2009-06-10
Whenever I try to move a file to the trash using Dolphin, a "Moving" window appears that has the Source and Destination (trash:/). That window does not go away; it stays at 0 B/s and never progresses. I can drag files to any folder except to the Trash (trash:/). I can even drag files to the "/home/username/.local/share/Trash/files/" directory using Dolphin and can move files to the trash using the mv command in the terminal: ```
mv /home/username/filename.ext /home/username/.local/share/Trash/files/
```

I can move files to the trash using Thunar file manager without problems. In Thunar, when I press DEL, the file goes to the trash. In Dolphin, when I press DEL or right click and select "Move to Trash", the files stays put. I have tried reinstalling Dolphin, setting the Dolphin configuration to default values, and restarting the computer. 
I have the latest recommended updates for Kubuntu Jaunty amd64.

Also, when I right click inside the Trash (trash:/) window in the white area and select Properties, "The KDE Crash Handler" window appears and says:

**A Fatal Error Occurred**
The application Dolphin (dolphin) crashed and caused the signal 6 (SIGABRT).

Application: Dolphin (dolphin), signal SIGABRT
0x00007fde040accf0 in nanosleep () from /lib/libc.so.6

Thread 1 (Thread 0x7fde08a4c750 (LWP 5825)):
[KCrash Handler]
#5  0x00007fde04037fb5 in raise () from /lib/libc.so.6
#6  0x00007fde04039bc3 in abort () from /lib/libc.so.6
#7  0x00007fde04030f09 in __assert_fail () from /lib/libc.so.6
#8  0x00007fde03b93012 in Strigi::AnalysisResult::Private::Private () from /usr/lib/libstreamanalyzer.so.0
#9  0x00007fde03b93130 in Strigi::AnalysisResult::AnalysisResult () from /usr/lib/libstreamanalyzer.so.0
#10 0x00007fde084ea709 in ?? () from /usr/lib/libkio.so.5
#11 0x00007fde084ebd22 in KFileMetaInfo::KFileMetaInfo () from /usr/lib/libkio.so.5
#12 0x00007fde084dbc3c in KFileItem::metaInfo () from /usr/lib/libkio.so.5
#13 0x00007fde085995f0 in KFileMetaPropsPlugin::KFileMetaPropsPlugin () from /usr/lib/libkio.so.5
#14 0x00007fde085bd841 in KPropertiesDialog::KPropertiesDialogPrivate::insertPages () from /usr/lib/libkio.so.5
#15 0x00007fde085bda93 in KPropertiesDialog::KPropertiesDialogPrivate::init () from /usr/lib/libkio.so.5
#16 0x00007fde085bee28 in KPropertiesDialog::KPropertiesDialog () from /usr/lib/libkio.so.5
#17 0x00007fde07a6234a in DolphinViewActionHandler::slotProperties () from /usr/lib/libdolphinprivate.so.4
#18 0x00007fde07a4aa9a in DolphinViewActionHandler::qt_metacall () from /usr/lib/libdolphinprivate.so.4
#19 0x00007fde04c8c1f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#20 0x00007fde0513e7e7 in QAction::triggered () from /usr/lib/libQtGui.so.4
#21 0x00007fde0513fc60 in QAction::activate () from /usr/lib/libQtGui.so.4
#22 0x00007fde0556da3c in ?? () from /usr/lib/libQtGui.so.4
#23 0x00007fde05573a0e in ?? () from /usr/lib/libQtGui.so.4
#24 0x00007fde067b9b71 in KMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.5
#25 0x00007fde051958cf in QWidget::event () from /usr/lib/libQtGui.so.4
#26 0x00007fde055761cb in QMenu::event () from /usr/lib/libQtGui.so.4
#27 0x00007fde0514478d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#28 0x00007fde0514d0da in QApplication::notify () from /usr/lib/libQtGui.so.4
#29 0x00007fde066e826b in KApplication::notify () from /usr/lib/libkdeui.so.5
#30 0x00007fde04c7675c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#31 0x00007fde0514c328 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#32 0x00007fde051b5fd4 in ?? () from /usr/lib/libQtGui.so.4
#33 0x00007fde051b4a88 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#34 0x00007fde051dd464 in ?? () from /usr/lib/libQtGui.so.4
#35 0x00007fde004f220a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#36 0x00007fde004f58e0 in ?? () from /usr/lib/libglib-2.0.so.0
#37 0x00007fde004f5a7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#38 0x00007fde04c9fe6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#39 0x00007fde051dcbef in ?? () from /usr/lib/libQtGui.so.4
#40 0x00007fde04c75002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#41 0x00007fde04c753cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#42 0x00007fde05576025 in QMenu::exec () from /usr/lib/libQtGui.so.4
#43 0x00000000004350a7 in _start ()

---

