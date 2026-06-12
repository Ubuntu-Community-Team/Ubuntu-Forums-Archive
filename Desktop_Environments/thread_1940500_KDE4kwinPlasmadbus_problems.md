---
title: "KDE4/kwin/Plasma/dbus problems"
date: 2012-03-13
forum: Desktop Environments
---

### Post by ArgentSun on 2012-03-13
Here's the story before all hell broke loose. Feel free to skip straight to the problem.

I did a system-wide package update a few days ago (more like over a week), and it looks like I managed to break a few things. I run Kubuntu 11.10 (Oneiric) and was using my default software manager (Muon) to do the update. It wasn't a very big update, but I had just added a repository to my sources.list, so I gave it plenty of time. I guess one of the problems was that I decided to nuke Muon, because it was stuck on doing something dpkg for a few hours. Figured if it's not done by then, it won't be. So I Ctrl-Alt-ESC'ed it and did a standard apt-get update, followed by apt-get upgrade. It looked like everything was alright, until I rebooted...

Now, the problem...
The very first time I tried logging in through KDM after those updates, I got an error:
```
Warning: Cannot open ConsoleKit session: Unable to open session: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```
The warning dialog box has only an [OK] button, which when pressed attempts to load everything normally. Kwin doesn't start though - applications like Dolphin and Skype look fine. 

In addition to this, the KDE Daemon and Plasma Desktop Shell crash as soon as I click [OK] in that warning box up there. The short error details (I will provide stack traces in a moment) are as follows:
```
Executable: kdeinit4 PID: 1751 Signal: Segmentation Fault (11)
Executable: plasma-desktop PID: 1791 Signal: Segmentation Fault (11)
```

I am not sure how many of those things are related, but I dumping everything in here. On a possibly related note, my ethernet service was not starting, but I fixed that previously.

---

### Post by ArgentSun on 2012-03-13
Here are the stack backtraces:

```
Application: KDE Daemon (kdeinit4), signal: Segmentation fault
[KCrash Handler]
#6  0x00007fd3f2521c54 in QDBusMessage::arguments() const () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#7  0x00007fd3f254f91e in QDBusPendingReplyData::argumentAt(int) const () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#8  0x00007fd3da5e4442 in NMNetworkManager::NMNetworkManager(QObject*, QList<QVariant> const&) () from /usr/lib/kde4/solid_networkmanager09.so
#9  0x00007fd3da5e1477 in QObject* KPluginFactory::createInstance<NMNetworkManager, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/solid_networkmanager09.so
#10 0x00007fd3f5491d61 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#11 0x00007fd3daee175e in ?? () from /usr/lib/libsolidcontrolnm09.so.4
#12 0x00007fd3daee3fca in ?? () from /usr/lib/libsolidcontrolnm09.so.4
#13 0x00007fd3daee4e6e in Solid::Control::NetworkManagerNm09::notifier() () from /usr/lib/libsolidcontrolnm09.so.4
#14 0x00007fd3db387a60 in ConnectionUsageMonitor::ConnectionUsageMonitor(ConnectionList*, ActivatableList*, QObject*) () from /usr/lib/libknmservice.so.4
#15 0x00007fd3db7eb22f in ?? () from /usr/lib/kde4/kded_networkmanagement.so
#16 0x00007fd3db7eb587 in QObject* KPluginFactory::createInstance<NetworkManagementService, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/kded_networkmanagement.so
#17 0x00007fd3f5491d61 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#18 0x00007fd3e37f340d in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
#19 0x00007fd3e37f4657 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
#20 0x00007fd3e37f63c1 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
#21 0x00007fd3f5cbbd92 in ?? () from /usr/lib/libkdeui.so.5
#22 0x00007fd3f5cbbe32 in ?? () from /usr/lib/libkdeui.so.5
#23 0x00007fd3f25160e9 in ?? () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#24 0x00007fd3f251719b in ?? () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#25 0x00007fd3f2517b22 in ?? () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#26 0x00007fd3f2517bf8 in ?? () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#27 0x00007fd3f4f58a5e in QObject::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#28 0x00007fd3f42f5324 in QApplication::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#29 0x00007fd3f42f1474 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#30 0x00007fd3f42f62e1 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#31 0x00007fd3f5cb6466 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#32 0x00007fd3f4f41afc in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#33 0x00007fd3f4f4551f in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#34 0x00007fd3f4f6ca73 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#35 0x00007fd3f0d23a5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#36 0x00007fd3f0d24258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#37 0x00007fd3f0d24429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#38 0x00007fd3f4f6ced6 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#39 0x00007fd3f439910e in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#40 0x00007fd3f4f40cf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#41 0x00007fd3f4f40ef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#42 0x00007fd3f4f45789 in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#43 0x00007fd3e37f2d65 in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_kded4.so
#44 0x0000000000408547 in _start ()

```

```
Application: Plasma Desktop Shell (plasma-desktop), signal: Segmentation fault
[Current thread is 1 (Thread 0x7f6bae9607a0 (LWP 1791))]

Thread 3 (Thread 0x7f6b90884700 (LWP 1792)):
#0  0x00007f6bae242473 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f6ba257df68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f6ba257e429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f6bab425f3e in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007f6bab3f9cf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f6bab3f9ef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#6  0x00007f6bab31127f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f6bab3dccbf in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f6bab313d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f6ba308cefc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#10 0x00007f6bae24e59d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7f6b8531b700 (LWP 1793)):
#0  0x00007f6bae242473 in poll () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f6ba257df68 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f6ba257e429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f6bab425f3e in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007f6bab3f9cf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f6bab3f9ef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#6  0x00007f6bab31127f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f6bab3dccbf in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f6bab313d05 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f6ba308cefc in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
#10 0x00007f6bae24e59d in clone () from /lib/x86_64-linux-gnu/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f6bae9607a0 (LWP 1791)):
[KCrash Handler]
#6  0x00007f6bab75dc54 in QDBusMessage::arguments() const () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#7  0x00007f6bab78b91e in QDBusPendingReplyData::argumentAt(int) const () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#8  0x00007f6b821f4442 in NMNetworkManager::NMNetworkManager(QObject*, QList<QVariant> const&) () from /usr/lib/kde4/solid_networkmanager09.so
#9  0x00007f6b821f1477 in QObject* KPluginFactory::createInstance<NMNetworkManager, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/solid_networkmanager09.so
#10 0x00007f6babbc3d61 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#11 0x00007f6b82d8375e in ?? () from /usr/lib/libsolidcontrolnm09.so.4
#12 0x00007f6b82d85fca in ?? () from /usr/lib/libsolidcontrolnm09.so.4
#13 0x00007f6b82d8841e in Solid::Control::NetworkManagerNm09::networkInterfaces() () from /usr/lib/libsolidcontrolnm09.so.4
#14 0x00007f6b838ac7da in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#15 0x00007f6b838adee7 in QObject* KPluginFactory::createInstance<NetworkManagerApplet, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#16 0x00007f6babbc3d61 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5
#17 0x00007f6badd8fb6f in Plasma::PluginLoader::loadApplet(QString const&, unsigned int, QList<QVariant> const&) () from /usr/lib/libplasma.so.3
#18 0x00007f6b94341008 in ?? () from /usr/lib/kde4/plasma_applet_systemtray.so
#19 0x00007f6b9433f0de in ?? () from /usr/lib/kde4/plasma_applet_systemtray.so
#20 0x00007f6b9434045f in ?? () from /usr/lib/kde4/plasma_applet_systemtray.so
#21 0x00007f6b9434b6b5 in ?? () from /usr/lib/kde4/plasma_applet_systemtray.so
#22 0x00007f6b943493a1 in ?? () from /usr/lib/kde4/plasma_applet_systemtray.so
#23 0x00007f6badd490bf in Plasma::Applet::flushPendingConstraintsEvents() () from /usr/lib/libplasma.so.3
#24 0x00007f6badd593f7 in ?? () from /usr/lib/libplasma.so.3
#25 0x00007f6badd6db52 in ?? () from /usr/lib/libplasma.so.3
#26 0x00007f6badd6e824 in Plasma::Corona::loadLayout(QString const&) () from /usr/lib/libplasma.so.3
#27 0x00007f6badd6e8ec in Plasma::Corona::initializeLayout(QString const&) () from /usr/lib/libplasma.so.3
#28 0x00007f6bae56644b in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_plasma-desktop.so
#29 0x00007f6bae56676a in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_plasma-desktop.so
#30 0x00007f6bae567f42 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_plasma-desktop.so
#31 0x00007f6bab411a5e in QObject::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#32 0x00007f6baa7ae324 in QApplication::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#33 0x00007f6baa7aa474 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#34 0x00007f6baa7af2e1 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#35 0x00007f6bac0a9466 in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#36 0x00007f6bab3faafc in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#37 0x00007f6bab3fe51f in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#38 0x00007f6bab425a73 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#39 0x00007f6ba257da5d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#40 0x00007f6ba257e258 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#41 0x00007f6ba257e429 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#42 0x00007f6bab425ed6 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#43 0x00007f6baa85210e in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#44 0x00007f6bab3f9cf2 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#45 0x00007f6bab3f9ef7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#46 0x00007f6bab3fe789 in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#47 0x00007f6bae54d1a3 in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_plasma-desktop.so
#48 0x00007f6bae18c30d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
#49 0x0000000000400671 in _start ()

```

---

### Post by Zorael on 2012-03-17
Well, it seems like dbus isn't running for whatever reason.

If you can get a terminal up, could you check to make sure it's there?
```
$ ps aux | grep dbus
```

If it's not, try starting it and see if it outputs anything of interest.
```
$ sudo start dbus
```

Also make sure that the line '**use-session-dbus**' is present and not commented in **/etc/X11/Xsession.options**.

You could also try reinstalling the entire package.
```
$ sudo apt-get install --reinstall dbus dbus-x11
```

---

### Post by heraklejon on 2013-03-26
SOLVED!! :D

Some one came to me with a PC giving the same error:
```

Warning: Cannot open ConsoleKit session: Unable to open session: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

```

This person's complain wasn't that error, but that she had no Internet. At first glance I didn't notice the error but that device eth0 was missing from ifconfig's output. Then, I realized the dbus error and found this post. So, following Zorael's answer, first I realized dbus wasn't running and then I noted it was not properly installed!!. According to dpkg-query it was Unpacked, so a simple dpkg --configure -a solved it.

There was no Internet because eth0 was managed by NetworkManager and it needs dbus in order to run.

Simulated code:
```

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3519847 (3.5 MB)  TX bytes:3519847 (3.5 MB)

$ ps -A | grep NetworkManager

$ ps -A | grep dbus

$ dpkg-query -l dbus*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-======================================
iU  dbus                            1.4.18-1ubuntu1.3               simple interprocess messaging system (daemon and utilities)
iU  dbus-x11                        1.4.18-1ubuntu1.3               simple interprocess messaging system (X11 deps)

$ sudo dpkg --configure -a
...

$ dpkg-query -l dbus*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version                         Description
+++-===============================-===============================-=======================================
ii  dbus                            1.4.18-1ubuntu1.3               simple interprocess messaging system (daemon and utilities)
ii  dbus-x11                        1.4.18-1ubuntu1.3               simple interprocess messaging system (X11 deps)

$ ps -A | grep dbus
  555 ?        00:00:50 dbus-daemon
 1640 ?        00:00:00 dbus-launch
 1644 ?        00:00:08 dbus-daemon
 3488 ?        00:00:00 dbus
 3713 ?        00:00:00 dbus

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:e8:bb:f6:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xe000 

$ ps -A | grep NetworkManager
  912 ?        00:00:20 NetworkManager

```

Last, but not least, my thanks to Zorael because I managed to solve this problem thanks to his hint.

---

