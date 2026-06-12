---
title: "kded keeps crashing"
date: 2008-03-04
forum: Desktop Environments
---

### Post by cptnobvious999 on 2008-03-04
I installed Kubuntu Hardy Alpha 5 on my Inspiron 1420N and everything seemed to be working fine. After setting everything up and applying some updates though, kded crashes as soon as I hit the house button on my keyboard to open up Amarok. After that happens I can no longer use that or the volume buttons.

Any ideas?? How would I go about finding the cause of this problem?

The backtrace provides the following:
```
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread 0xb67ee6c0 (LWP 9548)]
[KCrash handler]
#6  KConfigBase::readEntry (this=0x4d004b, pKey=0x829fa50 "search", 
    aDefault=@0xbf959144)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kconfigbase.cpp:216
#7  0xb787d722 in KConfigBase::readEntry (this=0x4d004b, pKey=@0xbf959148, 
    aDefault=@0xbf959144)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kconfigbase.cpp:206
#8  0xb62864d6 in KMilo::GenericMonitor::launch ()
   from /usr/lib/kde3/kmilo_generic.so
#9  0xb6286857 in KMilo::GenericMonitor::launchMusic ()
   from /usr/lib/kde3/kmilo_generic.so
#10 0xb6289e79 in KMilo::GenericMonitor::qt_invoke ()
   from /usr/lib/kde3/kmilo_generic.so
#11 0xb77fa243 in KGlobalAccelPrivate::activate (this=0x81e2b58, 
    pAction=0x81e32f8, seq=@0xbf9592bc)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kglobalaccel_x11.cpp:379
#12 0xb78869be in KGlobalAccelPrivate::x11KeyPress (this=0x81e2b58, 
    pEvent=0xbf959698)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kglobalaccel_x11.cpp:347
#13 0xb7886bdc in KGlobalAccelPrivate::x11Event (this=0x81e2b58, 
    pEvent=0xbf959698)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kglobalaccel_x11.cpp:255
#14 0xb7895b7a in KApplication::x11EventFilter (this=0xbf9598d4, 
    _event=0xbf959698)
    at /build/buildd/kdelibs-3.5.9/./kdecore/kapplication.cpp:1659
#15 0xb710f480 in qt_x11EventFilter (ev=0xbf959698)
    at kernel/qapplication_x11.cpp:391
#16 0xb711fa9b in QApplication::x11ProcessEvent (this=0xbf9598d4, 
    event=0xbf959698) at kernel/qapplication_x11.cpp:3348
#17 0xb713792f in QEventLoop::processEvents (this=0x80e70f8, flags=4)
    at kernel/qeventloop_x11.cpp:195
#18 0xb71adf90 in QEventLoop::enterLoop (this=0x80e70f8)
    at kernel/qeventloop.cpp:201
#19 0xb71adc8e in QEventLoop::exec (this=0x80e70f8)
    at kernel/qeventloop.cpp:148
#20 0xb71947df in QApplication::exec (this=0xbf9598d4)
    at kernel/qapplication.cpp:2761
#21 0xb667e318 in kdemain (argc=2, argv=0x80a6eb8)
    at /build/buildd/kdelibs-3.5.9/./kded/kded.cpp:961
#22 0xb6697454 in kdeinitmain (argc=2, argv=0x80a6eb8) at kded_dummy.cpp:3
#23 0x0804ee20 in launch (argc=2, _name=0x8051039 "kded", args=0x805105c "", 
    cwd=0x0, envc=0, envs=0x0, reset_env=false, tty=0x0, avoid_loops=false, 
    startup_id_str=0x805100d "0")
    at /build/buildd/kdelibs-3.5.9/./kinit/kinit.cpp:673
#24 0x08050637 in main (argc=5, argv=0xbf959d94, envp=0xbf959dac)
    at /build/buildd/kdelibs-3.5.9/./kinit/kinit.cpp:1855
#25 0xb7c63450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#26 0x0804bb91 in _start ()

```

---

### Post by kuja on 2008-04-09
I'm getting the same problem on my 1420n ...What you need to do is report this at [http://www.launchpad.net](http://www.launchpad.net) -Report it against the kdelibs4c2a package.

---

