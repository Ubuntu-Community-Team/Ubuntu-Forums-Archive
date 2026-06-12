---
title: "[SOLVED] Did Today's Update Break Your Compiz-Fusion?"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-09-13
Mine was fine until the compiz updates.

Any one else with a compiz-fusion that won't load now?

---

### Post by Ub1476 on 2007-09-13
Same problem on ATI X1400.

---

### Post by coldstatue on 2007-09-13
Here's what I get running from a console:

```
$ compiz --replace -c emerald &
[1] $ /usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/animation/screen0/options/fire_direction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (group) - Warn: No compatible text plugin loaded.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (shift) - Warn: No compatible text plugin loaded.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/switcher/allscreens/options/next_button. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 8454
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
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
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
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1223321888 (LWP 8454)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
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
Reading symbols from /usr/lib/compiz/libclone.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libclone.so
Reading symbols from /usr/lib/compiz/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libglib.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libplace.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libwater.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwater.so
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
Reading symbols from /usr/lib/compiz/libput.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libring.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libring.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libgroup.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /usr/lib/compiz/libshowdesktop.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libshift.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libcube.so...
(no debugging symbols found)...done.
LoUndefined command: "-e".  Try "help".
aded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libscale.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libswitcher.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libcubereflex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcubereflex.so
Reading symbols from /usr/lib/compiz/libscreensaver.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXss.so.1
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1223321888 (LWP 8454)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c876a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c2ea3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb462ecfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfdf7018 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb462ee4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfdf9979 in ?? ()
#8  0x00002106 in ?? ()
#9  0x08552d78 in ?? ()
#10 0x00002106 in ?? ()
#11 0x08552d78 in ?? ()
#12 0x00002106 in ?? ()
#13 0x00002106 in ?? ()
#14 0x08552d78 in ?? ()
#15 0xbfdf74db in ?? ()
#16 0xbfdf74d4 in ?? ()
#17 0xbfdf74d0 in ?? ()
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
#47 0x35343820 in ?? ()
#48 0x203c2034 in ?? ()
#49 0x706d742f in ?? ()
#50 0x6264672f in ?? ()
#51 0x706d742e in ?? ()
#52 0x67207c20 in ?? ()
#53 0x20706572 in ?? ()
#54 0x2220762d in ?? ()
#55 0x73206f4e in ?? ()
#56 0x6f626d79 in ?? ()
#57 0x6174206c in ?? ()
#58 0x22656c62 in ?? ()
#59 0x74207c20 in ?? ()
#60 0x2f206565 in ?? ()
#61 0x2f706d74 in ?? ()
#62 0x706d6f63 in ?? ()
#63 0x635f7a69 in ?? ()
#64 0x68736172 in ?? ()
#65 0x3534382d in ?? ()
#66 0x756f2e34 in ?? ()
#67 0x72203b74 in ?? ()
#68 0x662d206d in ?? ()
#69 0x6d742f20 in ?? ()
#70 0x64672f70 in ?? ()
#71 0x6d742e62 in ?? ()
#72 0x65203b70 in ?? ()
#73 0x206f6863 in ?? ()
#74 0x435b0a22 in ?? ()
#75 0x48534152 in ?? ()
#76 0x4e41485f in ?? ()
#77 0x52454c44 in ?? ()
#78 0x5c203a5d in ?? ()
#79 0x6d742f22 in ?? ()
#80 0x6f632f70 in ?? ()
#81 0x7a69706d in ?? ()
#82 0x6172635f in ?? ()
#83 0x382d6873 in ?? ()
#84 0x2e343534 in ?? ()
#85 0x5c74756f in ?? ()
#86 0x72632022 in ?? ()
#87 0x65746165 in ?? ()
#88 0x220a2164 in ?? ()
#89 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c876a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c2ea3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb462ecfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfdf7018 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb462ee4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfdf9979 in ?? ()
#8  0x00002106 in ?? ()
#9  0x08552d78 in ?? ()
#10 0x00002106 in ?? ()
#11 0x08552d78 in ?? ()
#12 0x00002106 in ?? ()
#13 0x00002106 in ?? ()
#14 0x08552d78 in ?? ()
#15 0xbfdf74db in ?? ()
#16 0xbfdf74d4 in ?? ()
#17 0xbfdf74d0 in ?? ()
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
#47 0x35343820 in ?? ()
#48 0x203c2034 in ?? ()
#49 0x706d742f in ?? ()
#50 0x6264672f in ?? ()
#51 0x706d742e in ?? ()
#52 0x67207c20 in ?? ()
#53 0x20706572 in ?? ()
#54 0x2220762d in ?? ()
#55 0x73206f4e in ?? ()
#56 0x6f626d79 in ?? ()
#57 0x6174206c in ?? ()
#58 0x22656c62 in ?? ()
#59 0x74207c20 in ?? ()
#60 0x2f206565 in ?? ()
#61 0x2f706d74 in ?? ()
#62 0x706d6f63 in ?? ()
#63 0x635f7a69 in ?? ()
#64 0x68736172 in ?? ()
#65 0x3534382d in ?? ()
#66 0x756f2e34 in ?? ()
#67 0x72203b74 in ?? ()
#68 0x662d206d in ?? ()
#69 0x6d742f20 in ?? ()
#70 0x64672f70 in ?? ()
#71 0x6d742e62 in ?? ()
#72 0x65203b70 in ?? ()
#73 0x206f6863 in ?? ()
#74 0x435b0a22 in ?? ()
#75 0x48534152 in ?? ()
#76 0x4e41485f in ?? ()
#77 0x52454c44 in ?? ()
#78 0x5c203a5d in ?? ()
#79 0x6d742f22 in ?? ()
#80 0x6f632f70 in ?? ()
#81 0x7a69706d in ?? ()
#82 0x6172635f in ?? ()
#83 0x382d6873 in ?? ()
#84 0x2e343534 in ?? ()
#85 0x5c74756f in ?? ()
#86 0x72632022 in ?? ()
#87 0x65746165 in ?? ()
#88 0x220a2164 in ?? ()
#89 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 8454

[CRASH_HANDLER]: "/tmp/compiz_crash-8454.out" created!

Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"



```

---

### Post by ashdezign on 2007-09-13
Mine is broken to. Right after update. Nvidea graphics card. Compiz worked fine before, since the update it fails to start

---

### Post by coldstatue on 2007-09-13
BAD NEWS - Resetting to defaults under the prefs of the configuration window fixes it..Importing old settings breaks it.

 Starting from scratch... AGAIN!

---

### Post by ashdezign on 2007-09-13
> **coldstatue said:**
> BAD NEWS - Resetting to defaults under the prefs of the configuration window fixes it..Importing old settings breaks it.

 Starting from scratch... AGAIN!


Doh!

I guess this is why its called bleeding edge!

Anyway, resetting to defaults worked, thanks for the heads up.

---

### Post by coldstatue on 2007-09-13
Don't turn the screen saver plug back on. That killed it for me. Otherwise, it looks fine so far.

---

### Post by coldstatue on 2007-09-13
I'm getting pretty good at setting up CF how I like it. I've done it so many times now, i can have all settings back to my old profile's within 10 minutes. :0)

At least it works again. I'm happy.

---

### Post by ronmarley1 on 2007-09-13
> **ashdezign said:**
> Doh!

I guess this is why its called bleeding edge!

Anyway, resetting to defaults worked, thanks for the heads up.

Resetting to defaults works for me also.  IBM R51 laptop with Intel graphics.

---

### Post by ronmarley1 on 2007-09-13
Looks like this update may also have some stability issues.  I turned on 3D windows, found that it worked a little funky, and when I turned it off, compiz fusion crashed.  It's never crashed on me since I moved from Beryl to Compiz Fusion.  As the poster above said, "bleeding edge!"

---

### Post by jauchter on 2007-09-13
This got compiz working for me again, but I have a new problem

I cant activate any plugins that arent turned on by default in the configuration manager

anyone else seeing this?  Am I missing something obvious?

Edit: in my clicking around, trying to get it working again this morning, I must have unchecked the 'automatic plugin sorting' in the 'plugins' tab under preferences
turning that option back on solved the problem

---

### Post by Izobalax on 2007-09-13
Well, I've tried the advice in this thread and I've got Compiz-Fusion working again... but not emerald. Running the command:

```
emerald --replace
```

...is no longer recognised. 

Any ideas?

/izo

---

### Post by drvista on 2007-09-13
YOU can simply if had update and your system made compiz-fusion down 
boot to recovery mode 
in terminal run as root
dpkg-reconfigure -phigh xserver-xoeg
then reboot
start as normal boot
install xserver-xgl from synaptic
install restricted drivers
that worked for me i hope it works for you
:)

---

### Post by Islington on 2007-09-13
This is the first time compiz fusion has crashed on me. Almost forgot that this was bleeding edge. Thanks for the solution though, resetting got it work again.

---

### Post by ashdezign on 2007-09-13
Anyone notice any funkiness with rotating the cube? The window that is visible when you start rotating the cube rotates with the cube whether you want it to or not. When you rotate using the mouse the cube drops back behind the visible window and you can barely see it.

Drag and Drop windows to new face of the cube also  has funkiness. The window you are rotating, rotates with you, disappears then reappears.

Other strangeness as well. I think this latest update is definitely unstable.
> 
" I cant activate any plugins that arent turned on by default in the configuration manager

anyone else seeing this?  Am I missing something obvious?"

No problems here though turning on some plugins causes compiz to crash. Turning the plugins on then restarting compiz seems to get around it.

---

### Post by Hawk__0 on 2007-09-13
> **ashdezign said:**
> Anyone notice any funkiness with rotating the cube? The window that is visible when you start rotating the cube rotates with the cube whether you want it to or not. When you rotate using the mouse the cube drops back behind the visible window and you can barely see it.

Drag and Drop windows to new face of the cube also  has funkiness. The window you are rotating, rotates with you, disappears then reappears.

Other strangeness as well. I think this latest update is definitely unstable.


No problems here though turning on some plugins causes compiz to crash. Turning the plugins on then restarting compiz seems to get around it.

ya im having those rotating funks as well.  its really pissing me off lol.
nvidia 7600GT

---

### Post by ashdezign on 2007-09-13
> ya im having those rotating funks as well.  its really pissing me off lol.
nvidia 7600GT


disable 3d windows. that solved it for me. compiz will crash when you disable it though, so you will have to restart compiz.

---

### Post by dahlheim on 2007-09-13
it broke mine.  was working fine, now manually rotating the cube, and other mundane things like selecting one of the url's in nautilus' address bar history, either freeze the system or crash compiz.

EDIT:  it seems fixed after de-installing and re-installing compiz packages.  :)

EDIT2:  and then freezes system again (still in x, pointer moves w/mouse, only sysrq can get me back out) when i go to compiz settings manager, and untic wobblies and tic animation.

---

### Post by dafyre on 2007-09-14
I haven't had too many problems with the Compiz-Fusion.  If I get a working install, I don't update it for at least a few weeks.:lolflag:

I have found that some of the plugins won't compile using the CF-Installer scripts, but they can be installed by hand....  so you can cd to the folder that has the plugin source in it, and issue:

sudo make

and then fix the problems that are listed.  If there's a problem with the code in the plugin, of course that can't be fixed, otherwise, keep hacking away at it and you'll get [insert favorite plugin here] installed.

I have to do this for the Group Tabs, as well as the Ring switcher.... Just thought I'd throw 2c. in.

---

### Post by spacebetween on 2007-09-14
It seems like most of my plugins don't work, even after resetting to defaults. Anyone else still having problems?

EDIT: Actually, I have problems involving windows. For example, I can't use any of the window Switchers (App/Ring/Shift). Also, the cube doesn't work. When I try to use any of these, Compiz seems to just turn off, and I have to use compiz --replace.

And, randomly, while I'm in Firefox, Compiz just turns off. Another edit: I think the crashing of Compiz in FF has something to do with text form boxes -- on websites, or even in the address bar/google search bar.

---

### Post by Mongo5000 on 2007-09-14
I was just debating whether to upgrade or not since its available but i'll sit tight for a bit and see how things pan out.

When it is getting out of alpha testing?

---

### Post by [Alsharifi] on 2007-09-14
jsut turning off the screensaver plugin fixed it for me.

---

### Post by spacebetween on 2007-09-14
> **'[Alsharifi] said:**
> jsut turning off the screensaver plugin fixed it for me.

I don't even have the screensaver plugin on.

AHHH THIS IS SO ANNOYING!

---

### Post by CC_machine on 2007-09-14
IMPORTANT: (well kind of): DON'T reset your settings, disable the screensaver plugin! or try all the window management plugins, if that doesn't.

---

### Post by patchoro on 2007-09-14
Since last issues with trevino I switched to use Amaranth's repo. When i once more had achieved a stable 3d situation I decided to no longer be bleeding edge. I only do upgrades AFTER I have checked the forums for responses on new editions. 

Which now proves itself to be a solid stategy.

---

### Post by Rupertronco on 2007-09-14
> **patchoro said:**
> Since last issues with trevino I switched to use Amaranth's repo. When i once more had achieved a stable 3d situation I decided to no longer be bleeding edge. I only do upgrades AFTER I have checked the forums for responses on new editions. 

Which now proves itself to be a solid stategy.

Amen, this has been my strategy for a few months now. Thanks to the above posters for enabling me to stick with my current setup, where all the plug-ins work!

---

### Post by crimesaucer on 2007-09-14
> **coldstatue said:**
> Don't turn the screen saver plug back on. That killed it for me. Otherwise, it looks fine so far.

My update also caused a problem with starting Compiz and Emerald. Turning off the screen saver plug-in did the trick for me...everything else seems the same for me.

Thanks coldstatue.

---

### Post by Nicram on 2007-09-15
> **crimesaucer said:**
> My update also caused a problem with starting Compiz and Emerald. Turning off the screen saver plug-in did the trick for me...everything else seems the same for me.

Thanks coldstatue.


The same here.
Thanks coldstatue.

---

