---
title: "gusty gibbon/compiz-fusion/ATI Video Card | Not working"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by StevenEpic on 2007-10-19
i just upgraded ubuntu to seven ten

compiz fusion is not working

i tried starting with the terminal, and this is what it gave me:
```

epic@steven-epic-design:~$ sudo compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'core'
/usr/bin/compiz.real (trailfocus) - Warn: Attempting to define start higher than max windows.
/usr/bin/compiz.real (trailfocus) - Warn: Attempting to define start higher than max windows.
/usr/bin/compiz.real (trailfocus) - Warn: Attempting to define start higher than max windows.
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: /media/sda1/Documents and Settings/User/My Documents/PiRK/Wallpapers/TigerAquaBlue1.jpg
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: /media/sda1/Documents and Settings/User/My Documents/PiRK/Wallpapers/TigerAquaBlue1.jpg
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 9859
Reading symbols from /usr/lib/fglrx/libGL.so.1.2.xlibmesa...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/fglrx/libGL.so.1.2.xlibmesa
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213446480 (LWP 9859)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /usr/lib/libXrender.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libini.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libcolorfilter.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcolorfilter.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglUndefined command: "-e".  Try "help".
ib-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libvideo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libopacify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopacify.so
Reading symbols from /usr/lib/compiz/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libinotify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libput.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libtext.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libzoom.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libmblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libaddhelper.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libaddhelper.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libtrailfocus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtrailfocus.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libfadedesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfadedesktop.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libexpo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libezoom.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libcubecaps.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcubecaps.so
Reading symbols from /usr/lib/compiz/libscreensaver.so...done.
Loaded symbols for /usr/lib/compiz/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...done.
Loaded symbols for /usr/lib/libXss.so.1
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213446480 (LWP 9859)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c4eb3a in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7490962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  0xbf8efb28 in ?? ()
#4  0xb7490a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  0xbf8f189b in ?? ()
#6  0x00002683 in ?? ()
#7  0x00002683 in ?? ()
#8  0x00002683 in ?? ()
#9  0xbf8efb00 in ?? ()
#10 0xb7fa17b0 in ?? () from /lib/ld-linux.so.2
#11 0xbf8efea8 in ?? ()
#12 0xbf8eff64 in ?? ()
#13 0x6f686365 in ?? ()
#14 0x20652d20 in ?? ()
#15 0x74657322 in ?? ()
#16 0x6f727020 in ?? ()
#17 0x0a74706d in ?? ()
#18 0x65726874 in ?? ()
#19 0x61206461 in ?? ()
#20 0x796c7070 in ?? ()
#21 0x6c6c6120 in ?? ()
#22 0x20746220 in ?? ()
#23 0x6c6c7566 in ?? ()
#24 0x6863650a in ?? ()
#25 0x5c5c206f in ?? ()
#26 0x650a6e5c in ?? ()
#27 0x206f6863 in ?? ()
#28 0x6e5c5c5c in ?? ()
#29 0x0a74620a in ?? ()
#30 0x74697571 in ?? ()
#31 0x203e2022 in ?? ()
#32 0x706d742f in ?? ()
#33 0x6264672f in ?? ()
#34 0x706d742e in ?? ()
#35 0x6264673b in ?? ()
#36 0x20712d20 in ?? ()
#37 0x7273752f in ?? ()
#38 0x6e69622f in ?? ()
#39 0x6d6f632f in ?? ()
#40 0x2e7a6970 in ?? ()
#41 0x6c616572 in ?? ()
#42 0x35383920 in ?? ()
#43 0x203c2039 in ?? ()
#44 0x706d742f in ?? ()
#45 0x6264672f in ?? ()
#46 0x706d742e in ?? ()
#47 0x67207c20 in ?? ()
#48 0x20706572 in ?? ()
#49 0x2220762d in ?? ()
#50 0x73206f4e in ?? ()
#51 0x6f626d79 in ?? ()
#52 0x6174206c in ?? ()
#53 0x22656c62 in ?? ()
#54 0x74207c20 in ?? ()
#55 0x2f206565 in ?? ()
#56 0x2f706d74 in ?? ()
#57 0x706d6f63 in ?? ()
#58 0x635f7a69 in ?? ()
#59 0x68736172 in ?? ()
#60 0x3538392d in ?? ()
#61 0x756f2e39 in ?? ()
#62 0x72203b74 in ?? ()
#63 0x662d206d in ?? ()
#64 0x6d742f20 in ?? ()
#65 0x64672f70 in ?? ()
#66 0x6d742e62 in ?? ()
#67 0x65203b70 in ?? ()
#68 0x206f6863 in ?? ()
#69 0x435b0a22 in ?? ()
#70 0x48534152 in ?? ()
#71 0x4e41485f in ?? ()
#72 0x52454c44 in ?? ()
#73 0x5c203a5d in ?? ()
#74 0x6d742f22 in ?? ()
#75 0x6f632f70 in ?? ()
#76 0x7a69706d in ?? ()
#77 0x6172635f in ?? ()
#78 0x392d6873 in ?? ()
#79 0x2e393538 in ?? ()
#80 0x5c74756f in ?? ()
#81 0x72632022 in ?? ()
#82 0x65746165 in ?? ()
#83 0x220a2164 in ?? ()
#84 0x056baf00 in ?? ()
#85 0xb7f9eb59 in ?? () from /lib/ld-linux.so.2
#86 <signal handler called>
#87 0x00000000 in ?? ()
#88 0x0806cef6 in pushPlugin ()
#89 0x0805500f in eventLoop ()
#90 0x08051bc0 in main ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c4eb3a in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7490962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  0xbf8efb28 in ?? ()
#4  0xb7490a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#5  0xbf8f189b in ?? ()
#6  0x00002683 in ?? ()
#7  0x00002683 in ?? ()
#8  0x00002683 in ?? ()
#9  0xbf8efb00 in ?? ()
#10 0xb7fa17b0 in ?? () from /lib/ld-linux.so.2
#11 0xbf8efea8 in ?? ()
#12 0xbf8eff64 in ?? ()
#13 0x6f686365 in ?? ()
#14 0x20652d20 in ?? ()
#15 0x74657322 in ?? ()
#16 0x6f727020 in ?? ()
#17 0x0a74706d in ?? ()
#18 0x65726874 in ?? ()
#19 0x61206461 in ?? ()
#20 0x796c7070 in ?? ()
#21 0x6c6c6120 in ?? ()
#22 0x20746220 in ?? ()
#23 0x6c6c7566 in ?? ()
#24 0x6863650a in ?? ()
#25 0x5c5c206f in ?? ()
#26 0x650a6e5c in ?? ()
#27 0x206f6863 in ?? ()
#28 0x6e5c5c5c in ?? ()
#29 0x0a74620a in ?? ()
#30 0x74697571 in ?? ()
#31 0x203e2022 in ?? ()
#32 0x706d742f in ?? ()
#33 0x6264672f in ?? ()
#34 0x706d742e in ?? ()
#35 0x6264673b in ?? ()
#36 0x20712d20 in ?? ()
#37 0x7273752f in ?? ()
#38 0x6e69622f in ?? ()
#39 0x6d6f632f in ?? ()
#40 0x2e7a6970 in ?? ()
#41 0x6c616572 in ?? ()
#42 0x35383920 in ?? ()
#43 0x203c2039 in ?? ()
#44 0x706d742f in ?? ()
#45 0x6264672f in ?? ()
#46 0x706d742e in ?? ()
#47 0x67207c20 in ?? ()
#48 0x20706572 in ?? ()
#49 0x2220762d in ?? ()
#50 0x73206f4e in ?? ()
#51 0x6f626d79 in ?? ()
#52 0x6174206c in ?? ()
#53 0x22656c62 in ?? ()
#54 0x74207c20 in ?? ()
#55 0x2f206565 in ?? ()
#56 0x2f706d74 in ?? ()
#57 0x706d6f63 in ?? ()
#58 0x635f7a69 in ?? ()
#59 0x68736172 in ?? ()
#60 0x3538392d in ?? ()
#61 0x756f2e39 in ?? ()
#62 0x72203b74 in ?? ()
#63 0x662d206d in ?? ()
#64 0x6d742f20 in ?? ()
#65 0x64672f70 in ?? ()
#66 0x6d742e62 in ?? ()
#67 0x65203b70 in ?? ()
#68 0x206f6863 in ?? ()
#69 0x435b0a22 in ?? ()
#70 0x48534152 in ?? ()
#71 0x4e41485f in ?? ()
#72 0x52454c44 in ?? ()
#73 0x5c203a5d in ?? ()
#74 0x6d742f22 in ?? ()
#75 0x6f632f70 in ?? ()
#76 0x7a69706d in ?? ()
#77 0x6172635f in ?? ()
#78 0x392d6873 in ?? ()
#79 0x2e393538 in ?? ()
#80 0x5c74756f in ?? ()
#81 0x72632022 in ?? ()
#82 0x65746165 in ?? ()
#83 0x220a2164 in ?? ()
#84 0x056baf00 in ?? ()
#85 0xb7f9eb59 in ?? () from /lib/ld-linux.so.2
#86 <signal handler called>
#87 0x00000000 in ?? ()
#88 0x0806cef6 in pushPlugin ()
#89 0x0805500f in eventLoop ()
#90 0x08051bc0 in main ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 9859

[CRASH_HANDLER]: "/tmp/compiz_crash-9859.out" created!

```

any help?

---

