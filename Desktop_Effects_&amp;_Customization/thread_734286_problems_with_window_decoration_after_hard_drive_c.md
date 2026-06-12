---
title: "problems with window decoration after hard drive crash"
date: 2008-03-24
forum: Desktop Effects &amp; Customization
---

### Post by MetalHannes on 2008-03-24
Hello,
About a week ago my Computer first froze then crashed.
After that i wasn't able to start without fsck the drive from a knoppix cd.
So after that i could start my ubuntu installation again but the xserver configuration was all messed up. So reconfigured everything as good as I was able to,
But when I start compiz now it won't load emerald
I've tried:
```
emerald --replace &
compiz --replace &
```

And also made emerald --replace & as Command in the Window decorations tab of the compiz-settings-manager

None of them worked.

I've installed XGL and it worked but I don't want to use XGL since it messes with my games :(

I've found some error output in /tmp:
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 8601
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
Reading symbols from /usr/lib/libGLcore.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libini.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /home/metalhannes/.compiz/plugins/lib3d.so...done.
Loaded symbols for /home/metalhannes/.compiz/plugins/lib3d.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libextrawm.so...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/libglib-2.0.so.0...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libregex.so...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libexpat.so.1...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread -1222138160 (LWP 8601)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/compiz/libscreenshot.so...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libshift.so...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libshowdesktop.so...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libsnap.so...done.
Loaded symbols for /usr/lib/compiz/libsnap.so
Reading symbols from /usr/lib/compiz/libsvg.so...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/librsvg-2.so.2...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /lib/libbz2.so.1.0...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libwater.so...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libwobbly.so...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /home/metalhannes/.compiz/plugins/libsnow.so...done.
Loaded symbols for /home/metalhannes/.compiz/plugins/libsnow.so
Reading symbols from /usr/lib/compiz/libanimation.so...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libblur.so...done.
Loaded symbols for /usr/lib/compiz/libblur.so
Reading symbols from /usr/lib/compiz/libfade.so...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libneg.so...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libopacify.so...done.
Loaded symbols for /usr/lib/compiz/libopacify.so
Reading symbols from /usr/lib/compiz/libreflex.so...done.
Loaded symbols for /usr/lib/compiz/libreflex.so
Reading symbols from /usr/lib/compiz/libvideo.so...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libcube.so...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libcubecaps.so...done.
Loaded symbols for /usr/lib/compiz/libcubecaps.so
Reading symbols from /usr/lib/compiz/librotate.so...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libscale.so...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libcubereflex.so...done.
Loaded symbols for /usr/lib/compiz/libcubereflex.so
Reading symbols from /usr/lib/compiz/libexpo.so...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libezoom.so...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/pango/1.6.0/modules/pango-basic-fc.so...done.
Loaded symbols for /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
Reading symbols from /home/metalhannes/.compiz/plugins/libwallpaper.so...done.
Loaded symbols for /home/metalhannes/.compiz/plugins/libwallpaper.so
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1222138160 (LWP 8601)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cc06b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c65b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5b02962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfa5a868 in ?? ()
#5  0xb5b02a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfa5dbf1 in ?? ()
#7  0x00002199 in ?? ()
#8  0x00002199 in ?? ()
#9  0x00002199 in ?? ()
#10 0xb7d75140 in ?? () from /lib/tls/i686/cmov/libc.so.6
#11 0x00000030 in ?? ()
#12 0x00000005 in ?? ()
#13 0xb7d73ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0x6f686365 in ?? ()
#15 0x20652d20 in ?? ()
#16 0x74657322 in ?? ()
#17 0x6f727020 in ?? ()
#18 0x0a74706d in ?? ()
#19 0x65726874 in ?? ()
#20 0x61206461 in ?? ()
#21 0x796c7070 in ?? ()
#22 0x6c6c6120 in ?? ()
#23 0x20746220 in ?? ()
#24 0x6c6c7566 in ?? ()
#25 0x6863650a in ?? ()
#26 0x5c5c206f in ?? ()
#27 0x650a6e5c in ?? ()
#28 0x206f6863 in ?? ()
#29 0x6e5c5c5c in ?? ()
#30 0x0a74620a in ?? ()
#31 0x74697571 in ?? ()
#32 0x203e2022 in ?? ()
#33 0x706d742f in ?? ()
#34 0x6264672f in ?? ()
#35 0x706d742e in ?? ()
#36 0x6264673b in ?? ()
#37 0x20712d20 in ?? ()
#38 0x7273752f in ?? ()
#39 0x6e69622f in ?? ()
#40 0x6d6f632f in ?? ()
#41 0x2e7a6970 in ?? ()
#42 0x6c616572 in ?? ()
#43 0x30363820 in ?? ()
#44 0x203c2031 in ?? ()
#45 0x706d742f in ?? ()
#46 0x6264672f in ?? ()
#47 0x706d742e in ?? ()
#48 0x67207c20 in ?? ()
#49 0x20706572 in ?? ()
#50 0x2220762d in ?? ()
#51 0x73206f4e in ?? ()
#52 0x6f626d79 in ?? ()
#53 0x6174206c in ?? ()
#54 0x22656c62 in ?? ()
#55 0x74207c20 in ?? ()
#56 0x2f206565 in ?? ()
#57 0x2f706d74 in ?? ()
#58 0x706d6f63 in ?? ()
#59 0x635f7a69 in ?? ()
#60 0x68736172 in ?? ()
#61 0x3036382d in ?? ()
#62 0x756f2e31 in ?? ()
#63 0x72203b74 in ?? ()
#64 0x662d206d in ?? ()
#65 0x6d742f20 in ?? ()
#66 0x64672f70 in ?? ()
#67 0x6d742e62 in ?? ()
#68 0x65203b70 in ?? ()
#69 0x206f6863 in ?? ()
#70 0x435b0a22 in ?? ()
#71 0x48534152 in ?? ()
#72 0x4e41485f in ?? ()
#73 0x52454c44 in ?? ()
#74 0x5c203a5d in ?? ()
#75 0x6d742f22 in ?? ()
#76 0x6f632f70 in ?? ()
#77 0x7a69706d in ?? ()
#78 0x6172635f in ?? ()
#79 0x382d6873 in ?? ()
#80 0x2e313036 in ?? ()
#81 0x5c74756f in ?? ()
#82 0x72632022 in ?? ()
#83 0x65746165 in ?? ()
#84 0x220a2164 in ?? ()
#85 0x08c16400 in ?? ()
#86 0x08c16508 in ?? ()
#87 0xb7c976c1 in ?? () from /lib/tls/i686/cmov/libc.so.6
#88 0xb7d75148 in ?? () from /lib/tls/i686/cmov/libc.so.6
#89 0xb7d75170 in ?? () from /lib/tls/i686/cmov/libc.so.6
#90 0xb7d5a13c in ?? () from /lib/tls/i686/cmov/libc.so.6
#91 0x00000030 in ?? ()
#92 0x0884ff50 in ?? ()
#93 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7cc06b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c65b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5b02962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfa5a868 in ?? ()
#5  0xb5b02a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfa5dbf1 in ?? ()
#7  0x00002199 in ?? ()
#8  0x00002199 in ?? ()
#9  0x00002199 in ?? ()
#10 0xb7d75140 in ?? () from /lib/tls/i686/cmov/libc.so.6
#11 0x00000030 in ?? ()
#12 0x00000005 in ?? ()
#13 0xb7d73ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0x6f686365 in ?? ()
#15 0x20652d20 in ?? ()
#16 0x74657322 in ?? ()
#17 0x6f727020 in ?? ()
#18 0x0a74706d in ?? ()
#19 0x65726874 in ?? ()
#20 0x61206461 in ?? ()
#21 0x796c7070 in ?? ()
#22 0x6c6c6120 in ?? ()
#23 0x20746220 in ?? ()
#24 0x6c6c7566 in ?? ()
#25 0x6863650a in ?? ()
#26 0x5c5c206f in ?? ()
#27 0x650a6e5c in ?? ()
#28 0x206f6863 in ?? ()
#29 0x6e5c5c5c in ?? ()
#30 0x0a74620a in ?? ()
#31 0x74697571 in ?? ()
#32 0x203e2022 in ?? ()
#33 0x706d742f in ?? ()
#34 0x6264672f in ?? ()
#35 0x706d742e in ?? ()
#36 0x6264673b in ?? ()
#37 0x20712d20 in ?? ()
#38 0x7273752f in ?? ()
#39 0x6e69622f in ?? ()
#40 0x6d6f632f in ?? ()
#41 0x2e7a6970 in ?? ()
#42 0x6c616572 in ?? ()
#43 0x30363820 in ?? ()
#44 0x203c2031 in ?? ()
#45 0x706d742f in ?? ()
#46 0x6264672f in ?? ()
#47 0x706d742e in ?? ()
#48 0x67207c20 in ?? ()
#49 0x20706572 in ?? ()
#50 0x2220762d in ?? ()
#51 0x73206f4e in ?? ()
#52 0x6f626d79 in ?? ()
#53 0x6174206c in ?? ()
#54 0x22656c62 in ?? ()
#55 0x74207c20 in ?? ()
#56 0x2f206565 in ?? ()
#57 0x2f706d74 in ?? ()
#58 0x706d6f63 in ?? ()
#59 0x635f7a69 in ?? ()
#60 0x68736172 in ?? ()
#61 0x3036382d in ?? ()
#62 0x756f2e31 in ?? ()
#63 0x72203b74 in ?? ()
#64 0x662d206d in ?? ()
#65 0x6d742f20 in ?? ()
#66 0x64672f70 in ?? ()
#67 0x6d742e62 in ?? ()
#68 0x65203b70 in ?? ()
#69 0x206f6863 in ?? ()
#70 0x435b0a22 in ?? ()
#71 0x48534152 in ?? ()
#72 0x4e41485f in ?? ()
#73 0x52454c44 in ?? ()
#74 0x5c203a5d in ?? ()
#75 0x6d742f22 in ?? ()
#76 0x6f632f70 in ?? ()
#77 0x7a69706d in ?? ()
#78 0x6172635f in ?? ()
#79 0x382d6873 in ?? ()
#80 0x2e313036 in ?? ()
#81 0x5c74756f in ?? ()
#82 0x72632022 in ?? ()
#83 0x65746165 in ?? ()
#84 0x220a2164 in ?? ()
#85 0x08c16400 in ?? ()
#86 0x08c16508 in ?? ()
#87 0xb7c976c1 in ?? () from /lib/tls/i686/cmov/libc.so.6
#88 0xb7d75148 in ?? () from /lib/tls/i686/cmov/libc.so.6
#89 0xb7d75170 in ?? () from /lib/tls/i686/cmov/libc.so.6
#90 0xb7d5a13c in ?? () from /lib/tls/i686/cmov/libc.so.6
#91 0x00000030 in ?? ()
#92 0x0884ff50 in ?? ()
#93 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 8601

```

I don't know what the most of this means so i have to post it all sry :(

It seems to find everything (except XGL ofcourse):
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:018b (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
```

I have got a nVidia Quadro 4 XGL with 128 MB and it all worked well before the big crash...

Thanks a lot

Hannes

---

