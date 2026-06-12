---
title: "Compiz Not Starting"
date: 2009-07-04
forum: Desktop Environments
---

### Post by shafin on 2009-07-04
Hi,
In my pc I have several user accounts. Recently, in the my account, compiz is failing to start, while it works fine on others.
Whenever I try compiz --replace, it throws this to me:
```
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 5040
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
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libxslt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...Reading symbols from /usr/lib/debug/usr/lib/libxml2.so.2.6.32...done.
done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/libm.so.6...done.
Loaded symbols for /lib/libm.so.6
Reading symbols from /lib/libc.so.6...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/libdl.so.2...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/libuuid.so.1...done.
Loaded symbols for /lib/libuuid.so.1
Reading symbols from /lib/libz.so.1...done.
Loaded symbols for /lib/libz.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /usr/lib/libdrm.so.2...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread 0x7ffc4b6a5750 (LWP 5040)]
Loaded symbols for /lib/libpthread.so.0
Reading symbols from /lib/ld-linux-x86-64.so.2...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Reading symbols from /usr/lib/libxcb.so.1...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /lib/librt.so.1...done.
Loaded symbols for /lib/librt.so.1
Reading symbols from /usr/lib/libXdmcp.so.6...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/dri/i915_dri.so...done.
Loaded symbols for /usr/lib/dri/i915_dri.so
Reading symbols from /usr/lib/libexpat.so.1...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/libdrm_intel.so.1...done.
Loaded symbols for /usr/lib/libdrm_intel.so.1
Reading symbols from /usr/lib/compiz/libccp.so...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libprotobuf.so.3...done.
Loaded symbols for /usr/lib/libprotobuf.so.3
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compizconfig/backends/libini.so...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libdbus.so...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /lib/libdbus-1.so.3...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libwidget.so...done.
Loaded symbols for /usr/lib/compiz/libwidget.so
Reading symbols from /usr/lib/compiz/libwater.so...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libglib.so...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/libglib-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libglib-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/libpcre.so.3...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /usr/lib/compiz/libfirepaint.so...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libcommands.so...done.
Loaded symbols for /usr/lib/compiz/libcommands.so
Reading symbols from /usr/lib/compiz/libfadedesktop.so...done.
Loaded symbols for /usr/lib/compiz/libfadedesktop.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libsession.so...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libshelf.so...done.
Loaded symbols for /usr/lib/compiz/libshelf.so
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangocairo-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpango-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgobject-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgmodule-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangoft2-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libpixman-1.so.0...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libdirectfb-1.0.so.0...done.
Loaded symbols for /usr/lib/libdirectfb-1.0.so.0
Reading symbols from /usr/lib/libfusion-1.0.so.0...done.
Loaded symbols for /usr/lib/libfusion-1.0.so.0
Reading symbols from /usr/lib/libdirect-1.0.so.0...done.
Loaded symbols for /usr/lib/libdirect-1.0.so.0
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libxcb-render-util.so.0...done.
Loaded symbols for /usr/lib/libxcb-render-util.so.0
Reading symbols from /usr/lib/libxcb-render.so.0...done.
Loaded symbols for /usr/lib/libxcb-render.so.0
Reading symbols from /usr/lib/compiz/libneg.so...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libsvg.so...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/librsvg-2.so.2...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgdk_pixbuf-2.0.so.0.1600.1...done.
done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libgio-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgio-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /lib/libbz2.so.1.0...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /lib/libselinux.so.1...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libannotate.so...done.
Loaded symbols for /usr/lib/compiz/libannotate.so
Reading symbols from /usr/lib/compiz/libwinrules.so...done.
Loaded symbols for /usr/lib/compiz/libwinrules.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libinotify.so...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libsplash.so...done.
Loaded symbols for /usr/lib/compiz/libsplash.so
Reading symbols from /usr/lib/compiz/libput.so...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libvideo.so...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libring.so...done.
Loaded symbols for /usr/lib/compiz/libring.so
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libreflex.so...done.
Loaded symbols for /usr/lib/compiz/libreflex.so
Reading symbols from /usr/lib/compiz/libregex.so...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libshift.so...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libobs.so...done.
Loaded symbols for /usr/lib/compiz/libobs.so
Reading symbols from /usr/lib/compiz/libgroup.so...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /usr/lib/compiz/libwobbly.so...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libwallpaper.so...done.
Loaded symbols for /usr/lib/compiz/libwallpaper.so
Reading symbols from /usr/lib/compiz/libanimation.so...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libloginout.so...done.
Loaded symbols for /usr/lib/compiz/libloginout.so
Reading symbols from /usr/lib/compiz/libanimationaddon.so...done.
Loaded symbols for /usr/lib/compiz/libanimationaddon.so
Reading symbols from /usr/lib/compiz/libcube.so...done.
Loaded symbols for /usr/lib/compiz/libcube.so
0x00007ffc495008f5 in waitpid ()
   from /lib/libc.so.6
(gdb) (gdb) 
Thread 1 (Thread 0x7ffc4b6a5750 (LWP 5040)):
#0  0x00007ffc495008f5 in waitpid () from /lib/libc.so.6
#1  0x00007ffc494982d1 in ?? () from /lib/libc.so.6
#2  0x00007ffc3d0e6879 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007ffc4948bfb5 in raise () from /lib/libc.so.6
#5  0x00007ffc4948dbc3 in abort () from /lib/libc.so.6
#6  0x00007ffc49484f09 in __assert_fail () from /lib/libc.so.6
#7  0x00007ffc4744b511 in ?? () from /usr/lib/dri/i915_dri.so
#8  0x00007ffc474a5826 in _mesa_reference_buffer_object ()
   from /usr/lib/dri/i915_dri.so
#9  0x00007ffc4753255d in ?? () from /usr/lib/dri/i915_dri.so
#10 0x00007ffc474be0b4 in _mesa_delete_list () from /usr/lib/dri/i915_dri.so
#11 0x00007ffc474c2f9c in ?? () from /usr/lib/dri/i915_dri.so
#12 0x00007ffc474c302e in _mesa_EndList () from /usr/lib/dri/i915_dri.so
#13 0x00007ffc3a6a31f6 in ?? () from /usr/lib/compiz/libcube.so
#14 0x00007ffc3a6a363f in ?? () from /usr/lib/compiz/libcube.so
#15 0x00007ffc46be2ee1 in ?? () from /usr/lib/compiz/libccp.so
#16 0x00007ffc45789db1 in ?? () from /usr/lib/compiz/libdbus.so
#17 0x00007ffc3a6a5fb1 in ?? () from /usr/lib/compiz/libcube.so
#18 0x00007ffc46be3415 in ?? () from /usr/lib/compiz/libccp.so
#19 0x00007ffc46be3726 in ?? () from /usr/lib/compiz/libccp.so
#20 0x00007ffc45787a02 in ?? () from /usr/lib/compiz/libdbus.so
#21 0x000000000042b54c in ?? ()
#22 0x000000000041304b in forEachScreenObject ()
#23 0x000000000042b7ad in ?? ()
#24 0x000000000040d91e in compObjectForEachType ()
#25 0x000000000042b4f6 in ?? ()
#26 0x000000000040eab3 in forEachDisplayObject ()
#27 0x000000000042b7ad in ?? ()
#28 0x000000000040d91e in compObjectForEachType ()
#29 0x000000000042b4f6 in ?? ()
#30 0x000000000042b65a in pushPlugin ()
#31 0x0000000000412778 in eventLoop ()
#32 0x000000000040d550 in main ()
#0  0x00007ffc495008f5 in waitpid () from /lib/libc.so.6
(gdb) 
(gdb) 
(gdb) #0  0x00007ffc495008f5 in waitpid () from /lib/libc.so.6
#1  0x00007ffc494982d1 in ?? () from /lib/libc.so.6
#2  0x00007ffc3d0e6879 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  <signal handler called>
#4  0x00007ffc4948bfb5 in raise () from /lib/libc.so.6
#5  0x00007ffc4948dbc3 in abort () from /lib/libc.so.6
#6  0x00007ffc49484f09 in __assert_fail () from /lib/libc.so.6
#7  0x00007ffc4744b511 in ?? () from /usr/lib/dri/i915_dri.so
#8  0x00007ffc474a5826 in _mesa_reference_buffer_object ()
   from /usr/lib/dri/i915_dri.so
#9  0x00007ffc4753255d in ?? () from /usr/lib/dri/i915_dri.so
#10 0x00007ffc474be0b4 in _mesa_delete_list () from /usr/lib/dri/i915_dri.so
#11 0x00007ffc474c2f9c in ?? () from /usr/lib/dri/i915_dri.so
#12 0x00007ffc474c302e in _mesa_EndList () from /usr/lib/dri/i915_dri.so
#13 0x00007ffc3a6a31f6 in ?? () from /usr/lib/compiz/libcube.so
#14 0x00007ffc3a6a363f in ?? () from /usr/lib/compiz/libcube.so
#15 0x00007ffc46be2ee1 in ?? () from /usr/lib/compiz/libccp.so
#16 0x00007ffc45789db1 in ?? () from /usr/lib/compiz/libdbus.so
#17 0x00007ffc3a6a5fb1 in ?? () from /usr/lib/compiz/libcube.so
#18 0x00007ffc46be3415 in ?? () from /usr/lib/compiz/libccp.so
#19 0x00007ffc46be3726 in ?? () from /usr/lib/compiz/libccp.so
#20 0x00007ffc45787a02 in ?? () from /usr/lib/compiz/libdbus.so
#21 0x000000000042b54c in ?? ()
#22 0x000000000041304b in forEachScreenObject ()
#23 0x000000000042b7ad in ?? ()
#24 0x000000000040d91e in compObjectForEachType ()
#25 0x000000000042b4f6 in ?? ()
#26 0x000000000040eab3 in forEachDisplayObject ()
#27 0x000000000042b7ad in ?? ()
#28 0x000000000040d91e in compObjectForEachType ()
#29 0x000000000042b4f6 in ?? ()
#30 0x000000000042b65a in pushPlugin ()
#31 0x0000000000412778 in eventLoop ()
#32 0x000000000040d550 in main ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 5040
```

What could have caused this problem?

---

