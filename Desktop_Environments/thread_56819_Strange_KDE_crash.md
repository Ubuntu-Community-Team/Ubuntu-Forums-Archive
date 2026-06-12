---
title: "Strange KDE crash"
date: 2005-08-14
forum: Desktop Environments
---

### Post by haaglin on 2005-08-14
Hi. 

I'm having some real strange crashes here, it says that kwin has crashed, and then my desktop switches to gnome?? all my apps are still up and running, but the "window decorations" are gone, and my desktop menu (when right click on the desktop) is the gnome one, same for the icons and wallpaper. but if i rightclick on the desktop and select open terminal from the gnome menu, i can write "kwin" and all is back to normal. My KDE desktop comes back, and so does the window decorations. Her is the error log i get when it crashes: 

btw, not sure if its important, but this happens when i'm in the Settings tab of the msn client Mercury, (java app)

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
[Thread debugging using libthread_db enabled]
[New Thread -1229961536 (LWP 8923)]
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
#4  0xb68b7ba9 in KWinInternal::Client::checkGroup ()
   from /usr/lib/libkdeinit_kwin.so
#5  0xb689a1ed in KWinInternal::Client::getWMHints ()
   from /usr/lib/libkdeinit_kwin.so
#6  0xb68aeaff in KWinInternal::Client::propertyNotifyEvent ()
   from /usr/lib/libkdeinit_kwin.so
#7  0xb68ae4bb in KWinInternal::Client::windowEvent ()
   from /usr/lib/libkdeinit_kwin.so
#8  0xb68ad949 in KWinInternal::Workspace::workspaceEvent ()
   from /usr/lib/libkdeinit_kwin.so
#9  0xb68a495e in KWinInternal::Application::x11EventFilter ()
   from /usr/lib/libkdeinit_kwin.so
#10 0xb7141128 in qt_set_x11_event_filter () from /usr/lib/libqt-mt.so.3
#11 0xbffff320 in ?? ()
#12 0x00400000 in ?? ()
#13 0xb764b670 in ?? () from /usr/lib/libqt-mt.so.3
#14 0xb764b670 in ?? () from /usr/lib/libqt-mt.so.3
#15 0x00000004 in ?? ()
#16 0xbffff1e8 in ?? ()
#17 0xb714ac9a in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#18 0x00000020 in ?? ()
#19 0x08168b08 in ?? ()
#20 0x00000000 in ?? ()
#21 0x081742c8 in ?? ()
#22 0x08181258 in ?? ()
#23 0x0818a320 in ?? ()
#24 0x081be880 in ?? ()
#25 0x00000000 in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000001 in ?? ()
#28 0x0815dce0 in ?? ()
#29 0xb6c42600 in in6addr_any () from /lib/tls/i686/cmov/libc.so.6
#30 0x00000000 in ?? ()
#31 0x081c05c8 in ?? ()
#32 0x081696f8 in ?? ()
#33 0x081745a0 in ?? ()
#34 0xb6c42601 in in6addr_any () from /lib/tls/i686/cmov/libc.so.6
#35 0xb68e67a4 in vtable for KWinInternal::Application ()
   from /usr/lib/libkdeinit_kwin.so
#36 0x08175fa0 in ?? ()
#37 0x08175e00 in ?? ()
#38 0x081998e0 in ?? ()
#39 0x080525d8 in vtable for QCString ()
#40 0x08175a60 in ?? ()
#41 0xbffff590 in ?? ()
#42 0x08175ad8 in ?? ()
#43 0x0815dd08 in ?? ()
#44 0x0000012d in ?? ()
#45 0x000000df in ?? ()
#46 0xbffff534 in ?? ()
#47 0x08273238 in ?? ()
#48 0x08055070 in ?? ()
#49 0xb6e81f01 in dlvsym () from /lib/tls/i686/cmov/libdl.so.2


```

---

### Post by manicka on 2005-08-14
It appears that is the java app, crashing your kde. 

Is mercury any better than gaim or kopete?

---

### Post by haaglin on 2005-08-14
[QUOTE=manicka]It appears that is the java app, crashing your kde. 

Is mercury any better than gaim or kopete?[/QUOTE]


Yes. i love it. is supports nugde (with shaking window), winks, webcam, video conference, skins, and lots of add-ons. [www.mercury.to](www.mercury.to)

i will ask for support from the Mercury people then. tnx.

---

