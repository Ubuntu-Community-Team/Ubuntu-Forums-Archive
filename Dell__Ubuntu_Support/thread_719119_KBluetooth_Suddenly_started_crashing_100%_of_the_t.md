---
title: "KBluetooth Suddenly started crashing 100% of the time"
date: 2008-03-08
forum: Dell  Ubuntu Support
---

### Post by Beloch on 2008-03-08
Hi there, 
     My Dell m1330 laptop is almost two weeks old.  Bluetooth worked very well from the start... until today.

I rebooted and now, whenever I boot or try to start Kbluetooth manually, it immediately crashes.  The backtrace is below.

I primarily use bluetooth with a Dell Travel Mouse.  I also pair my cellphone and use KBluelock, although I've just been using the mouse today.  

I've tried apt-get remove on kdebluetooth and then reinstalling, but that didn't make any difference.  Any thoughts?  

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
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233652032 (LWP 6346)]
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
#6  0xb7351416 in QString::latin1 () from /usr/lib/libqt-mt.so.3
#7  0xb7354700 in QString::ascii () from /usr/lib/libqt-mt.so.3
#8  0xb7f0e036 in KBluetooth::DBusSignal::newMessage ()
   from /usr/lib/libkbluetooth.so.0
#9  0xb7f0ecdc in KBluetooth::DBusSignal::getString ()
   from /usr/lib/libkbluetooth.so.0
#10 0xb7f0eee8 in KBluetooth::DBusSignal::getString ()
   from /usr/lib/libkbluetooth.so.0
#11 0xb7f09ec5 in KBluetooth::Adapter::getMode ()
   from /usr/lib/libkbluetooth.so.0
#12 0x08059711 in ?? ()
#13 0xbf969888 in ?? ()
#14 0x080d1160 in ?? ()
#15 0xbf969864 in ?? ()
#16 0xb6a2eff4 in ?? () from /usr/lib/libstdc++.so.6
#17 0xbf9698c4 in ?? ()
#18 0x080d10c8 in ?? ()
#19 0xbf969868 in ?? ()
#20 0xb69fad81 in operator delete () from /usr/lib/libstdc++.so.6
#21 0x0805bd88 in ?? ()
#22 0x080d0fb8 in ?? ()
#23 0x00000000 in ?? ()

```

---

