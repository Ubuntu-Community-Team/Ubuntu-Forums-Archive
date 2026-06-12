---
title: "Kicker always crashes when KDE exists"
date: 2005-11-12
forum: Desktop Environments
---

### Post by xbaez on 2005-11-12
I'll appreciate some tips, KDE works great, but when I logoff, kicker crashes.

How can I tell KDE to stop showing me these messages when certain applications crash? This bugs me because if I want to shut down the computer automatically, I'm can't, the message is only closed by clicki on the "OK" Button.

**My kicker version is 4.3.4.3-oubuntu6 (breezy-updates)**

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1230989632 (LWP 9403)]
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
(no debugging symbols found)
[KCrash handler]
#4  0xb76510d9 in QGList::find () from /usr/lib/libqt-mt.so.3
#5  0xb78cee29 in KGlobal::registerStaticDeleter ()
   from /usr/lib/libkdecore.so.4
#6  0xb7bbaa85 in KDirWatch::self () from /usr/lib/libkio.so.4
#7  0xb7bbb1b2 in KDirListerCache::KDirListerCache ()
   from /usr/lib/libkio.so.4
#8  0xb7bbb26c in KDirListerCache::self () from /usr/lib/libkio.so.4
#9  0xb7bd07a3 in KDirLister::stop () from /usr/lib/libkio.so.4
#10 0xb7bd07e2 in KDirLister::~KDirLister () from /usr/lib/libkio.so.4
#11 0xb612c236 in SystemMenu::~SystemMenu ()
   from /usr/lib/kde3/kickermenu_systemmenu.so
#12 0xb79a641e in QPtrList<QObject>::deleteItem ()
   from /usr/lib/libkdecore.so.4
#13 0xb765212a in QGList::clear () from /usr/lib/libqt-mt.so.3
#14 0xb78fb7f9 in KLibrary::~KLibrary () from /usr/lib/libkdecore.so.4
#15 0xb78fbe09 in KLibLoader::close_pending () from /usr/lib/libkdecore.so.4
#16 0xb78fc231 in KLibLoader::~KLibLoader () from /usr/lib/libkdecore.so.4
#17 0xb78a9267 in KLibLoader::cleanUp () from /usr/lib/libkdecore.so.4
#18 0xb7947d65 in KApplication::~KApplication () from /usr/lib/libkdecore.so.4
#19 0xb7948121 in KUniqueApplication::~KUniqueApplication ()
   from /usr/lib/libkdecore.so.4
#20 0xb6779559 in Kicker::~Kicker () from /usr/lib/libkdeinit_kicker.so
#21 0xb6792115 in kdemain () from /usr/lib/libkdeinit_kicker.so
#22 0xb7fa7750 in kdeinitmain () from /usr/lib/kde3/kicker.so
#23 0x0804df8d in ?? ()
#24 0x00000001 in ?? ()
#25 0x080a3220 in ?? ()
#26 0x00000001 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000000 in ?? ()
#30 0x00001f80 in ?? ()
#31 0xb7d88334 in free () from /lib/tls/i686/cmov/libc.so.6
#32 0x0804e605 in ?? ()
#33 0x00000000 in ?? ()
#34 0x00000000 in ?? ()
#35 0x080a2f97 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x080507d2 in vtable for QPtrList<char> ()
#40 0x00000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x00000000 in ?? ()
#43 0x00000001 in ?? ()
#44 0x00000008 in ?? ()
#45 0x080a2f88 in ?? ()
#46 0x080a2f8c in ?? ()
#47 0x080a2f93 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0x080a2f97 in ?? ()
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x080507d2 in vtable for QPtrList<char> ()
#54 0x080a2f9b in ?? ()
#55 0x080a2f97 in ?? ()
#56 0x00000000 in ?? ()
#57 0x00000000 in ?? ()
#58 0x08051400 in vtable for QCString ()
#59 0x0805a478 in ?? ()
#60 0x08051400 in vtable for QCString ()
#61 0x0805a468 in ?? ()
#62 0x0077b858 in ?? ()
#63 0x80cd0000 in ?? ()
#64 0x0000000c in ?? ()
#65 0x00000013 in ?? ()
#66 0x00000000 in ?? ()
#67 0xbf9dee9c in ?? ()
#68 0x00000000 in ?? ()
#69 0x0000247d in ?? ()
#70 0x0000247d in ?? ()
#71 0xbf9defa8 in ?? ()
#72 0x0804ebec in ?? ()
#73 0x0000000a in ?? ()
#74 0xbf9dee9c in ?? ()
#75 0xbf9dee1c in ?? ()
#76 0xbf9ded9c in ?? ()
#77 0x00000000 in ?? ()
#78 0xb7e50900 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#79 0x0806a0a0 in ?? ()
#80 0xbf9deda8 in ?? ()
#81 0xb7d882ca in free () from /lib/tls/i686/cmov/libc.so.6

---

### Post by daller on 2005-11-15
And easy fix would be to upgrade the KDE 3.5 Release Candidate 1 (find it on [www.kubuntu.org](www.kubuntu.org))

...Elseway, I have no idea...

---

### Post by xbaez on 2005-11-16
No way, I HAVE KDE 3.5 RC1 and it doesn't works
I was even considering the idea of reinstalling KDE, since I burned my own CDs with .debs (XB DVD Repository in .disk/info), took it to my house, and then I did a fresh copy of (K)Ubuntu

Gnome and KDE work fine there, without that problem.

Amarok 1.5 was giving me an error, so I downgraded to Amarok 1.3

I don't know how but I found out the reason of this problem. I deleted my $HOME directory, created a new one, to see excactly what was causing this.

First, kicker worked ok. Then I modifyied kicker, added some applets, still worked good. Third attempt, I launched amarok, and it crashed!!!

I know that KDE uses arts, so I used the artsd engine (was on xine, tried gstreamer as well) and it works!

Now I can logoff, and kicker doesn't produces an error

To me this is important in case I want to leave my computer on and shut it down with a crontab.

When kicker failed, you HAD to click on the "ok" button of the error message if you wanted to continue shutting down the OS 

;)

---

