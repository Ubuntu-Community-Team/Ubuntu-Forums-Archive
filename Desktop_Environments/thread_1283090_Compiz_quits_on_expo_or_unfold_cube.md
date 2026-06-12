---
title: "Compiz quits on expo or unfold cube"
date: 2009-10-05
forum: Desktop Environments
---

### Post by night_fox on 2009-10-05
My compiz has suddenly stopped working properly. When I do expo or unfold cube, it quits to metacity.

My graphics card is:

[PHP]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
[/PHP]

Here is what it prints to stderr:

[PHP]WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Undefined command: "-e".  Try "help".
[/PHP]

Here is what it prints to stdout:

[PHP]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 8839
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
Reading symbols from /lib/tls/i686/cmov/libm.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
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
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xb79be710 (LWP 8839)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libxcb.so.1...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /lib/tls/i686/cmov/librt.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libXdmcp.so.6...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/dri/i915_dri.so...Reading symbols from /usr/lib/debug/usr/lib/dri/i915_dri.so...done.
done.
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
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libglib-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libglib-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libORBit-2.so.0...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgmodule-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgthread-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /usr/lib/libdbus-glib-1.so.2...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /lib/libdbus-1.so.3...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /usr/lib/libgobject-2.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libgobject-2.0.so.0.2000.1...done.
done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /lib/libpcre.so.3...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /usr/lib/compiz/libwater.so...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libextrawm.so...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libdbus.so...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libglib.so...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangocairo-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpango-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...Reading symbols from /usr/lib/debug/usr/lib/libpangoft2-1.0.so.0.2400.1...done.
done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...Reading symbols from /usr/lib/debug/usr/lib/libfontconfig.so.1.3.0...done.
done.
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
Reading symbols from /usr/lib/compiz/libneg.so...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libshift.so...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libring.so...done.
Loaded symbols for /usr/lib/compiz/libring.so
Reading symbols from /usr/lib/compiz/libsession.so...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libregex.so...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libinotify.so...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libvideo.so...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libwallpaper.so...done.
Loaded symbols for /usr/lib/compiz/libwallpaper.so
Reading symbols from /usr/lib/compiz/libanimation.so...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libreflex.so...done.
Loaded symbols for /usr/lib/compiz/libreflex.so
Reading symbols from /usr/lib/compiz/libwobbly.so...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libfade.so...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libcube.so...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libanimationaddon.so...done.
Loaded symbols for /usr/lib/compiz/libanimationaddon.so
Reading symbols from /usr/lib/compiz/librotate.so...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libscale.so...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libscalefilter.so...done.
Loaded symbols for /usr/lib/compiz/libscalefilter.so
Reading symbols from /usr/lib/compiz/libshowmouse.so...done.
Loaded symbols for /usr/lib/compiz/libshowmouse.so
Reading symbols from /usr/lib/compiz/lib3d.so...done.
Loaded symbols for /usr/lib/compiz/lib3d.so
Reading symbols from /usr/lib/compiz/libexpo.so...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libezoom.so...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libstaticswitcher.so...done.
Loaded symbols for /usr/lib/compiz/libstaticswitcher.so
Reading symbols from /usr/lib/compiz/libswitcher.so...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libbench.so...done.
Loaded symbols for /usr/lib/compiz/libbench.so
Reading symbols from /usr/lib/pango/1.6.0/modules/pango-basic-fc.so...Reading symbols from /usr/lib/debug/usr/lib/pango/1.6.0/modules/pango-basic-fc.so...done.
done.
Loaded symbols for /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0xb7f0f430 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread 0xb79be710 (LWP 8839)):
#0  0xb7f0f430 in __kernel_vsyscall ()
#1  0xb7bde2a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b7857b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb57c83a7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb7f0f430 in __kernel_vsyscall ()
#6  0xb7b6a6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7b6c098 in abort () from /lib/tls/i686/cmov/libc.so.6
#8  0xb78b827d in _mesa_meta_GenerateMipmap (ctx=0x9816080, target=3553, 
    texObj=0xa342c38) at drivers/common/meta.c:2230
	srcImage = (const struct gl_texture_image *) 0xa33f5d8
	srcLevel = 0
	status = 0
	verts = {{x = 0, y = 0, s = 0, t = 0, r = 0}, {x = 512, y = 0, s = 1, 
    t = 0, r = 0}, {x = 512, y = 512, s = 1, t = 1, r = 0}, {x = 0, y = 512, 
    s = 0, t = 1, r = 0}}
	minFilterSave = 9987
	magFilterSave = 9729
	genMipmapSave = 0 '\0'
	wrapSSave = 33071
	wrapTSave = 33071
	wrapRSave = 10497
	fboSave = 0
	dstLevel = 1
	__PRETTY_FUNCTION__ = "_mesa_meta_GenerateMipmap"
	st = {{0, 0}, {1, 0}, {1, 1}, {0, 1}}
#9  0xb77d8dbc in _mesa_GenerateMipmapEXT (target=3553) at main/fbobject.c:1971
	texObj = (struct gl_texture_object *) 0xa342c38
	ctx = (GLcontext *) 0x9816080
#10 0x08053797 in enableTexture ()
#11 0xb56220d7 in ?? () from /usr/lib/compiz/libreflex.so
#12 0xb54ae916 in ?? () from /usr/lib/compiz/libexpo.so
#13 0xb562ad4f in ?? () from /usr/lib/compiz/libwallpaper.so
#14 0xb54af07f in ?? () from /usr/lib/compiz/libexpo.so
#15 0x0806d036 in paintWindow ()
#16 0xb7208fe0 in ?? () from /usr/lib/compiz/libresize.so
#17 0xb57d65c7 in ?? () from /usr/lib/compiz/libshift.so
#18 0xb567d620 in ?? () from /usr/lib/compiz/libring.so
#19 0xb566b564 in ?? () from /usr/lib/compiz/libthumbnail.so
#20 0xb55f02a0 in ?? () from /usr/lib/compiz/libanimation.so
#21 0xb55e17e0 in ?? () from /usr/lib/compiz/libwobbly.so
#22 0xb55dcf41 in ?? () from /usr/lib/compiz/libfade.so
#23 0xb55d438b in ?? () from /usr/lib/compiz/libcube.so
#24 0xb551cea0 in ?? () from /usr/lib/compiz/libscale.so
#25 0xb5516135 in ?? () from /usr/lib/compiz/libmove.so
#26 0xb54b9fd9 in ?? () from /usr/lib/compiz/lib3d.so
#27 0xb54aee6b in ?? () from /usr/lib/compiz/libexpo.so
#28 0xb549019b in ?? () from /usr/lib/compiz/libstaticswitcher.so
#29 0xb5482ff0 in ?? () from /usr/lib/compiz/libswitcher.so
#30 0x0806ec4c in ?? ()
#31 0x0806f9f0 in paintTransformedOutput ()
#32 0xb54b019d in ?? () from /usr/lib/compiz/libexpo.so
#33 0xb54b1375 in ?? () from /usr/lib/compiz/libexpo.so
#34 0x0806f8ec in paintOutput ()
#35 0xb72094b2 in ?? () from /usr/lib/compiz/libresize.so
#36 0xb57d73a4 in ?? () from /usr/lib/compiz/libshift.so
#37 0xb567dfe5 in ?? () from /usr/lib/compiz/libring.so
#38 0xb566b6ae in ?? () from /usr/lib/compiz/libthumbnail.so
#39 0xb565d5e2 in ?? () from /usr/lib/compiz/libfirepaint.so
#40 0xb56332d5 in ?? () from /usr/lib/compiz/libresizeinfo.so
#41 0xb562a6fc in ?? () from /usr/lib/compiz/libwallpaper.so
#42 0xb55ed180 in ?? () from /usr/lib/compiz/libanimation.so
#43 0xb55e1882 in ?? () from /usr/lib/compiz/libwobbly.so
#44 0xb55d4197 in ?? () from /usr/lib/compiz/libcube.so
#45 0xb55ccbdf in ?? () from /usr/lib/compiz/librotate.so
#46 0xb551b972 in ?? () from /usr/lib/compiz/libscale.so
#47 0xb55105b1 in ?? () from /usr/lib/compiz/libscalefilter.so
#48 0xb54c20e5 in ?? () from /usr/lib/compiz/libshowmouse.so
#49 0xb54b9e8c in ?? () from /usr/lib/compiz/lib3d.so
#50 0xb54ae256 in ?? () from /usr/lib/compiz/libexpo.so
#51 0xb549a54a in ?? () from /usr/lib/compiz/libezoom.so
#52 0xb548db57 in ?? () from /usr/lib/compiz/libstaticswitcher.so
#53 0xb5483699 in ?? () from /usr/lib/compiz/libswitcher.so
#54 0xb53f73c4 in ?? () from /usr/lib/compiz/libbench.so
#55 0x08055d41 in paintScreen ()
#56 0xb7221f73 in ?? () from /usr/lib/compiz/libworkarounds.so
#57 0xb57d5413 in ?? () from /usr/lib/compiz/libshift.so
#58 0xb55d4082 in ?? () from /usr/lib/compiz/libcube.so
#59 0xb54b18f3 in ?? () from /usr/lib/compiz/libexpo.so
#60 0x080581d4 in eventLoop ()
#61 0x08052b75 in main ()
#0  0xb7f0f430 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xb7f0f430 in __kernel_vsyscall ()
#1  0xb7bde2a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b7857b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb57c83a7 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb7f0f430 in __kernel_vsyscall ()
#6  0xb7b6a6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7b6c098 in abort () from /lib/tls/i686/cmov/libc.so.6
#8  0xb78b827d in _mesa_meta_GenerateMipmap (ctx=0x9816080, target=3553, 
    texObj=0xa342c38) at drivers/common/meta.c:2230
#9  0xb77d8dbc in _mesa_GenerateMipmapEXT (target=3553) at main/fbobject.c:1971
#10 0x08053797 in enableTexture ()
#11 0xb56220d7 in ?? () from /usr/lib/compiz/libreflex.so
#12 0xb54ae916 in ?? () from /usr/lib/compiz/libexpo.so
#13 0xb562ad4f in ?? () from /usr/lib/compiz/libwallpaper.so
#14 0xb54af07f in ?? () from /usr/lib/compiz/libexpo.so
#15 0x0806d036 in paintWindow ()
#16 0xb7208fe0 in ?? () from /usr/lib/compiz/libresize.so
#17 0xb57d65c7 in ?? () from /usr/lib/compiz/libshift.so
#18 0xb567d620 in ?? () from /usr/lib/compiz/libring.so
#19 0xb566b564 in ?? () from /usr/lib/compiz/libthumbnail.so
#20 0xb55f02a0 in ?? () from /usr/lib/compiz/libanimation.so
#21 0xb55e17e0 in ?? () from /usr/lib/compiz/libwobbly.so
#22 0xb55dcf41 in ?? () from /usr/lib/compiz/libfade.so
#23 0xb55d438b in ?? () from /usr/lib/compiz/libcube.so
#24 0xb551cea0 in ?? () from /usr/lib/compiz/libscale.so
#25 0xb5516135 in ?? () from /usr/lib/compiz/libmove.so
#26 0xb54b9fd9 in ?? () from /usr/lib/compiz/lib3d.so
#27 0xb54aee6b in ?? () from /usr/lib/compiz/libexpo.so
#28 0xb549019b in ?? () from /usr/lib/compiz/libstaticswitcher.so
#29 0xb5482ff0 in ?? () from /usr/lib/compiz/libswitcher.so
#30 0x0806ec4c in ?? ()
#31 0x0806f9f0 in paintTransformedOutput ()
#32 0xb54b019d in ?? () from /usr/lib/compiz/libexpo.so
#33 0xb54b1375 in ?? () from /usr/lib/compiz/libexpo.so
#34 0x0806f8ec in paintOutput ()
#35 0xb72094b2 in ?? () from /usr/lib/compiz/libresize.so
#36 0xb57d73a4 in ?? () from /usr/lib/compiz/libshift.so
#37 0xb567dfe5 in ?? () from /usr/lib/compiz/libring.so
#38 0xb566b6ae in ?? () from /usr/lib/compiz/libthumbnail.so
#39 0xb565d5e2 in ?? () from /usr/lib/compiz/libfirepaint.so
#40 0xb56332d5 in ?? () from /usr/lib/compiz/libresizeinfo.so
#41 0xb562a6fc in ?? () from /usr/lib/compiz/libwallpaper.so
#42 0xb55ed180 in ?? () from /usr/lib/compiz/libanimation.so
#43 0xb55e1882 in ?? () from /usr/lib/compiz/libwobbly.so
#44 0xb55d4197 in ?? () from /usr/lib/compiz/libcube.so
#45 0xb55ccbdf in ?? () from /usr/lib/compiz/librotate.so
#46 0xb551b972 in ?? () from /usr/lib/compiz/libscale.so
#47 0xb55105b1 in ?? () from /usr/lib/compiz/libscalefilter.so
#48 0xb54c20e5 in ?? () from /usr/lib/compiz/libshowmouse.so
#49 0xb54b9e8c in ?? () from /usr/lib/compiz/lib3d.so
#50 0xb54ae256 in ?? () from /usr/lib/compiz/libexpo.so
#51 0xb549a54a in ?? () from /usr/lib/compiz/libezoom.so
#52 0xb548db57 in ?? () from /usr/lib/compiz/libstaticswitcher.so
#53 0xb5483699 in ?? () from /usr/lib/compiz/libswitcher.so
#54 0xb53f73c4 in ?? () from /usr/lib/compiz/libbench.so
#55 0x08055d41 in paintScreen ()
#56 0xb7221f73 in ?? () from /usr/lib/compiz/libworkarounds.so
#57 0xb57d5413 in ?? () from /usr/lib/compiz/libshift.so
#58 0xb55d4082 in ?? () from /usr/lib/compiz/libcube.so
#59 0xb54b18f3 in ?? () from /usr/lib/compiz/libexpo.so
#60 0x080581d4 in eventLoop ()
#61 0x08052b75 in main ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 8839

[CRASH_HANDLER]: "/tmp/compiz_crash-8839.out" created!
[/PHP]

Where /tmp/compiz_crash-8839.out contains the same backtrace as the one above. Can someone please help me sort this out?

---

