---
title: "New install KDE errors"
date: 2005-06-03
forum: Desktop Environments
---

### Post by zootreeves on 2005-06-03
I've been using ubuntu for a while and i thought i'd try kubuntu instead. But there is a number of problems:
 1. I have installed ndiswrapper but modprobe does not load it on boot even though i have done "sudo ndiswrapper -m"

2. KDE always seems to forget stuff like i setup kwallet but after a reboot it asks me to set it up again.

3. When i try to update "network settings" i click on admistration mode and most of the time even though the password is right it does not let me administer anything. I have to run the command "mv /home/me/.kde /home/me/.kde-old" and then reboot in order for it to work.

5. I always seem to get this error:

```
[SIZE=1](no debugging symbols found)
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
[Thread debugging using libthread_db enabled]
[New Thread -1229691488 (LWP 8924)]
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
#4  0x00000000 in ?? ()
#5  0xb69a75b0 in KCModuleProxy::~KCModuleProxy ()
   from /usr/lib/libkutils.so.1
#6  0xb7415342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#7  0xb770d4ef in QFrame::~QFrame () from /usr/lib/libqt-mt.so.3
#8  0xb7415342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#9  0xb6f644a3 in KJanusWidget::~KJanusWidget () from /usr/lib/libkdeui.so.4
#10 0xb7415342 in QWidget::~QWidget () from /usr/lib/libqt-mt.so.3
#11 0xb7560eaa in QDialog::~QDialog () from /usr/lib/libqt-mt.so.3
#12 0xb6f5d2da in KDialogBase::~KDialogBase () from /usr/lib/libkdeui.so.4
#13 0xb699a66a in KCMultiDialog::~KCMultiDialog ()
   from /usr/lib/libkutils.so.1
#14 0xb69d102a in KCMShellMultiDialog::~KCMShellMultiDialog ()
   from /usr/lib/libkdeinit_kcmshell.so
#15 0xb69cfab5 in kdemain () from /usr/lib/libkdeinit_kcmshell.so
#16 0xb7fe7776 in kdeinitmain () from /usr/lib/kde3/kcmshell.so
#17 0x0804cb6e in ?? ()
#18 0x00000002 in ?? ()
#19 0x08136138 in ?? ()
#20 0x00000001 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000000 in ?? ()
#23 0x0000007b in ?? ()
#24 0x00001f80 in ?? ()
#25 0x0000ffff in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000000 in ?? ()
#30 0x00000000 in ?? ()
#31 0x00000000 in ?? ()
#32 0x00000000 in ?? ()
#33 0x00000000 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x08135e20 in ?? ()
#43 0x00000000 in ?? ()
#44 0x00000000 in ?? ()
#45 0x00000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x00000000 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0xb7805ee0 in vtable for QGArray () from /usr/lib/libqt-mt.so.3
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x00000000 in ?? ()
#54 0x00000000 in ?? ()
#55 0x80000000 in ?? ()
#56 0x00004010 in ?? ()
#57 0x00000000 in ?? ()
#58 0x0805a4c0 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000010 in ?? ()
#61 0xb7eaf9e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#62 0xb7eaf038 in ?? () from /lib/tls/i686/cmov/libc.so.6
#63 0xb7eaf9e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#64 0x00000001 in ?? ()
#65 0xbffff748 in ?? ()
#66 0xb7df4b0b in malloc () from /lib/tls/i686/cmov/libc.so.6
#67 0x0804e046 in ?? ()
#68 0x00000002 in ?? ()
#69 0x080a7f44 in ?? ()
#70 0x080a7f64 in ?? ()
#71 0x00000000 in ?? ()
#72 0x00000001 in ?? ()
#73 0x080a7f75 in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0x00000000 in ?? ()
#77 0x080a7f79 in ?? ()
#78 0x00000000 in ?? ()
#79 0x00000000 in ?? ()
#80 0x00000000 in ?? ()
#81 0x00000000 in ?? ()
#82 0x00000000 in ?? ()
#83 0x00000000 in ?? ()
#84 0x00000000 in ?? ()
#85 0x080a7f79 in ?? ()
#86 0x00000000 in ?? ()
#87 0x00000000 in ?? ()
#88 0x080a7f68 in ?? ()
#89 0x00000001 in ?? ()
#90 0x00000000 in ?? ()
#91 0x080a7f4d in ?? ()
#92 0x080a7f44 in ?? ()
#93 0x00000002 in ?? ()
#94 0x080a7f40 in ?? ()
#95 0x000022db in ?? ()
#96 0x00000004 in ?? ()
#97 0x00000004 in ?? ()
#98 0x0000000a in ?? ()
#99 0x00000062 in ?? ()
#100 0x080513d8 in vtable for QCString ()
#101 0x0805a4c8 in ?? ()
#102 0x00000000 in ?? ()
#103 0x00000000 in ?? ()
#104 0x080513d8 in vtable for QCString ()
#105 0x0805a4b8 in ?? ()
#106 0x80cd0000 in ?? ()
#107 0x00000000 in ?? ()
#108 0xbffffb58 in ?? ()
#109 0xbffffa40 in ?? ()
#110 0xbffffac0 in ?? ()
#111 0x00000001 in ?? ()
#112 0xbffffa40 in ?? ()
#113 0x00001cf5 in ?? ()
#114 0xbffffb58 in ?? ()
#115 0x0804e591 in ?? ()
#116 0x00000008 in ?? ()
#117 0xbffffac0 in ?? ()
#118 0xbffffa40 in ?? ()
#119 0xbffff9c0 in ?? ()
#120 0x00000000 in ?? ()
#121 0xbffff960 in ?? ()
#122 0xbffff8c8 in ?? ()
#123 0xb7f6fd13 in operator delete () from /usr/lib/libstdc++.so.5[/SIZE]
``` 

I don't know if it is related to any of the problems but when i first started kubuntu sudo would not work I had to add "me      ALL=(ALL) ALL" to /etc/sudoers.

---

### Post by dejitarob on 2005-06-03
[QUOTE=zootreeves]I've been using ubuntu for a while and i thought i'd try kubuntu instead. But there is a number of problems:
 1. I have installed ndiswrapper but modprobe does not load it on boot even though i have done "sudo ndiswrapper -m"[/quote]add it in /etc/modules

[QUOTE=zootreeves]5. I always seem to get this error:

[CODE][SIZE=1](no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[/QUOTE]Is this in konqueror? I used to get this a lot too. Turning off the preview bar on the left seemed to fix it.

---

### Post by zootreeves on 2005-06-04
Ok i added ndiswrapper to /etc/modules and it fixed it thanks!

To fix the other error tho I had to completely remove kde (including config) and then reinstall evrything and at the same time install gnome as well and that seemed to make it more stable.

---

### Post by zootreeves on 2005-06-04
Just rebooted and the problems with admistrator mode are back i cannot enter it again. 

Also Amorak has started blacking out every other song - see screenshot. I changed the fonts and theme and both amorak and juk do it. Even if i put it back to the original theme.

---

### Post by deadlands on 2005-06-04
[QUOTE=zootreeves]Just rebooted and the problems with admistrator mode are back i cannot enter it again. 

Also Amorak has started blacking out every other song - see screenshot. I changed the fonts and theme and both amorak and juk do it. Even if i put it back to the original theme.[/QUOTE]

It's not the fonts or theme that causes that. Goto Kcontrol -> Appearances & Themes --> Colors and then pulls down the 'Widget Color' Menu to 'Alternate Background in Lists' and change the color to a lighter color.

Hope that helps!

---

### Post by zootreeves on 2005-06-04
Thanks thats fixed it

---

### Post by dejitarob on 2005-06-05
Your problem seems to stem from those Avril Lavigne mp3s. Remove them and it should work.

---

