---
title: "GKSU crashing Compiz"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by denham2010 on 2007-12-07
Hi,

After some recent updates to Gutsy, there now appears to be a conflict with GKSU and Compiz.

I find whenever I open Synaptic, Compiz crashes as soon as I have input my password.

To test my theory, in a terminal I opened several apps with GKSU...ie GEDIT, NAUTILUS etc. and every time, after entering my password, Compiz would crash.

I have inserted my Compiz output below. Any help in fixing this would be great, otherwise I am going to have to sudo any app from the cli to access it as root.

Thanks.

Compiz Crash Output:
```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 20763
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libSM.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213225296 (LWP 20763)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /home/denham2010/.compiz/plugins/libfreewins.so...done.
Loaded symbols for /home/denham2010/.compiz/plugins/libfreewins.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libshift.so...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libshowdesktop.so...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libsvg.so...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libdbus.so...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libextrawm.so...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libwidget.so...done.
Loaded symbols for /usr/lib/compiz/libwidget.so
Reading symbols from /usr/lib/compiz/libregex.so...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libvideo.so...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libwobbly.so...done.
Loaded symbols for /usr/lib/compUndefined command: "-e".  Try "help".
iz/libwobbly.so
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libanimation.so...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libfade.so...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libtrailfocus.so...done.
Loaded symbols for /usr/lib/compiz/libtrailfocus.so
Reading symbols from /usr/lib/compiz/libgroup.so...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /usr/lib/compiz/libscale.so...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /home/denham2010/.compiz/plugins/libscreensaver.so...done.
Loaded symbols for /home/denham2010/.compiz/plugins/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...done.
Loaded symbols for /usr/lib/libXss.so.1
Reading symbols from /usr/lib/compiz/libexpo.so...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libgconf.so...done.
Loaded symbols for /usr/lib/compiz/libgconf.so
Reading symbols from /usr/lib/compiz/libannotate.so...done.
Loaded symbols for /usr/lib/compiz/libannotate.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libclone.so...done.
Loaded symbols for /usr/lib/compiz/libclone.so
Reading symbols from /usr/lib/compiz/libswitcher.so...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213225296 (LWP 20763)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cdf6b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c84b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7aa5962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe78e98 in ?? ()
#5  0xb7aa5a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe7a8cd in ?? ()
#7  0x0000511b in ?? ()
#8  0x0000511b in ?? ()
#9  0x0000511b in ?? ()
#10 0xbfe78fa8 in ?? ()
#11 0xb79d3189 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#12 <signal handler called>
#13 0xb73cd596 in groupHandleChanges () from /usr/lib/compiz/libgroup.so
#14 0xb73c528c in groupPreparePaintScreen () from /usr/lib/compiz/libgroup.so
#15 0xb755dc60 in ?? () from /usr/lib/compiz/libscale.so
#16 0x0815d5c8 in ?? ()
#17 0x00000054 in ?? ()
#18 0x00000004 in ?? ()
#19 0xb78c1990 in ?? () from /usr/lib/compiz/libshowdesktop.so
#20 0x082d3b90 in ?? ()
#21 0x082760b0 in ?? ()
#22 0x00000094 in ?? ()
#23 0xb7c799de in ?? () from /lib/tls/i686/cmov/libc.so.6
#24 0xb73a7f81 in ScreenWrapper::preparePaintScreen (this=0x864a5b8, 
    msSinceLastPaint=84) at wrapper.cpp:35
No locals.
#25 0xb73a87d1 in ScreenEffect::preparePaintScreen (this=0x864a5b8, 
    msSinceLastPaint=84) at effect.cpp:56
        sd = (ScreenSaverDisplay *) 0x86471b8
#26 0xb73a8d87 in screenSaverPreparePaintScreen (s=0x815d5c8, 
    msSinceLastPaint=84) at screensaver.cpp:157
        ss = (ScreenSaverScreen *) 0x868aa70
#27 0xb739d2c6 in ?? () from /usr/lib/compiz/libexpo.so
#28 0x0815d5c8 in ?? ()
#29 0x00000054 in ?? ()
#30 0x3e2c0831 in ?? ()
#31 0xb738f644 in ?? () from /usr/lib/compiz/libclone.so
#32 0x0000002d in ?? ()
#33 0x00000054 in ?? ()
#34 0xbfe797d8 in ?? ()
#35 0xb738db50 in ?? () from /usr/lib/compiz/libclone.so
#36 0x0815d5c8 in ?? ()
#37 0x00000054 in ?? ()
#38 0x00000020 in ?? ()
#39 0xb7b569a1 in ?? () from /usr/lib/libXext.so.6
#40 0x08082c18 in ?? ()
#41 0xbfe797e0 in ?? ()
#42 0xbfe79788 in ?? ()
#43 0xb7b98b79 in _XRead () from /usr/lib/libX11.so.6
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cdf6b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c84b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7aa5962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe78e98 in ?? ()
#5  0xb7aa5a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe7a8cd in ?? ()
#7  0x0000511b in ?? ()
#8  0x0000511b in ?? ()
#9  0x0000511b in ?? ()
#10 0xbfe78fa8 in ?? ()
#11 0xb79d3189 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#12 <signal handler called>
#13 0xb73cd596 in groupHandleChanges () from /usr/lib/compiz/libgroup.so
#14 0xb73c528c in groupPreparePaintScreen () from /usr/lib/compiz/libgroup.so
#15 0xb755dc60 in ?? () from /usr/lib/compiz/libscale.so
#16 0x0815d5c8 in ?? ()
#17 0x00000054 in ?? ()
#18 0x00000004 in ?? ()
#19 0xb78c1990 in ?? () from /usr/lib/compiz/libshowdesktop.so
#20 0x082d3b90 in ?? ()
#21 0x082760b0 in ?? ()
#22 0x00000094 in ?? ()
#23 0xb7c799de in ?? () from /lib/tls/i686/cmov/libc.so.6
#24 0xb73a7f81 in ScreenWrapper::preparePaintScreen (this=0x864a5b8, 
    msSinceLastPaint=84) at wrapper.cpp:35
#25 0xb73a87d1 in ScreenEffect::preparePaintScreen (this=0x864a5b8, 
    msSinceLastPaint=84) at effect.cpp:56
#26 0xb73a8d87 in screenSaverPreparePaintScreen (s=0x815d5c8, 
    msSinceLastPaint=84) at screensaver.cpp:157
#27 0xb739d2c6 in ?? () from /usr/lib/compiz/libexpo.so
#28 0x0815d5c8 in ?? ()
#29 0x00000054 in ?? ()
#30 0x3e2c0831 in ?? ()
#31 0xb738f644 in ?? () from /usr/lib/compiz/libclone.so
#32 0x0000002d in ?? ()
#33 0x00000054 in ?? ()
#34 0xbfe797d8 in ?? ()
#35 0xb738db50 in ?? () from /usr/lib/compiz/libclone.so
#36 0x0815d5c8 in ?? ()
#37 0x00000054 in ?? ()
#38 0x00000020 in ?? ()
#39 0xb7b569a1 in ?? () from /usr/lib/libXext.so.6
#40 0x08082c18 in ?? ()
#41 0xbfe797e0 in ?? ()
#42 0xbfe79788 in ?? ()
#43 0xb7b98b79 in _XRead () from /usr/lib/libX11.so.6
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 20763
```

---

### Post by denham2010 on 2007-12-08
** Bump **

---

### Post by smartboyathome on 2007-12-09
Looks like there might be some problem between X11 and Compiz, as X11 is the last one on there.

---

