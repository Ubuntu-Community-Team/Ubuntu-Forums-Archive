---
title: "Compiz crashes when coming out of fullscreen in lucid"
date: 2010-05-15
forum: Desktop Environments
---

### Post by yochaigal on 2010-05-15
Hello,

Ever since upgrading to Lucid from Karmic, I have two problems associated with compiz:

1) Compiz crashes randomly, sometimes at startup

2) Compiz almost always crashes whenever I take a windows OUT of fullscreen --- this takes probably 15 tries but will eventually happen.

I use an HP Pavilion DV4000 with an intel 915 chipset.  Running Lucid Lynx with 2.6.32-22-generic kernel.

If I launch compiz from terminal (compiz --replace) and the error occurs, my output is:

yochai@yochai-laptop:/var/log$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz: i915_vtbl.c:339: i915_emit_state: Assertion `0' failed.

After the last line it returns to the command shell.  Only on the last line does it crash, of course (and only after a while).  

If I enable the compiz plugin called crash handler, I get:

yochai@yochai-laptop:/var/log$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz: i915_vtbl.c:339: i915_emit_state: Assertion `0' failed.
Reading symbols from /usr/bin/compiz...(no debugging symbols found)...done.
Attaching to program: /usr/bin/compiz, process 1950
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/mesa/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/mesa/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /usr/lib/libxcb-aux.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-aux.so.0
Reading symbols from /usr/lib/libxcb-event.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-event.so.1
Reading symbols from /usr/lib/libxcb-atom.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-atom.so.1
Reading symbols from /usr/lib/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/libdrm.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/dri/i915_dri.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/dri/i915_dri.so
Reading symbols from /lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libexpat.so.1
Reading symbols from /lib/libdrm_intel.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libdrm_intel.so.1
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libprotobuf.so.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.5
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libdbus-glib-1.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libdirectfb-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirectfb-1.2.so.0
Reading symbols from /usr/lib/libfusion-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfusion-1.2.so.0
Reading symbols from /usr/lib/libdirect-1.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdirect-1.2.so.0
Reading symbols from /lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libpng12.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /lib/tls/i686/cmov/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libresolv.so.2
Reading symbols from /lib/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libgnomecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libcommands.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcommands.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbolsUndefined command: "-e".  Try "help".
 found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libsession.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libexpo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libobs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libobs.so
Reading symbols from /usr/lib/compiz/libezoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libsnap.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsnap.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libstaticswitcher.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libstaticswitcher.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
0x00270422 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb78c7a40 (LWP 1950)):
#0  0x00270422 in __kernel_vsyscall ()
#1  0x003307d3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x002d1de3 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0x00a3127d in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00adc3e1 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  <signal handler called>
#6  0x00270422 in __kernel_vsyscall ()
#7  0x002c3651 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0x002c6a82 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0x002bc718 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0x010002e7 in ?? () from /usr/lib/dri/i915_dri.so
#11 0x0102a534 in ?? () from /usr/lib/dri/i915_dri.so
#12 0x010df8f3 in ?? () from /usr/lib/dri/i915_dri.so
#13 0x010d36b3 in _tnl_run_pipeline () from /usr/lib/dri/i915_dri.so
#14 0x0102a9fd in ?? () from /usr/lib/dri/i915_dri.so
#15 0x010d4406 in _tnl_draw_prims () from /usr/lib/dri/i915_dri.so
#16 0x010d4869 in _tnl_vbo_draw_prims () from /usr/lib/dri/i915_dri.so
#17 0x010cbf31 in ?? () from /usr/lib/dri/i915_dri.so
#18 0x010c2c17 in ?? () from /usr/lib/dri/i915_dri.so
#19 0x0806e8fb in ?? ()
#20 0x0806e67e in drawWindowTexture ()
#21 0x00c58912 in ?? () from /usr/lib/compiz/libanimation.so
#22 0x00b0a741 in ?? () from /usr/lib/compiz/libexpo.so
#23 0x0806da42 in drawWindow ()
#24 0x00ae144a in ?? () from /usr/lib/compiz/libdecoration.so
#25 0x005982d3 in ?? () from /usr/lib/compiz/libsvg.so
#26 0x00b0b1e9 in ?? () from /usr/lib/compiz/libexpo.so
#27 0x00dcef0e in ?? () from /usr/lib/compiz/libobs.so
#28 0x0806d921 in paintWindow ()
#29 0x00ccf1b8 in ?? () from /usr/lib/compiz/libmove.so
#30 0x005910aa in ?? () from /usr/lib/compiz/libresize.so
#31 0x00c5c637 in ?? () from /usr/lib/compiz/libanimation.so
#32 0x00991c79 in ?? () from /usr/lib/compiz/libfade.so
#33 0x00b0af08 in ?? () from /usr/lib/compiz/libexpo.so
#34 0x00dcee35 in ?? () from /usr/lib/compiz/libobs.so
#35 0x00b47eaf in ?? () from /usr/lib/compiz/libscale.so
#36 0x00cc3b6c in ?? () from /usr/lib/compiz/libstaticswitcher.so
#37 0x0806f569 in ?? ()
#38 0x080702c4 in paintOutput ()
#39 0x0059159c in ?? () from /usr/lib/compiz/libresize.so
#40 0x0092c2a8 in ?? () from /usr/lib/compiz/libresizeinfo.so
#41 0x00c5918f in ?? () from /usr/lib/compiz/libanimation.so
#42 0x00b0a296 in ?? () from /usr/lib/compiz/libexpo.so
#43 0x00d3b58f in ?? () from /usr/lib/compiz/libezoom.so
#44 0x00b469b2 in ?? () from /usr/lib/compiz/libscale.so
#45 0x00cc15cc in ?? () from /usr/lib/compiz/libstaticswitcher.so
#46 0x080562eb in paintScreen ()
#47 0x008d9fc3 in ?? () from /usr/lib/compiz/libworkarounds.so
#48 0x00b0d9ca in ?? () from /usr/lib/compiz/libexpo.so
#49 0x08058647 in eventLoop ()
#50 0x08052e4b in main ()
(gdb) 
(gdb) 
(gdb) #0  0x00270422 in __kernel_vsyscall ()
#1  0x003307d3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x002d1de3 in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0x00a3127d in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00adc3e1 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  <signal handler called>
#6  0x00270422 in __kernel_vsyscall ()
#7  0x002c3651 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0x002c6a82 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0x002bc718 in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0x010002e7 in ?? () from /usr/lib/dri/i915_dri.so
#11 0x0102a534 in ?? () from /usr/lib/dri/i915_dri.so
#12 0x010df8f3 in ?? () from /usr/lib/dri/i915_dri.so
#13 0x010d36b3 in _tnl_run_pipeline () from /usr/lib/dri/i915_dri.so
#14 0x0102a9fd in ?? () from /usr/lib/dri/i915_dri.so
#15 0x010d4406 in _tnl_draw_prims () from /usr/lib/dri/i915_dri.so
#16 0x010d4869 in _tnl_vbo_draw_prims () from /usr/lib/dri/i915_dri.so
#17 0x010cbf31 in ?? () from /usr/lib/dri/i915_dri.so
#18 0x010c2c17 in ?? () from /usr/lib/dri/i915_dri.so
#19 0x0806e8fb in ?? ()
#20 0x0806e67e in drawWindowTexture ()
#21 0x00c58912 in ?? () from /usr/lib/compiz/libanimation.so
#22 0x00b0a741 in ?? () from /usr/lib/compiz/libexpo.so
#23 0x0806da42 in drawWindow ()
#24 0x00ae144a in ?? () from /usr/lib/compiz/libdecoration.so
#25 0x005982d3 in ?? () from /usr/lib/compiz/libsvg.so
#26 0x00b0b1e9 in ?? () from /usr/lib/compiz/libexpo.so
#27 0x00dcef0e in ?? () from /usr/lib/compiz/libobs.so
#28 0x0806d921 in paintWindow ()
#29 0x00ccf1b8 in ?? () from /usr/lib/compiz/libmove.so
#30 0x005910aa in ?? () from /usr/lib/compiz/libresize.so
#31 0x00c5c637 in ?? () from /usr/lib/compiz/libanimation.so
#32 0x00991c79 in ?? () from /usr/lib/compiz/libfade.so
#33 0x00b0af08 in ?? () from /usr/lib/compiz/libexpo.so
#34 0x00dcee35 in ?? () from /usr/lib/compiz/libobs.so
#35 0x00b47eaf in ?? () from /usr/lib/compiz/libscale.so
#36 0x00cc3b6c in ?? () from /usr/lib/compiz/libstaticswitcher.so
#37 0x0806f569 in ?? ()
#38 0x080702c4 in paintOutput ()
#39 0x0059159c in ?? () from /usr/lib/compiz/libresize.so
#40 0x0092c2a8 in ?? () from /usr/lib/compiz/libresizeinfo.so
#41 0x00c5918f in ?? () from /usr/lib/compiz/libanimation.so
#42 0x00b0a296 in ?? () from /usr/lib/compiz/libexpo.so
#43 0x00d3b58f in ?? () from /usr/lib/compiz/libezoom.so
#44 0x00b469b2 in ?? () from /usr/lib/compiz/libscale.so
#45 0x00cc15cc in ?? () from /usr/lib/compiz/libstaticswitcher.so
#46 0x080562eb in paintScreen ()
#47 0x008d9fc3 in ?? () from /usr/lib/compiz/libworkarounds.so
#48 0x00b0d9ca in ?? () from /usr/lib/compiz/libexpo.so
#49 0x08058647 in eventLoop ()
#50 0x08052e4b in main ()
(gdb) A debugging session is active.

	Inferior 1 [process 1950] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 1950

[CRASH_HANDLER]: "/tmp/compiz_crash-1950.out" created!

---

