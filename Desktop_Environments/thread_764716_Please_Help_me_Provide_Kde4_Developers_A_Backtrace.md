---
title: "Please Help me Provide Kde4 Developers A Backtrace, need help in using gdb."
date: 2008-04-24
forum: Desktop Environments
---

### Post by interzoneuk on 2008-04-24
Hi.

I am trying to give the KDE developers a backtrace for a nasty (crashing) bug in kde4. - see bug :-

[http://bugs.kde.org/show_bug.cgi?id=157282](http://bugs.kde.org/show_bug.cgi?id=157282)

I am unable to use gdb to provide a backtrace, i'm nearly there but must be doing something wrong..



This is what i am doing

From console in kde (as root)

# ps aux | grep kwin (to find kwin pid)

# gdb kwin (pid)

- at this point i am unable to click on anything (as kwin is frozen..)

I turn logging on by

# set logging on

I then try to debug by using

# continue

- after using continue I can start to use kde (kwin) again, however no more output is created.

Can someone please point me in the right direction I must be doing something wrong, or even better provide example lines that they would use....


Cheers

i.e - here is (one of many) attempts

-------------------------------------------------------------

suse64:/home/morgan # cat /home/kde4user/gdb-kwin.txt
GNU gdb 6.6.50.20070726-cvs
Copyright © 2007 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB. Type "show warranty" for details.
This GDB was configured as "x86_64-suse-linux".
(gdb) attach 13394
Attaching to process 13394
Reading symbols from /usr/bin/kwin...Reading symbols from /usr/lib/debug/usr/bin/kwin.debug...done.
Using host libthread_db library "/lib64/libthread_db.so.1".
done.
Reading symbols from /usr/lib64/libkdeinit4_kwin.so...Reading symbols from /usr/lib/debug/usr/lib64/libkdeinit4_kwin.so.debug...done.
done.
Loaded symbols for /usr/lib64/libkdeinit4_kwin.so
Reading symbols from /usr/lib64/libSM.so.6...done.
Loaded symbols for /usr/lib64/libSM.so.6
Reading symbols from /usr/lib64/libICE.so.6...done.
Loaded symbols for /usr/lib64/libICE.so.6
Reading symbols from /usr/lib64/libX11.so.6...done.
Loaded symbols for /usr/lib64/libX11.so.6
Reading symbols from /usr/lib64/libXext.so.6...done.
Loaded symbols for /usr/lib64/libXext.so.6
Reading symbols from /usr/lib64/libXft.so.2...done.
Loaded symbols for /usr/lib64/libXft.so.2
Reading symbols from /usr/lib64/libXau.so.6...done.
Loaded symbols for /usr/lib64/libXau.so.6
Reading symbols from /usr/lib64/libXdmcp.so.6...done.
Loaded symbols for /usr/lib64/libXdmcp.so.6
Reading symbols from /usr/lib64/libXpm.so.4...done.
Loaded symbols for /usr/lib64/libXpm.so.4
Reading symbols from /usr/lib64/libXfixes.so.3...done.
Loaded symbols for /usr/lib64/libXfixes.so.3
Reading symbols from /usr/lib64/libXrender.so.1...done.
Loaded symbols for /usr/lib64/libXrender.so.1
Reading symbols from /usr/lib64/libkdecorations.so.4...Reading symbols from /usr/lib/debug/usr/lib64/libkdecorations.so.4.0.0.debug...done.
done.
Loaded symbols for /usr/lib64/libkdecorations.so.4
Reading symbols from /usr/lib64/libkwineffects.so.1...Reading symbols from /usr/lib/debug/usr/lib64/libkwineffects.so.1.0.0.debug...done.
done.
Loaded symbols for /usr/lib64/libkwineffects.so.1
Reading symbols from /usr/lib64/libQtSvg.so.4...done.
Loaded symbols for /usr/lib64/libQtSvg.so.4
Reading symbols from /usr/lib64/libkdecore.so.5...Reading symbols from /usr/lib/debug/usr/lib64/libkdecore.so.5.0.0.debug...done.
done.
Loaded symbols for /usr/lib64/libkdecore.so.5
Reading symbols from /usr/lib64/libQtCore.so.4...done.
Loaded symbols for /usr/lib64/libQtCore.so.4
Reading symbols from /lib64/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread 0x2b7009a99ec0 (LWP 13394)]
Loaded symbols for /lib64/libpthread.so.0
Reading symbols from /usr/lib64/libQtNetwork.so.4...done.
Loaded symbols for /usr/lib64/libQtNetwork.so.4
Reading symbols from /usr/lib64/libQtDBus.so.4...done.
Loaded symbols for /usr/lib64/libQtDBus.so.4
Reading symbols from /lib64/libz.so.1...done.
Loaded symbols for /lib64/libz.so.1
Reading symbols from /lib64/libbz2.so.1...done.
Loaded symbols for /lib64/libbz2.so.1
Reading symbols from /lib64/libresolv.so.2...done.
Loaded symbols for /lib64/libresolv.so.2
Reading symbols from /usr/lib64/libQtGui.so.4...done.
Loaded symbols for /usr/lib64/libQtGui.so.4
Reading symbols from /usr/lib64/libQtXml.so.4...done.
Loaded symbols for /usr/lib64/libQtXml.so.4
Reading symbols from /usr/lib64/libXtst.so.6...done.
Loaded symbols for /usr/lib64/libXtst.so.6
Reading symbols from /usr/lib64/libXcursor.so.1...done.
Loaded symbols for /usr/lib64/libXcursor.so.1
Reading symbols from /usr/lib64/libkdeui.so.5...Reading symbols from /usr/lib/debug/usr/lib64/libkdeui.so.5.0.0.debug...done.
done.
Loaded symbols for /usr/lib64/libkdeui.so.5
Reading symbols from /usr/lib64/libGL.so.1...done.
Loaded symbols for /usr/lib64/libGL.so.1
Reading symbols from /lib64/libdl.so.2...done.
Loaded symbols for /lib64/libdl.so.2
Reading symbols from /usr/lib64/libkwinnvidiahack.so.4...Reading symbols from /usr/lib/debug/usr/lib64/libkwinnvidiahack.so.4.0.0.debug...done.
done.
Loaded symbols for /usr/lib64/libkwinnvidiahack.so.4
Reading symbols from /usr/lib64/libXrandr.so.2...done.
Loaded symbols for /usr/lib64/libXrandr.so.2
Reading symbols from /usr/lib64/libXcomposite.so.1...done.
Loaded symbols for /usr/lib64/libXcomposite.so.1
Reading symbols from /usr/lib64/libXdamage.so.1...done.
Loaded symbols for /usr/lib64/libXdamage.so.1
Reading symbols from /usr/lib64/libstdc++.so.6...done.
Loaded symbols for /usr/lib64/libstdc++.so.6
Reading symbols from /lib64/libm.so.6...done.
Loaded symbols for /lib64/libm.so.6
Reading symbols from /lib64/libgcc_s.so.1...done.
Loaded symbols for /lib64/libgcc_s.so.1
Reading symbols from /lib64/libc.so.6...done.
Loaded symbols for /lib64/libc.so.6
Reading symbols from /usr/lib64/libxcb-xlib.so.0...done.
Loaded symbols for /usr/lib64/libxcb-xlib.so.0
Reading symbols from /usr/lib64/libxcb.so.1...done.
Loaded symbols for /usr/lib64/libxcb.so.1
Reading symbols from /usr/lib64/libfontconfig.so.1...done.
Loaded symbols for /usr/lib64/libfontconfig.so.1
Reading symbols from /usr/lib64/libfreetype.so.6...done.
Loaded symbols for /usr/lib64/libfreetype.so.6
Reading symbols from /usr/lib64/libpng12.so.0...done.
Loaded symbols for /usr/lib64/libpng12.so.0
Reading symbols from /usr/lib64/libXi.so.6...done.
Loaded symbols for /usr/lib64/libXi.so.6
Reading symbols from /usr/lib64/libXinerama.so.1...done.
Loaded symbols for /usr/lib64/libXinerama.so.1
Reading symbols from /usr/lib64/libgthread-2.0.so.0...done.
Loaded symbols for /usr/lib64/libgthread-2.0.so.0
Reading symbols from /lib64/librt.so.1...done.
Loaded symbols for /lib64/librt.so.1
Reading symbols from /usr/lib64/libglib-2.0.so.0...done.
Loaded symbols for /usr/lib64/libglib-2.0.so.0
Reading symbols from /lib64/ld-linux-x86-64.so.2...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /lib64/libdbus-1.so.3...done.
Loaded symbols for /lib64/libdbus-1.so.3
Reading symbols from /usr/lib64/libGLcore.so.1...done.
Loaded symbols for /usr/lib64/libGLcore.so.1
Reading symbols from /usr/lib64/tls/libnvidia-tls.so.1...done.
Loaded symbols for /usr/lib64/tls/libnvidia-tls.so.1
Reading symbols from /lib64/libexpat.so.1...done.
Loaded symbols for /lib64/libexpat.so.1
Reading symbols from /usr/lib64/libpcre.so.0...done.
Loaded symbols for /usr/lib64/libpcre.so.0
Reading symbols from /usr/lib64/gconv/UTF-16.so...done.
Loaded symbols for /usr/lib64/gconv/UTF-16.so
Reading symbols from /usr/lib64/kde4/plugins/styles/oxygen.so...done.
Loaded symbols for /usr/lib64/kde4/plugins/styles/oxygen.so
Reading symbols from /usr/lib64/kde4/kwin3_oxygen.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/kwin3_oxygen.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/kwin3_oxygen.so
Reading symbols from /usr/lib64/kde4/kwin4_effect_builtins.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/kwin4_effect_builtins.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/kwin4_effect_builtins.so
Reading symbols from /usr/lib64/qt4/plugins/imageformats/libqgif.so...done.
Loaded symbols for /usr/lib64/qt4/plugins/imageformats/libqgif.so
Reading symbols from /usr/lib64/qt4/plugins/imageformats/libqjpeg.so...done.
Loaded symbols for /usr/lib64/qt4/plugins/imageformats/libqjpeg.so
Reading symbols from /usr/lib64/libjpeg.so.62...done.
Loaded symbols for /usr/lib64/libjpeg.so.62
Reading symbols from /usr/lib64/qt4/plugins/imageformats/libqmng.so...done.
Loaded symbols for /usr/lib64/qt4/plugins/imageformats/libqmng.so
Reading symbols from /usr/lib64/libmng.so.1...done.
Loaded symbols for /usr/lib64/libmng.so.1
Reading symbols from /usr/lib64/liblcms.so.1...done.
Loaded symbols for /usr/lib64/liblcms.so.1
Reading symbols from /usr/lib64/qt4/plugins/imageformats/libqsvg.so...done.
Loaded symbols for /usr/lib64/qt4/plugins/imageformats/libqsvg.so
Reading symbols from /usr/lib64/qt4/plugins/imageformats/libqtiff.so...done.
Loaded symbols for /usr/lib64/qt4/plugins/imageformats/libqtiff.so
Reading symbols from /usr/lib64/libtiff.so.3...done.
Loaded symbols for /usr/lib64/libtiff.so.3
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_dds.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_dds.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_dds.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_eps.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_eps.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_eps.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_exr.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_exr.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_exr.so
Reading symbols from /usr/lib64/libImath.so.4...done.
Loaded symbols for /usr/lib64/libImath.so.4
Reading symbols from /usr/lib64/libIlmImf.so.4...done.
Loaded symbols for /usr/lib64/libIlmImf.so.4
Reading symbols from /usr/lib64/libIex.so.4...done.
Loaded symbols for /usr/lib64/libIex.so.4
Reading symbols from /usr/lib64/libHalf.so.4...done.
Loaded symbols for /usr/lib64/libHalf.so.4
Reading symbols from /usr/lib64/libIlmThread.so.4...done.
Loaded symbols for /usr/lib64/libIlmThread.so.4
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_ico.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_ico.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_ico.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_jp2.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_jp2.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_jp2.so
Reading symbols from /usr/lib64/libjasper.so.1...done.
Loaded symbols for /usr/lib64/libjasper.so.1
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_pcx.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_pcx.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_pcx.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_psd.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_psd.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_psd.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_rgb.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_rgb.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_rgb.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_tga.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_tga.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_tga.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_xcf.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_xcf.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_xcf.so
Reading symbols from /usr/lib64/kde4/plugins/imageformats/kimg_xview.so...Reading symbols from /usr/lib/debug/usr/lib64/kde4/plugins/imageformats/kimg_xview.so.debug...done.
done.
Loaded symbols for /usr/lib64/kde4/plugins/imageformats/kimg_xview.so
0x00002b7006f0d9af in poll () from /lib64/libc.so.6
(gdb) continue
Continuing.

--------------------------------

No more output is produced - even when it does crash X/kwin....

- also are you meant to use CTRL+C to get out of continue mode ?

---

### Post by interzoneuk on 2008-06-26
Can anyone help me do a backtrace..........

Bug still present in KDE 4.0.4 and KDE 4.1

All I need is someone to get me get the backtrace...........

---

### Post by GeneralZod on 2008-06-26
> **interzoneuk said:**
> Can anyone help me do a backtrace..........

Bug still present in KDE 4.0.4 and KDE 4.1

All I need is someone to get me get the backtrace...........

Assuming it is indeed a proper crash in kwin and not a hard-lock inside X or your drivers, then gdb *should*, if it is attached to the crashing process, go back into "interactive" mode where you can type commands in again, at which point you simply type 

```

bt

``` 

If it's not a proper crash (i.e. if X ends up in an infinite loop or something), or it's a driver problem, then it might not be possible to get a backtrace at all :/

You might want to try using GDB in a virtual terminal (e.g. by pressing CTRL+ALT+F1, logging in, attaching GDB to kwin, and then returning to your KDE session with CTRL+ALT+F7) - this way, assuming that CTRL+ALT+F1 is still functional at the time of the crash, you can easily switch back to GDB running in a VT without having to worry about the fact that your GUI no longer responds correctly.

Thanks for taking the time to delve into the issue you reported! :)

Edit:

Another strategy is not to run and attach GDB until *after* kwin has crashed - this should automatically pause kwin, assuming things have not gone too badly wrong, and generate a stack trace.  Remember - you'll need the debug symbols for kde if you want a proper backtrace - these are usually installable as separate packages, usually with names like kde<something>-dbg.  Good luck!

---

