---
title: "Kicker Crash(3.5)..possible to change kicker arguments?"
date: 2005-12-07
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-12-07
Hi

Since latest KDE I have the nice problem of kicker crashing on me upon shutdown. Sometimes It won't even let me see the crash dialog so that I need to hardshutdown my laptop:(. I'll append the debig msg below if you can solve it it would be nice. But in the meantime I would like to have kicker startup with "kicker --nocrashhandler" so that the crash dialog won't appear when I shitdown.

Is this possible. I've tried searching for some file where kicker might start but maybe it is hardcoded into some binary.

help!

*this is the crash msg:*
```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1208846656 (LWP 7114)]
[KCrash handler]
#4  0x082c0490 in ?? ()
#5  0x439658ae in _X11TransWrite () from /usr/lib/libX11.so.6
#6  0x4396a26b in _XError () from /usr/lib/libX11.so.6
#7  0x43948341 in XFlush () from /usr/lib/libX11.so.6
#8  0xb7cb284d in _XimFilterWaitEvent ()
   from /usr/lib/X11/locale/common/ximcp.so.2
#9  0xb7cb1951 in _XimFlush () from /usr/lib/X11/locale/common/ximcp.so.2
#10 0xb7c9ff19 in _XimUnregisterServerFilter ()
   from /usr/lib/X11/locale/common/ximcp.so.2
#11 0x43975296 in XDestroyIC () from /usr/lib/libX11.so.6
#12 0x43f59d74 in QInputContext::~QInputContext () from /usr/lib/libqt-mt.so.3
#13 0x43f7f4ac in QWidget::destroyInputContext () from /usr/lib/libqt-mt.so.3
#14 0x43f7f4eb in QWidget::deleteTLSysExtra () from /usr/lib/libqt-mt.so.3
#15 0x4405067e in QWidget::deleteExtra () from /usr/lib/libqt-mt.so.3
#16 0x440534cb in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#17 0x440d8a2f in QFrame::~QFrame () from /usr/lib/libqt-mt.so.3
#18 0x4413c95d in QPopupMenu::~QPopupMenu () from /usr/lib/libqt-mt.so.3
#19 0x449ebadf in KPopupMenu::~KPopupMenu () from /usr/lib/libkdeui.so.4
#20 0x449ed0b1 in KPanelMenu::~KPanelMenu () from /usr/lib/libkdeui.so.4
#21 0x450b1c79 in PanelServiceMenu::~PanelServiceMenu ()
   from /usr/lib/libkdeinit_kicker.so
#22 0x450a4d0f in PanelServiceMenu::clearSubmenus ()
   from /usr/lib/libkdeinit_kicker.so
#23 0x450b1b7d in PanelServiceMenu::~PanelServiceMenu ()
   from /usr/lib/libkdeinit_kicker.so
#24 0x450a4d0f in PanelServiceMenu::clearSubmenus ()
   from /usr/lib/libkdeinit_kicker.so
#25 0x450b0e0d in PanelServiceMenu::~PanelServiceMenu ()
   from /usr/lib/libkdeinit_kicker.so
#26 0x450b102f in PanelKMenu::~PanelKMenu ()
   from /usr/lib/libkdeinit_kicker.so
#27 0x45063d89 in MenuManager::~MenuManager ()
   from /usr/lib/libkdeinit_kicker.so
#28 0x44018f02 in QObject::~QObject () from /usr/lib/libqt-mt.so.3
#29 0x43fb70dc in QApplication::~QApplication () from /usr/lib/libqt-mt.so.3
#30 0x44726ca9 in KApplication::~KApplication () from /usr/lib/libkdecore.so.4
#31 0x44726e8f in KUniqueApplication::~KUniqueApplication ()
   from /usr/lib/libkdecore.so.4
#32 0x45068013 in Kicker::~Kicker () from /usr/lib/libkdeinit_kicker.so
#33 0x4507d897 in kdemain () from /usr/lib/libkdeinit_kicker.so
#34 0x437caea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#35 0x080483d1 in ?? ()
```

---

### Post by EPOX123 on 2005-12-07
err doesn't any one have a fix for this. always have to push ok or x button...

We cant be the only ones with this problem. I have a fresh install...

:KSkubuntu x86_64:KS

---

### Post by NeoChaosX on 2005-12-07
Fresh install here, too, and kicker's always dying on me when I shut down or reboot. I just log out and shut down from kdm, but yeah, that bug - even if it is during a trivial time like shutting down - does not look good.

---

### Post by Sokraates on 2005-12-07
[QUOTE=EPOX123]err doesn't any one have a fix for this. always have to push ok or x button...

We cant be the only ones with this problem. I have a fresh install...

:KSkubuntu x86_64:KS[/QUOTE]

I'm with you and I've had this problem since Hoary and KDE 3.4.1 (or was it 3.4.2???). Still I've never found out why it happens and how to avoid it.

---

### Post by lithium- on 2005-12-07
I also have this problem with the kicker in kde 3.5.
I had this problem with the normal kde 3.4.3 in breezy.
I've done a fresh install with the kubuntu cd.

A fix would be welcome.

---

### Post by GoldBuggie on 2005-12-07
While I do hope that my system will randomly get to a non crashing kicker, after readingsome things on kde.org I'm not so sure this will happen.

[http://bugs.kde.org/show_bug.cgi?id=109548](http://bugs.kde.org/show_bug.cgi?id=109548)

It seems that some previous bug about ctashing kicker got a patch , and was present on some versionm but the patch was somehow removed from 3.5 or something and well...The kicker developer seems to have alot of bugs about kicker which practically goes back to the same problem. He mentiones that 3.5.1 will have the crashing fixed. I'm only wondering if this version will make it to the market and when?

In the meantime if someone still knows how to startup kicker with arguments on kde startup then please tell me.

---

### Post by shakin on 2005-12-07
To add an argument you can try editing /usr/share/autostart/panel.desktop and adding the argument to the line that says 'Exec=kicker'.

If that doesn't work you can create an alias like "alias kicker='kicker --nocrashhandler'" so running kicker will always run it with the nocrashhandler option until you remove the alias.

---

### Post by EPOX123 on 2005-12-07
edited /usr/share/autostart/panel.desktop
changed Exec=kicker
to
Exec=kicker  --nocrashhandler

works for me :) thank you

But remember this is just a hack not a fix so if any one gets some info let us know :)

by the way don't reinstall kicker doesn't do jack.

---

### Post by GoldBuggie on 2005-12-07
Aaaah...thank you **shakin**. That information is highly appreciated. I'm so glad that I found that argument for kicker. Now I can shutdown my laptop and carry it in my case without worrying of overheating. :D

**NOTE!** As mentioned above this is only a hack **NOT** a fix. So when updating your kde system please remove this to see if it is fixed. But in the meantime enjoy its benefits.

---

### Post by existenz on 2005-12-12
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231955744 (LWP 8245)]
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
#4  0xb757c18d in QGList::findRef () from /usr/lib/libqt-mt.so.3
#5  0xb757d720 in QGList::removeRef () from /usr/lib/libqt-mt.so.3
#6  0xb7b1e0a8 in KDirListerCache::forgetDirs () from /usr/lib/libkio.so.4
#7  0xb7b1ea43 in KDirListerCache::forgetDirs () from /usr/lib/libkio.so.4
#8  0xb7b1ef3a in KDirLister::~KDirLister () from /usr/lib/libkio.so.4
#9  0xb6164214 in SystemMenu::~SystemMenu ()
   from /usr/lib/kde3/kickermenu_systemmenu.so
#10 0xb78e149f in QPtrList<QObject>::deleteItem ()
   from /usr/lib/libkdecore.so.4
#11 0xb757d12a in QGList::clear () from /usr/lib/libqt-mt.so.3
#12 0xb782f1a1 in KLibrary::~KLibrary () from /usr/lib/libkdecore.so.4
#13 0xb782f7ec in KLibLoader::close_pending () from /usr/lib/libkdecore.so.4
#14 0xb782fc0b in KLibLoader::~KLibLoader () from /usr/lib/libkdecore.so.4
#15 0xb77d94e6 in KLibLoader::cleanUp () from /usr/lib/libkdecore.so.4
#16 0xb78797c4 in KApplication::~KApplication () from /usr/lib/libkdecore.so.4
#17 0xb7879c0f in KUniqueApplication::~KUniqueApplication ()
   from /usr/lib/libkdecore.so.4
#18 0xb6732013 in Kicker::~Kicker () from /usr/lib/libkdeinit_kicker.so
#19 0xb6747897 in kdemain () from /usr/lib/libkdeinit_kicker.so
#20 0xb7f15540 in kdeinitmain () from /usr/lib/kde3/kicker.so
#21 0x0804df98 in ?? ()
#22 0x00000001 in ?? ()
#23 0x080b7848 in ?? ()
#24 0xbff2be08 in ?? ()
#25 0x0804dfdc in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0xb7ce6334 in free () from /lib/tls/i686/cmov/libc.so.6
#30 0x0804e57a in ?? ()
#31 0x00000000 in ?? ()
#32 0x00000000 in ?? ()
#33 0x08133a17 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x080505b2 in vtable for QPtrList<char> ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x00000001 in ?? ()
#43 0x00000008 in ?? ()
#44 0x08133a08 in ?? ()
#45 0x08133a0c in ?? ()
#46 0x08133a13 in ?? ()
#47 0x00000000 in ?? ()
#48 0x00000000 in ?? ()
#49 0x08133a17 in ?? ()
#50 0x00000000 in ?? ()
#51 0x00000000 in ?? ()
#52 0x080505b2 in vtable for QPtrList<char> ()
#53 0x08133a17 in ?? ()
#54 0x00000000 in ?? ()
#55 0xbff2c0c8 in ?? ()
#56 0x08051400 in vtable for QCString ()
#57 0x0805a5c8 in ?? ()
#58 0x08051400 in vtable for QCString ()
#59 0x0805a5b8 in ?? ()
#60 0xbff2bebc in ?? ()
#61 0xbff2bf3c in ?? ()
#62 0x0000000c in ?? ()
#63 0x00000013 in ?? ()
#64 0x00000000 in ?? ()
#65 0xbff2bf3c in ?? ()
#66 0x00000000 in ?? ()
#67 0xbff2bebc in ?? ()
#68 0xbff2bf3c in ?? ()
#69 0xbff2c0c8 in ?? ()
#70 0x0804eb6c in ?? ()
#71 0xffffffff in ?? ()
#72 0x00000000 in ?? ()
#73 0x0000000a in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0x00000000 in ?? ()
#77 0x00000000 in ?? ()
#78 0x00000000 in ?? ()
#79 0x00000000 in ?? ()
#80 0x00000000 in ?? ()
#81 0x00000000 in ?? ()
#82 0x00000000 in ?? ()
#83 0x00000000 in ?? ()
#84 0x00000000 in ?? ()
#85 0x00000000 in ?? ()
#86 0x00000000 in ?? ()
#87 0x00000000 in ?? ()
#88 0x00000000 in ?? ()
#89 0x00000000 in ?? ()
#90 0x00000000 in ?? ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x00000000 in ?? ()
#95 0x00000000 in ?? ()
#96 0x00000000 in ?? ()
#97 0x00000000 in ?? ()
#98 0x00000000 in ?? ()
#99 0x00000000 in ?? ()
#100 0x00000000 in ?? ()
#101 0x00000000 in ?? ()
#102 0x00000000 in ?? ()
#103 0x00000000 in ?? ()
#104 0x00000000 in ?? ()
#105 0x00000000 in ?? ()
#106 0x00000000 in ?? ()
#107 0x00000000 in ?? ()
#108 0x00000000 in ?? ()
#109 0x00000000 in ?? ()
#110 0x00000000 in ?? ()
#111 0x00000000 in ?? ()
#112 0x00000000 in ?? ()
#113 0x00000000 in ?? ()
#114 0x00000000 in ?? ()
#115 0x00000000 in ?? ()
#116 0x00000000 in ?? ()
#117 0x00000000 in ?? ()
#118 0x00000000 in ?? ()
#119 0x00000000 in ?? ()
#120 0x00000000 in ?? ()
#121 0x00000000 in ?? ()
#122 0x00000000 in ?? ()
#123 0x00000000 in ?? ()
#124 0x00000000 in ?? ()
#125 0x00000000 in ?? ()
#126 0x00000000 in ?? ()
#127 0x00000000 in ?? ()
#128 0x00000000 in ?? ()
#129 0x00000000 in ?? ()
#130 0x00000000 in ?? ()
#131 0x00000000 in ?? ()
#132 0x00000000 in ?? ()
#133 0x00000000 in ?? ()
#134 0x00000000 in ?? ()
#135 0x00000000 in ?? ()
#136 0x00000000 in ?? ()
#137 0x00000000 in ?? ()
#138 0x00000100 in ?? ()
#139 0x00000000 in ?? ()
#140 0x00000000 in ?? ()
#141 0x00000000 in ?? ()
#142 0x00000000 in ?? ()
#143 0x00000000 in ?? ()
#144 0x00000000 in ?? ()
#145 0x00000000 in ?? ()
#146 0x00000000 in ?? ()
#147 0x00000000 in ?? ()
#148 0x00000000 in ?? ()
#149 0x00000000 in ?? ()
#150 0x00000000 in ?? ()
#151 0x00000000 in ?? ()
#152 0x00000000 in ?? ()
#153 0x00000000 in ?? ()
#154 0x00000000 in ?? ()
#155 0x00000000 in ?? ()
#156 0x00000000 in ?? ()
#157 0x00000000 in ?? ()
#158 0x00000000 in ?? ()
#159 0x00000000 in ?? ()
#160 0x00000000 in ?? ()
#161 0x00000000 in ?? ()
#162 0x00000000 in ?? ()
#163 0x00000000 in ?? ()
#164 0x00000000 in ?? ()
#165 0x00000000 in ?? ()
#166 0x00000000 in ?? ()
#167 0x00000000 in ?? ()
#168 0x00000000 in ?? ()
#169 0x00000000 in ?? ()
#170 0x00002032 in ?? ()
#171 0x00000000 in ?? ()
#172 0x00000000 in ?? ()
#173 0x00000000 in ?? ()
#174 0x00002017 in ?? ()
#175 0x00000000 in ?? ()
#176 0x00000000 in ?? ()
#177 0x0805da40 in ?? ()
#178 0x00000000 in ?? ()
#179 0x00000002 in ?? ()
#180 0x00000000 in ?? ()
#181 0x00000000 in ?? ()
#182 0x00720073 in ?? ()
#183 0x006c002f in ?? ()
#184 0x0063006f in ?? ()
#185 0x006c0061 in ?? ()
#186 0x0062002f in ?? ()
#187 0x006e0069 in ?? ()
#188 0xb7da2d80 in in6addr_any () from /lib/tls/i686/cmov/libc.so.6
#189 0x00730075 in ?? ()
#190 0x002f0072 in ?? ()
#191 0x00620073 in ?? ()
#192 0x006e0069 in ?? ()
#193 0x002f003a in ?? ()
#194 0x00730075 in ?? ()
#195 0xb7dad0dc in ?? () from /lib/tls/i686/cmov/libc.so.6
#196 0xb7dae900 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#197 0x0805a5b8 in ?? ()
#198 0x00000003 in ?? ()
#199 0x00000008 in ?? ()
#200 0x00000002 in ?? ()
#201 0x00f2c268 in ?? ()
#202 0x00000002 in ?? ()
#203 0x0805a5d8 in ?? ()
#204 0x0805da40 in ?? ()
#205 0xbff2c268 in ?? ()
#206 0x0804fa61 in ?? ()
#207 0x00000004 in ?? ()
#208 0xbff2c25b in ?? ()
#209 0x00000001 in ?? ()
#210 0xbff2dfea in ?? ()
#211 0xb7ce8391 in malloc () from /lib/tls/i686/cmov/libc.so.6

```


same here

---

