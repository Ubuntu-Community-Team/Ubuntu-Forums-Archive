---
title: "AmaroK 1.4.3 on Ubuntu 6.06 LTS"
date: 2006-09-05
forum: Desktop Environments
---

### Post by linzer on 2006-09-05
I'm trying to upgrade amaroK 1.4.2 to the latest 1.4.3 via the instructions on [http://kubuntu.org/announcements/amarok-1.4.3.php]("http://kubuntu.org/announcements/amarok-1.4.3.php").  I am NOT running kubuntu but rather ubuntu.

I have no problem adding the pgp key nor adding the source to my sources.list.  Next I sudo apt-get update.  To make things easier, I start synaptic, search for amaroK and can see 1.4.2-0ubuntu2~dap is installed along with amarok-xine of the same version.  If I try to mark for upgrade either of these packages, I run into problems.

Short answer is a dependency problem.

I try to uninstall amarok, amarok-xine and kubuntu-desktop then try installing again (1.4.3).

The error states the following:

amarok:

Depends: amarok-xine but it is not going to be installed
Depends: kdelibs4c2a (>=4.3.5.3-1) but 4.3.5.2-0ubuntu18.1 is to be installed.

Any suggestions as to how to proceed?

TIA

---

### Post by ButteBlues on 2006-09-05
$ sudo apt-get install kdelibs4c2a=4.3.5.3-1
$ sudo apt-get upgrade

---

### Post by linzer on 2006-09-05
Thanks will try and reply back in the morning.  Right now I'm waiting on 1.4.2 to rebuild its music library.

---

### Post by linzer on 2006-09-05
No such luck.

matt@ubuntu:~$ sudo apt-get install kdelibs4c2a=4.3.5.3-1
Reading package lists... Done
Building dependency tree... Done
E: Version '4.3.5.3-1' for 'kdelibs4c2a' was not found

---

### Post by jid on 2006-09-06
Hi,

You can add this repository to your sources.list, and the problem of "depends" disappear !!

deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main

Good luck

---

### Post by Antoine.L on 2006-09-06
This looks as good a place as any to report my problem:

I'm running Kubuntu 6.06.1, and I've upgraded to Amarok 1.4.3 using the kubuntu repos.

And now amarok crashes on start!  Below is the output that the mailer sends off to the amarok devs:

```

======== DEBUG INFORMATION  =======
Version:    1.4.3
Engine:     xine-engine
Build date: Sep  6 2006
CC version: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
KDElibs:    3.5.2
Qt:         3.3.6
TagLib:     1.4.0
CPU count:  1

==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: symbolic link to `/usr/bin/amarokapp'


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1249716544 (LWP 7162)]
[New Thread -1323308112 (LWP 7187)]
[New Thread -1296954448 (LWP 7176)]
[New Thread -1288561744 (LWP 7175)]
[New Thread -1278280784 (LWP 7174)]
[New Thread -1252987984 (LWP 7173)]
[New Thread -1261380688 (LWP 7170)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68eec in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb660df7f in QWaitCondition::wait () from /usr/lib/libqt-mt.so.3
#3  0xb733c309 in KNetwork::KResolver::wait () from /usr/lib/libkdecore.so.4
#4  0xb439702a in DaapClient::resolve ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#5  0xb4397e3a in DaapClient::resolvedDaap ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#6  0xb43984ce in DaapClient::qt_invoke ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#7  0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb632b211 in QObject::activate_signal_bool () from /usr/lib/libqt-mt.so.3
#9  0xb435ad7b in DNSSD::RemoteService::resolved ()
   from /usr/lib/libkdnssd.so.1
#10 0xb435e1bb in DNSSD::RemoteService::customEvent ()
   from /usr/lib/libkdnssd.so.1
#11 0xb6328157 in QObject::event () from /usr/lib/libqt-mt.so.3
#12 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#13 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#14 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#15 0xb435f23d in DNSSD::resolve_callback () from /usr/lib/libkdnssd.so.1
#16 0xb4340108 in avahi_service_resolver_event ()
   from /usr/lib/libavahi-client.so.3
#17 0xb433b84b in avahi_client_get_version_string ()
   from /usr/lib/libavahi-client.so.3
#18 0xb430cf5f in dbus_connection_dispatch () from /usr/lib/libdbus-1.so.2
#19 0xb4341db6 in avahi_error_number_to_dbus ()
   from /usr/lib/libavahi-client.so.3
#20 0xb44ce432 in AvahiTimeout::timeout () from /usr/lib/libavahi-qt3.so.1
#21 0xb44ce998 in AvahiTimeout::qt_invoke () from /usr/lib/libavahi-qt3.so.1
#22 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb632b954 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#24 0xb66c039e in QTimer::timeout () from /usr/lib/libqt-mt.so.3
#25 0xb634feb1 in QTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb62d9adf in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#33 0xb62bf90e in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#34 0xb62bf939 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#35 0xb7d9af9e in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
#36 0xb7d9b91e in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
#37 0xb7b8364b in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
#38 0xb7b562b8 in App::continueInit () from /usr/lib/libamarok.so.0
#39 0xb7b56e01 in App::qt_invoke () from /usr/lib/libamarok.so.0
#40 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#41 0xb66be29a in QSignal::signal () from /usr/lib/libqt-mt.so.3
#42 0xb6348630 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#43 0xb6350120 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#44 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#45 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#46 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#47 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#48 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#49 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#50 0xb62d9947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#51 0xb62d986a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#52 0xb62bf965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#53 0x0804bc67 in ?? ()
#54 0xbfe6d164 in ?? ()
#55 0xbfe6d2e4 in ?? ()
#56 0x00000019 in ?? ()
#57 0x080676ac in vtable for QGList ()
#58 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6c68eec in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb660df7f in QWaitCondition::wait () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#3  0xb733c309 in KNetwork::KResolver::wait () from /usr/lib/libkdecore.so.4
No symbol table info available.
#4  0xb439702a in DaapClient::resolve ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
No symbol table info available.
#5  0xb4397e3a in DaapClient::resolvedDaap ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
No symbol table info available.
#6  0xb43984ce in DaapClient::qt_invoke ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
No symbol table info available.
#7  0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#8  0xb632b211 in QObject::activate_signal_bool () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#9  0xb435ad7b in DNSSD::RemoteService::resolved ()
   from /usr/lib/libkdnssd.so.1
No symbol table info available.
#10 0xb435e1bb in DNSSD::RemoteService::customEvent ()
   from /usr/lib/libkdnssd.so.1
No symbol table info available.
#11 0xb6328157 in QObject::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#12 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#13 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#14 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#15 0xb435f23d in DNSSD::resolve_callback () from /usr/lib/libkdnssd.so.1
No symbol table info available.
#16 0xb4340108 in avahi_service_resolver_event ()
   from /usr/lib/libavahi-client.so.3
No symbol table info available.
#17 0xb433b84b in avahi_client_get_version_string ()
   from /usr/lib/libavahi-client.so.3
No symbol table info available.
#18 0xb430cf5f in dbus_connection_dispatch () from /usr/lib/libdbus-1.so.2
No symbol table info available.
#19 0xb4341db6 in avahi_error_number_to_dbus ()
   from /usr/lib/libavahi-client.so.3
No symbol table info available.
#20 0xb44ce432 in AvahiTimeout::timeout () from /usr/lib/libavahi-qt3.so.1
No symbol table info available.
#21 0xb44ce998 in AvahiTimeout::qt_invoke () from /usr/lib/libavahi-qt3.so.1
No symbol table info available.
#22 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#23 0xb632b954 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#24 0xb66c039e in QTimer::timeout () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#25 0xb634feb1 in QTimer::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#26 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#27 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#28 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#29 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#30 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#31 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#32 0xb62d9adf in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#33 0xb62bf90e in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#34 0xb62bf939 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#35 0xb7d9af9e in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#36 0xb7d9b91e in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#37 0xb7b8364b in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#38 0xb7b562b8 in App::continueInit () from /usr/lib/libamarok.so.0
No symbol table info available.
#39 0xb7b56e01 in App::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#40 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#41 0xb66be29a in QSignal::signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#42 0xb6348630 in QSignal::activate () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#43 0xb6350120 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#44 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#45 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#46 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#47 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#48 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#49 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#50 0xb62d9947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#51 0xb62d986a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#52 0xb62bf965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#53 0x0804bc67 in ?? ()
No symbol table info available.
#54 0xbfe6d164 in ?? ()
No symbol table info available.
#55 0xbfe6d2e4 in ?? ()
No symbol table info available.
#56 0x00000019 in ?? ()
No symbol table info available.
#57 0x080676ac in vtable for QGList ()
No symbol table info available.
#58 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 7 (Thread -1261380688 (LWP 7170)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68eec in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb429f6cf in xine_open () from /usr/lib/libxine.so.1
Thread 6 (Thread -1252987984 (LWP 7173)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb68cc8c4 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3d373bc in ?? ()
   from /usr/lib/xine/plugins/1.1.1/xineplug_ao_out_alsa.so
#3  0xb550e3a0 in ?? ()
#4  0x00000001 in ?? ()
#5  0x0000014d in ?? ()
#6  0x00000000 in ?? ()
Thread 5 (Thread -1278280784 (LWP 7174)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68c76 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb42b1454 in _x_ao_new_port () from /usr/lib/libxine.so.1
Thread 4 (Thread -1288561744 (LWP 7175)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68c76 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb42a2690 in xine_config_load () from /usr/lib/libxine.so.1
#3  0xb42d3164 in ?? () from /usr/lib/libxine.so.1
#4  0x00000000 in ?? ()
Thread 3 (Thread -1296954448 (LWP 7176)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68c76 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb42b1c40 in xine_event_wait () from /usr/lib/libxine.so.1
#3  0x085a1b38 in ?? ()
Thread 2 (Thread -1323308112 (LWP 7187)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c6c48b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d095 in amaroK::Crash::crashHandler ()
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb68359a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb68372b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb682ef51 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7338794 in KNetwork::KResolverWorkerBase::acquireResolver ()
   from /usr/lib/libkdecore.so.4
#9  0xb734286a in (anonymous namespace)::GetAddrInfoThread::run ()
   from /usr/lib/libkdecore.so.4
#10 0xb7342e0f in KNetwork::Internal::KGetAddrinfoWorker::run ()
   from /usr/lib/libkdecore.so.4
#11 0xb7338f4d in KNetwork::Internal::KResolverThread::run ()
   from /usr/lib/libkdecore.so.4
#12 0xb62b6f9a in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
#13 0xb6c66341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb68d64ee in clone () from /lib/tls/i686/cmov/libc.so.6
Thread 1 (Thread -1249716544 (LWP 7162)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c68eec in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb660df7f in QWaitCondition::wait () from /usr/lib/libqt-mt.so.3
#3  0xb733c309 in KNetwork::KResolver::wait () from /usr/lib/libkdecore.so.4
#4  0xb439702a in DaapClient::resolve ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#5  0xb4397e3a in DaapClient::resolvedDaap ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#6  0xb43984ce in DaapClient::qt_invoke ()
   from /usr/lib/kde3/libamarok_daap-mediadevice.so
#7  0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb632b211 in QObject::activate_signal_bool () from /usr/lib/libqt-mt.so.3
#9  0xb435ad7b in DNSSD::RemoteService::resolved ()
   from /usr/lib/libkdnssd.so.1
#10 0xb435e1bb in DNSSD::RemoteService::customEvent ()
   from /usr/lib/libkdnssd.so.1
#11 0xb6328157 in QObject::event () from /usr/lib/libqt-mt.so.3
#12 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#13 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#14 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#15 0xb435f23d in DNSSD::resolve_callback () from /usr/lib/libkdnssd.so.1
#16 0xb4340108 in avahi_service_resolver_event ()
   from /usr/lib/libavahi-client.so.3
#17 0xb433b84b in avahi_client_get_version_string ()
   from /usr/lib/libavahi-client.so.3
#18 0xb430cf5f in dbus_connection_dispatch () from /usr/lib/libdbus-1.so.2
#19 0xb4341db6 in avahi_error_number_to_dbus ()
   from /usr/lib/libavahi-client.so.3
#20 0xb44ce432 in AvahiTimeout::timeout () from /usr/lib/libavahi-qt3.so.1
#21 0xb44ce998 in AvahiTimeout::qt_invoke () from /usr/lib/libavahi-qt3.so.1
#22 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb632b954 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#24 0xb66c039e in QTimer::timeout () from /usr/lib/libqt-mt.so.3
#25 0xb634feb1 in QTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb62d9adf in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#33 0xb62bf90e in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#34 0xb62bf939 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#35 0xb7d9af9e in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
#36 0xb7d9b91e in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
#37 0xb7b8364b in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
#38 0xb7b562b8 in App::continueInit () from /usr/lib/libamarok.so.0
#39 0xb7b56e01 in App::qt_invoke () from /usr/lib/libamarok.so.0
#40 0xb632aeb9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#41 0xb66be29a in QSignal::signal () from /usr/lib/libqt-mt.so.3
#42 0xb6348630 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#43 0xb6350120 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#44 0xb62c0e56 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#45 0xb62c1052 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#46 0xb72ce7ab in KApplication::notify () from /usr/lib/libkdecore.so.4
#47 0xb6252157 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#48 0xb62b2843 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#49 0xb6265f67 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#50 0xb62d9947 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#51 0xb62d986a in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#52 0xb62bf965 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#53 0x0804bc67 in ?? ()
#54 0xbfe6d164 in ?? ()
#55 0xbfe6d2e4 in ?? ()
#56 0x00000019 in ?? ()
#57 0x080676ac in vtable for QGList ()
#58 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================
[
0: /usr/lib/libkdecore.so.4(_Z11kdBacktracei+0x45) [0xb722ff67]
1: /usr/lib/libkdecore.so.4(_Z11kdBacktracev+0x26) [0xb72302ac]
2: amarok(_ZN6amaroK5Crash12crashHandlerEi+0xcd1) [0x804cab1]
3: [0xffffe420]
4: /lib/tls/i686/cmov/libc.so.6(abort+0xe9) [0xb68372b9]
5: /lib/tls/i686/cmov/libc.so.6(__assert_fail+0x101) [0xb682ef51]
6: /usr/lib/libkdecore.so.4(_ZN8KNetwork16KReverseResolverC2ERKNS_14KSocketAddressEiP7QObjectPKc+0) [0xb7338794]
7: /usr/lib/libkdecore.so.4(_ZN43_GLOBAL__N__ZN8KNetwork14KResolverEntryC2Ev17GetAddrInfoThread3runEv+0x11a) [0xb734286a]
8: /usr/lib/libkdecore.so.4(_ZN8KNetwork8Internal18KGetAddrinfoWorker3runEv+0xc9) [0xb7342e0f]
9: /usr/lib/libkdecore.so.4(_ZN8KNetwork8Internal15KResolverThread3runEv+0x35) [0xb7338f4d]
10: /usr/lib/libqt-mt.so.3(_ZN15QThreadInstance5startEPv+0x86) [0xb62b6f9a]
11: /lib/tls/i686/cmov/libpthread.so.0 [0xb6c66341]
12: /lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb68d64ee]
]

```

---

### Post by svizi on 2006-09-13
I am trying to install amarok 1.4.3. I did the mistake to install the 1.3.9 from the ubuntu repositories. I then uninstall it from synaptic package manager and i try to install it using the above suggestions and i get the errors:

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages


Keep in mind that on a clean install of 6.06 i install amarok 1.4.3 but i didn't install 1.3.9 later. Can anyone give me some suggestions?

---

### Post by Baji on 2006-09-14
> **svizi said:**
> I am trying to install amarok 1.4.3. I did the mistake to install the 1.3.9 from the ubuntu repositories. I then uninstall it from synaptic package manager and i try to install it using the above suggestions and i get the errors:

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages


Keep in mind that on a clean install of 6.06 i install amarok 1.4.3 but i didn't install 1.3.9 later. Can anyone give me some suggestions?

quoting [http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

[B]Important:  you need to enable dapper-backports to be able to install Amarok 1.4.3. This includes unsupported updates for other popular packages including KTorrent and K3b.

Apt source:

    * deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main
[/B]

---

