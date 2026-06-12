---
title: "kdm broken"
date: 2006-02-02
forum: Desktop Environments
---

### Post by gammagoat on 2006-02-02
While installing either vegastrike or extra screen savers kdm has failed to funtion properly. I think from reading some other treads that, the nvidia driver that I am using maybe the cause. Am I thinking right? Any way here is the debuging info that gdb gives. Can someone tell me what this means?

my problem is very similar if not the same as this guys problem([http://www.ubuntuforums.org/showthread.php?t=125029)](http://www.ubuntuforums.org/showthread.php?t=125029)). I would really  like not to have to reinstall again, so please if any of you have a fix for me I would very much appreciate it.

Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

[Thread debugging using libthread_db enabled]
[New Thread -1228081472 (LWP 7329)]
(no debugging symbols found)
[KCrash handler]
#7  0xb74c3e28 in QObject::property () from /usr/lib/libqt-mt.so.3
#8  0x08077941 in QValueList<QString>::operator+= ()
#9  0xb6afc221 in KClassicGreeter::KClassicGreeter ()
   from /usr/lib/kde3/kgreet_classic.so
#10 0xb6afc26f in KClassicGreeter::KClassicGreeter ()
   from /usr/lib/kde3/kgreet_classic.so
#11 0x08065619 in ?? ()
#12 0x081973a0 in ?? ()
#13 0x08156398 in ?? ()
#14 0x081422e8 in ?? ()
#15 0x081427e8 in ?? ()
#16 0x0819740c in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x0805dfff in ?? ()
#20 0x08197378 in ?? ()
#21 0x00000115 in ?? ()
#22 0xbfc3c268 in ?? ()
#23 0x08197378 in ?? ()
#24 0x081427e8 in ?? ()
#25 0x081422e8 in ?? ()
#26 0xbfc3c278 in ?? ()
#27 0x08066275 in ?? ()
#28 0x08197378 in ?? ()
#29 0x00000000 in ?? ()
#30 0xbfc3c278 in ?? ()
#31 0x08064b40 in ?? ()
#32 0x081422e8 in ?? ()
#33 0x00000200 in ?? ()
#34 0x00000280 in ?? ()
#35 0x00000200 in ?? ()
#36 0x00000280 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000115 in ?? ()
#39 0x08197378 in ?? ()
#40 0x081427e8 in ?? ()
#41 0x081422e8 in ?? ()
#42 0xbfc3c2f8 in ?? ()
#43 0x08071f2b in ?? ()
#44 0x08197378 in ?? ()
#45 0x00000000 in ?? ()

---

### Post by gammagoat on 2006-02-02
FIXED
This is what I did

sudo apt-get install --reinstall kdm

ctrl alt F1

sudo/etc/init.d/kdm stop

sudo/etc/init.d/kdm. restart

shut down computer and restart.

---

### Post by jscat on 2006-02-11
Thanks for your own reply. I had to boot into recover mode then manually startx until I found this.

---

