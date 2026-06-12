---
title: "Openoffice crashes when quitting it"
date: 2008-06-11
forum: Desktop Environments
---

### Post by LK_gandalf_ on 2008-06-11
Hi. I  have kubuntu Hardy 64 bit, and openoffice as default.

When I close the program, I recevice a crash report. I've tried this from the console, to have some infos for you:

I launch it...
```

~$ openoffice
javaldx: Could not find a Java Runtime Environment!

```

and now I close it:
```

~$ KCrash: Application 'soffice.bin' crashing...
XIO:  fatal IO error 9 (Descrittore di file errato) on X server ":0.0"
      after 82 requests (82 known processed) with 0 events remaining.

```

How can I fix it?
thanks
[/code]

---

### Post by LK_gandalf_ on 2008-06-14
up

new info from the crash handler gui:
```

[KCrash handler]
#5  0x00007fe90d20096d in _XFreeExtData () from /usr/lib/libX11.so.6
#6  0x00007fe90d20d570 in _XFreeDisplayStructure () from /usr/lib/libX11.so.6
#7  0x00007fe90d1f990f in XCloseDisplay () from /usr/lib/libX11.so.6
#8  0x00007fe9037d9c8a in qt_cleanup () from /usr/lib/libqt-mt.so.3
#9  0x00007fe903855e05 in QApplication::~QApplication ()
   from /usr/lib/libqt-mt.so.3
#10 0x00007fe904b4ac91 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#11 0x00007fe904b4a303 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#12 0x00007fe90323d9da in X11SalData::DeleteDisplay ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#13 0x00007fe90323dc44 in X11SalData::~X11SalData ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#14 0x00007fe904b4a293 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#15 0x00007fe90324ca9e in X11SalInstance::~X11SalInstance ()
   from /usr/lib/openoffice/program/libvclplug_gen680lx.so
#16 0x00007fe904b50683 in ?? ()
   from /usr/lib/openoffice/program/libvclplug_kde680lx.so
#17 0x00007fe910b34676 in ?? ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#18 0x00007fe9108f70be in DeInitVCL ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#19 0x00007fe9108f7895 in ?? ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#20 0x00007fe9108f79d5 in SVMain ()
   from /usr/lib/openoffice/program/libvcl680lx.so
#21 0x00000000004267dd in main ()

```

---

### Post by LK_gandalf_ on 2008-06-26
up

---

