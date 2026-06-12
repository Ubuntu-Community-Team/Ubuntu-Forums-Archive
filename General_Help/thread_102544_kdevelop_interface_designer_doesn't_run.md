---
title: "kdevelop interface designer doesn't run"
date: 2005-12-12
forum: General Help
---

### Post by eantoranz on 2005-12-12
I'm testing kdevelop to see if it's fit for our development needs.

I want to run the interface designer, but I get a application crash.

This is the backtrace:
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
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
[New Thread -1231202624 (LWP 921)]
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
#4  0xb6caeef1 in XCreateGC () from /usr/lib/libX11.so.6
#5  0xb711e8bb in qsincos () from /usr/lib/libqt-mt.so.3
#6  0xb711eee0 in qsincos () from /usr/lib/libqt-mt.so.3
#7  0xb711f301 in QPainter::updatePen () from /usr/lib/libqt-mt.so.3
#8  0xb71d7d8f in QPainter::setPen () from /usr/lib/libqt-mt.so.3
#9  0xb730bd54 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#10 0xb730b910 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#11 0xb730b969 in QSplashScreen::repaint () from /usr/lib/libqt-mt.so.3
#12 0xb730baff in QSplashScreen::setPixmap () from /usr/lib/libqt-mt.so.3
#13 0xb730bba8 in QSplashScreen::QSplashScreen () from /usr/lib/libqt-mt.so.3
#14 0x0804eac4 in ?? ()
#15 0x081794c0 in ?? ()
#16 0xbfa9cd5c in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000001 in ?? ()
#21 0x0804fef8 in vtable for QGList ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x0804fe64 in vtable for QGList ()
#25 0xb7f9f838 in ?? () from /lib/ld-linux.so.2
#26 0x00000000 in ?? ()
#27 0xb7f891ac in ?? ()
#28 0xbfa9ccd8 in ?? ()
#29 0xb7f917c9 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#30 0xb6a17ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x0804e7c1 in ?? ()

```

Any ideas what I have to do? maybe I'm missing a package???

I'm using kubuntu breezy

---

### Post by eantoranz on 2005-12-12
It's solved!

Short answer:

go to /usr/share/apps/
link kdevelop3 to kdevelop: ln -s kdevelop3 kdevelop

I saw the answer here: [http://www.linuxquestions.org/questions/showthread.php?postid=1625635](http://www.linuxquestions.org/questions/showthread.php?postid=1625635)

---

