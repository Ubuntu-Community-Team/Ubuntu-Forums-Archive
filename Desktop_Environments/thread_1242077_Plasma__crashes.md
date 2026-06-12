---
title: "Plasma  crashes"
date: 2009-08-16
forum: Desktop Environments
---

### Post by Patricrawley on 2009-08-16
I tried to install the Magic Folder and Facebook plasmoids using plasmapkg -i, installing from a local folder and by downloading through the add widget window. All three of these installs crashes my plasma environment. I am running KDE 4.3 on an x64 jaunty system.

---

### Post by Patricrawley on 2009-08-17
```
Application: Plasma Workspace (kdeinit4), signal: Segmentation fault
[Current thread is 0 (LWP 3639)]

Thread 2 (Thread 0x7ffb3f85f950 (LWP 3642)):
#0  0x00007ffb5b2b62e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00007ffb5f3b9d19 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#2  0x00007ffb5e24381c in ?? () from /usr/lib/libQtNetwork.so.4
#3  0x00007ffb5f3b8d35 in ?? () from /usr/lib/libQtCore.so.4
#4  0x00007ffb5b2b23ba in start_thread () from /lib/libpthread.so.0
#5  0x00007ffb5be96fcd in clone () from /lib/libc.so.6
#6  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ffb5f97e750 (LWP 3639)):
[KCrash Handler]
#5  0x00007ffb5be31c60 in strlen () from /lib/libc.so.6
#6  0x00007ffb390be70f in PyString_FromFormatV () from /usr/lib/libpython2.6.so.1.0
#7  0x00007ffb3911cb50 in PyErr_Format () from /usr/lib/libpython2.6.so.1.0
#8  0x00007ffb3884e8b5 in ?? () from /usr/lib/python2.6/dist-packages/sip.so
#9  0x00007ffb37b7c468 in initplasma () from /usr/lib/python2.6/dist-packages/PyKDE4/plasma.so
#10 0x00007ffb39127ab6 in _PyImport_LoadDynamicModule () from /usr/lib/libpython2.6.so.1.0
#11 0x00007ffb39125f49 in ?? () from /usr/lib/libpython2.6.so.1.0
#12 0x00007ffb391261e2 in ?? () from /usr/lib/libpython2.6.so.1.0
#13 0x00007ffb39126888 in ?? () from /usr/lib/libpython2.6.so.1.0
#14 0x00007ffb39126e3f in PyImport_ImportModuleLevel () from /usr/lib/libpython2.6.so.1.0
#15 0x00007ffb391091dd in ?? () from /usr/lib/libpython2.6.so.1.0
#16 0x00007ffb39067c48 in PyObject_Call () from /usr/lib/libpython2.6.so.1.0
#17 0x00007ffb391097c6 in PyEval_CallObjectWithKeywords () from /usr/lib/libpython2.6.so.1.0
#18 0x00007ffb3910d6ad in PyEval_EvalFrameEx () from /usr/lib/libpython2.6.so.1.0
#19 0x00007ffb391109a9 in PyEval_EvalCodeEx () from /usr/lib/libpython2.6.so.1.0
#20 0x00007ffb39110ac2 in PyEval_EvalCode () from /usr/lib/libpython2.6.so.1.0
#21 0x00007ffb391232f0 in PyImport_ExecCodeModuleEx () from /usr/lib/libpython2.6.so.1.0
#22 0x00007ffb3912507c in ?? () from /usr/lib/libpython2.6.so.1.0
#23 0x00007ffb39125f49 in ?? () from /usr/lib/libpython2.6.so.1.0
#24 0x00007ffb391261e2 in ?? () from /usr/lib/libpython2.6.so.1.0
#25 0x00007ffb3912683c in ?? () from /usr/lib/libpython2.6.so.1.0
#26 0x00007ffb39126e3f in PyImport_ImportModuleLevel () from /usr/lib/libpython2.6.so.1.0
#27 0x00007ffb391091dd in ?? () from /usr/lib/libpython2.6.so.1.0
#28 0x00007ffb39067c48 in PyObject_Call () from /usr/lib/libpython2.6.so.1.0
#29 0x00007ffb3906a40e in PyObject_CallFunction () from /usr/lib/libpython2.6.so.1.0
#30 0x00007ffb3912700c in PyImport_Import () from /usr/lib/libpython2.6.so.1.0
#31 0x00007ffb391271d5 in PyImport_ImportModule () from /usr/lib/libpython2.6.so.1.0
#32 0x00007ffb394c8e86 in ?? () from /usr/lib/kde4/kpythonpluginfactory.so
#33 0x00007ffb394cb1ac in ?? () from /usr/lib/kde4/kpythonpluginfactory.so
#34 0x00007ffb56e3a26f in ?? () from /usr/lib/libplasma.so.3
#35 0x00007ffb56e3a7ee in Plasma::loadScriptEngine () from /usr/lib/libplasma.so.3
#36 0x00007ffb56dcf308 in ?? () from /usr/lib/libplasma.so.3
#37 0x00007ffb56dd0079 in Plasma::Applet::Applet () from /usr/lib/libplasma.so.3
#38 0x00007ffb56dd0b9c in Plasma::Applet::load () from /usr/lib/libplasma.so.3
#39 0x00007ffb56ddf8d6 in ?? () from /usr/lib/libplasma.so.3
#40 0x00007ffb5331d13f in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#41 0x00007ffb53321dc8 in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#42 0x00007ffb5f4b7ea2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#43 0x00007ffb5daf4085 in KDialog::slotButtonClicked () from /usr/lib/libkdeui.so.5
#44 0x00007ffb5daf629d in KDialog::qt_metacall () from /usr/lib/libkdeui.so.5
#45 0x00007ffb5332170d in ?? () from /usr/lib/libkdeinit4_plasma-desktop.so
#46 0x00007ffb5f4b7ea2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#47 0x00007ffb5f4bac3e in QSignalMapper::mapped () from /usr/lib/libQtCore.so.4
#48 0x00007ffb5f4bb4e0 in QSignalMapper::map () from /usr/lib/libQtCore.so.4
#49 0x00007ffb5f4bc0d0 in QSignalMapper::qt_metacall () from /usr/lib/libQtCore.so.4
#50 0x00007ffb5f4b7ea2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#51 0x00007ffb5d08fe27 in QAbstractButton::clicked () from /usr/lib/libQtGui.so.4
#52 0x00007ffb5cde9c6b in ?? () from /usr/lib/libQtGui.so.4
#53 0x00007ffb5cdeb8c2 in ?? () from /usr/lib/libQtGui.so.4
#54 0x00007ffb5cdebb15 in QAbstractButton::mouseReleaseEvent () from /usr/lib/libQtGui.so.4
#55 0x00007ffb5cabf0bf in QWidget::event () from /usr/lib/libQtGui.so.4
#56 0x00007ffb5ca6df4d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#57 0x00007ffb5ca768ea in QApplication::notify () from /usr/lib/libQtGui.so.4
#58 0x00007ffb5db8071b in KApplication::notify () from /usr/lib/libkdeui.so.5
#59 0x00007ffb5f4a26ac in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#60 0x00007ffb5ca75b38 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#61 0x00007ffb5cadfb19 in ?? () from /usr/lib/libQtGui.so.4
#62 0x00007ffb5cadeb53 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#63 0x00007ffb5cb07454 in ?? () from /usr/lib/libQtGui.so.4
#64 0x00007ffb5b50120a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#65 0x00007ffb5b5048e0 in ?? () from /usr/lib/libglib-2.0.so.0
#66 0x00007ffb5b504a7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#67 0x00007ffb5f4cba8f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#68 0x00007ffb5cb06bdf in ?? () from /usr/lib/libQtGui.so.4
#69 0x00007ffb5f4a0f42 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#70 0x00007ffb5f4a1314 in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#71 0x00007ffb5f4a35e4 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#72 0x00007ffb532ff1eb in kdemain () from /usr/lib/libkdeinit4_plasma-desktop.so
#73 0x0000000000407215 in _start ()

```

This is the error from starting the magic folder plasmoid

---

### Post by krazyd on 2009-08-18
you might have more luck with this kind of kde-specific question on the kde forums: [http://forum.kde.org/](http://forum.kde.org/)

---

