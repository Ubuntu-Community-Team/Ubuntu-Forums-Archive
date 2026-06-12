---
title: "[SOLVED] Compiz fusion Broke after Upgrade."
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by [Alsharifi] on 2007-09-14
Using a readon x300 pci-e+XGL+fglrx and trevinos repos.

went to terminal today and did "sudo apt-get update +sudo apt-get upgrade"

it installed "compiz-plugins-extra + compiz-plugins-unofficial" and i couple more things.

and then rebooted and compiz starts for about 4 sec. and then it jumps back into metacity

when i run "compiz --replace" in terminal i get


```
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (animation) - Error: Unknown option "fie_color" in "fie_color=#00ff00,fire_particles=800,fire_smoke=]"
/usr/bin/compiz.real (animation) - Error: Unknown option "fie_color" in "fie_color=#00ff88,fire_particles=300,fire_smoke=]"
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: pictures/dark.png
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 16756
Reading symbols from /usr/lib/fglrx/libGL.so.1.2.xlibmesa...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/fglrx/libGL.so.1.2.xlibmesa
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
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
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
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
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213843776 (LWP 16756)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /usr/lib/libXrender.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /usr/lib/compiz/libput.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libtext.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libfadedesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfadedesktop.so
Reading symbols from /usr/lib/compiz/libdbus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libplace.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libwinrules.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwinrules.so
Reading symbols from /usr/lib/compiz/libmblur.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libextrawm.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libfade.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/librotate.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libscreensaver.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreensaver.so
ReUndefined command: "-e".  Try "help".
ading symbols from /usr/lib/libXss.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXss.so.1
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213843776 (LWP 16756)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c426a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7be9a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb557acfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfb64d88 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb557ae4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfb67986 in ?? ()
#8  0x00004174 in ?? ()
#9  0x082b4cb0 in ?? ()
#10 0x00004174 in ?? ()
#11 0x082b4cb0 in ?? ()
#12 0x00004174 in ?? ()
#13 0x00004174 in ?? ()
#14 0x082b4cb0 in ?? ()
#15 0xbfb6524b in ?? ()
#16 0xbfb65244 in ?? ()
#17 0xbfb65240 in ?? ()
#18 0x6f686365 in ?? ()
#19 0x20652d20 in ?? ()
#20 0x74657322 in ?? ()
#21 0x6f727020 in ?? ()
#22 0x0a74706d in ?? ()
#23 0x65726874 in ?? ()
#24 0x61206461 in ?? ()
#25 0x796c7070 in ?? ()
#26 0x6c6c6120 in ?? ()
#27 0x20746220 in ?? ()
#28 0x6c6c7566 in ?? ()
#29 0x6863650a in ?? ()
#30 0x5c5c206f in ?? ()
#31 0x650a6e5c in ?? ()
#32 0x206f6863 in ?? ()
#33 0x6e5c5c5c in ?? ()
#34 0x0a74620a in ?? ()
#35 0x74697571 in ?? ()
#36 0x203e2022 in ?? ()
#37 0x706d742f in ?? ()
#38 0x6264672f in ?? ()
#39 0x706d742e in ?? ()
#40 0x6264673b in ?? ()
#41 0x20712d20 in ?? ()
#42 0x7273752f in ?? ()
#43 0x6e69622f in ?? ()
#44 0x6d6f632f in ?? ()
#45 0x2e7a6970 in ?? ()
#46 0x6c616572 in ?? ()
#47 0x37363120 in ?? ()
#48 0x3c203635 in ?? ()
#49 0x6d742f20 in ?? ()
#50 0x64672f70 in ?? ()
#51 0x6d742e62 in ?? ()
#52 0x207c2070 in ?? ()
#53 0x70657267 in ?? ()
#54 0x20762d20 in ?? ()
#55 0x206f4e22 in ?? ()
#56 0x626d7973 in ?? ()
#57 0x74206c6f in ?? ()
#58 0x656c6261 in ?? ()
#59 0x207c2022 in ?? ()
#60 0x20656574 in ?? ()
#61 0x706d742f in ?? ()
#62 0x6d6f632f in ?? ()
#63 0x5f7a6970 in ?? ()
#64 0x73617263 in ?? ()
#65 0x36312d68 in ?? ()
#66 0x2e363537 in ?? ()
#67 0x3b74756f in ?? ()
#68 0x206d7220 in ?? ()
#69 0x2f20662d in ?? ()
#70 0x2f706d74 in ?? ()
#71 0x2e626467 in ?? ()
#72 0x3b706d74 in ?? ()
#73 0x68636520 in ?? ()
#74 0x0a22206f in ?? ()
#75 0x4152435b in ?? ()
#76 0x485f4853 in ?? ()
#77 0x4c444e41 in ?? ()
#78 0x3a5d5245 in ?? ()
#79 0x2f225c20 in ?? ()
#80 0x2f706d74 in ?? ()
#81 0x706d6f63 in ?? ()
#82 0x635f7a69 in ?? ()
#83 0x68736172 in ?? ()
#84 0x3736312d in ?? ()
#85 0x6f2e3635 in ?? ()
#86 0x225c7475 in ?? ()
#87 0x65726320 in ?? ()
#88 0x64657461 in ?? ()
#89 0x00220a21 in ?? ()
#90 0xbfb64e80 in ?? ()
#91 0xb7f41ff4 in ?? () from /lib/ld-linux.so.2
#92 0x00000001 in ?? ()
#93 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c426a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7be9a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb557acfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfb64d88 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb557ae4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfb67986 in ?? ()
#8  0x00004174 in ?? ()
#9  0x082b4cb0 in ?? ()
#10 0x00004174 in ?? ()
#11 0x082b4cb0 in ?? ()
#12 0x00004174 in ?? ()
#13 0x00004174 in ?? ()
#14 0x082b4cb0 in ?? ()
#15 0xbfb6524b in ?? ()
#16 0xbfb65244 in ?? ()
#17 0xbfb65240 in ?? ()
#18 0x6f686365 in ?? ()
#19 0x20652d20 in ?? ()
#20 0x74657322 in ?? ()
#21 0x6f727020 in ?? ()
#22 0x0a74706d in ?? ()
#23 0x65726874 in ?? ()
#24 0x61206461 in ?? ()
#25 0x796c7070 in ?? ()
#26 0x6c6c6120 in ?? ()
#27 0x20746220 in ?? ()
#28 0x6c6c7566 in ?? ()
#29 0x6863650a in ?? ()
#30 0x5c5c206f in ?? ()
#31 0x650a6e5c in ?? ()
#32 0x206f6863 in ?? ()
#33 0x6e5c5c5c in ?? ()
#34 0x0a74620a in ?? ()
#35 0x74697571 in ?? ()
#36 0x203e2022 in ?? ()
#37 0x706d742f in ?? ()
#38 0x6264672f in ?? ()
#39 0x706d742e in ?? ()
#40 0x6264673b in ?? ()
#41 0x20712d20 in ?? ()
#42 0x7273752f in ?? ()
#43 0x6e69622f in ?? ()
#44 0x6d6f632f in ?? ()
#45 0x2e7a6970 in ?? ()
#46 0x6c616572 in ?? ()
#47 0x37363120 in ?? ()
#48 0x3c203635 in ?? ()
#49 0x6d742f20 in ?? ()
#50 0x64672f70 in ?? ()
#51 0x6d742e62 in ?? ()
#52 0x207c2070 in ?? ()
#53 0x70657267 in ?? ()
#54 0x20762d20 in ?? ()
#55 0x206f4e22 in ?? ()
#56 0x626d7973 in ?? ()
#57 0x74206c6f in ?? ()
#58 0x656c6261 in ?? ()
#59 0x207c2022 in ?? ()
#60 0x20656574 in ?? ()
#61 0x706d742f in ?? ()
#62 0x6d6f632f in ?? ()
#63 0x5f7a6970 in ?? ()
#64 0x73617263 in ?? ()
#65 0x36312d68 in ?? ()
#66 0x2e363537 in ?? ()
#67 0x3b74756f in ?? ()
#68 0x206d7220 in ?? ()
#69 0x2f20662d in ?? ()
#70 0x2f706d74 in ?? ()
#71 0x2e626467 in ?? ()
#72 0x3b706d74 in ?? ()
#73 0x68636520 in ?? ()
#74 0x0a22206f in ?? ()
#75 0x4152435b in ?? ()
#76 0x485f4853 in ?? ()
#77 0x4c444e41 in ?? ()
#78 0x3a5d5245 in ?? ()
#79 0x2f225c20 in ?? ()
#80 0x2f706d74 in ?? ()
#81 0x706d6f63 in ?? ()
#82 0x635f7a69 in ?? ()
#83 0x68736172 in ?? ()
#84 0x3736312d in ?? ()
#85 0x6f2e3635 in ?? ()
#86 0x225c7475 in ?? ()
#87 0x65726320 in ?? ()
#88 0x64657461 in ?? ()
#89 0x00220a21 in ?? ()
#90 0xbfb64e80 in ?? ()
#91 0xb7f41ff4 in ?? () from /lib/ld-linux.so.2
#92 0x00000001 in ?? ()
#93 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 16756

[CRASH_HANDLER]: "/tmp/compiz_crash-16756.out" created!

Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"
Window manager warning: Screen 0 on display "localhost:1.0" already has a window manager; try using the --replace option to replace the current window manager.


```




any ideas will be much appreciated!

---

### Post by Forlong on 2007-09-14
The screensaver plugin brakes Compiz in Treviño's repository. Disable it in CCSM and you should be fine.

Please do a search in the forums next time, this issue has been address a lot lately.
And also keep in mind that bleeding edge git-packages have the tendency to break sometimes.

---

### Post by [Alsharifi] on 2007-09-14
thanx alot the fixed the problem.

i did a search,but on this forum ever time i search all kinds of unrelated threads come up..mabey im not using the search feature right.

---

### Post by spacebetween on 2007-09-14
It does the same thing for me, and I don't have the screesaver plugin turned on.

This isn't solved yet!

---

### Post by [Alsharifi] on 2007-09-14
humm did u double check?

run in terminal 

```
compiz --replace
```

and post what u get.

---

### Post by spacebetween on 2007-09-14
I get this:

```
ryan@matthew:~$ compiz --replace
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/rotate/allscreens/options/initiate_button. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

---

### Post by [Alsharifi] on 2007-09-14
thats exactly what i got....u SURE the screen saver plugin is not enabled?..

go to to compiz setting manager and it will be in extras.

---

### Post by spacebetween on 2007-09-14
> **'[Alsharifi] said:**
> thats exactly what i got....u SURE the screen saver plugin is not enabled?..

go to to compiz setting manager and it will be in extras.

100% sure. I've even reset to default settings a few times -- still the same thing AND with screensaver plugin disabled!!

ahhh this is annoying

---

### Post by Forlong on 2007-09-14
Then try disabling one plugin at a time. Opacify might be a good start.

---

### Post by spacebetween on 2007-09-14
> **Forlong said:**
> Then try disabling one plugin at a time. Opacify might be a good start.

Sure enough, disabling opacify has solved the problem. I hope it's fixed in future updates.

---

### Post by smartboyathome on 2007-09-14
You might want to uninstall Trevino's repo and install Amaranth's. Amaranth's is more stable since it is backported from gutsy, and even though it isn't the most bleeding edge, I would recommend it to anyone who isn't trying to develop code.

---

