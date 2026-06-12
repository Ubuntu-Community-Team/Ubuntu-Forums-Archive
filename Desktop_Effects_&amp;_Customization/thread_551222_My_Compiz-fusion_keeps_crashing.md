---
title: "My Compiz-fusion keeps crashing"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-09-14
I just installed some Compiz-fusion updates, and now compiz crashes whenever I start it.  Here's the debug file:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 12686
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
Reading symbols from /usr/lib/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213610304 (LWP 12686)]
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
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libzoom.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libwinrules.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwinrules.so
Reading symbols from /usr/lib/compiz/lib3d.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/lib3d.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libdbus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libworkarounds.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libcube.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libscreensaver.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXss.so.1
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213610304 (LWP 12686)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c7b6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c22a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5a59cfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfb18098 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb5a59e4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfb1acc1 in ?? ()
#8  0x0000318e in ?? ()
#9  0x081a26d8 in ?? ()
#10 0x0000318e in ?? ()
#11 0x081a26d8 in ?? ()
#12 0x0000318e in ?? ()
#13 0x0000318e in ?? ()
#14 0x081a26d8 in ?? ()
#15 0xbfb18538 in ?? ()
#16 0x00000008 in ?? ()
#17 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c7b6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c22a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5a59cfc in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfb18098 in ?? ()
#5  0x00000400 in ?? ()
#6  0xb5a59e4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#7  0xbfb1acc1 in ?? ()
#8  0x0000318e in ?? ()
#9  0x081a26d8 in ?? ()
#10 0x0000318e in ?? ()
#11 0x081a26d8 in ?? ()
#12 0x0000318e in ?? ()
#13 0x0000318e in ?? ()
#14 0x081a26d8 in ?? ()
#15 0xbfb18538 in ?? ()
#16 0x00000008 in ?? ()
#17 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 12686
```

Does anyone know what the problem is?  Also, could I just revert back to before I installed the updates?

Thanks.

---

### Post by Yes on 2007-09-19
I just reinstalled everything to do with compiz, and it still crashes.  Any ideas?

---

### Post by alvarez1900 on 2007-09-19
I just updated my wifes upstairs computer and compiz crashes when trying to use any of the effects... the animations will work but anything that lasts like 5 seconds or more will crash (cube, water, fire, unfold, etc...)

---

### Post by Yes on 2007-09-19
I just downloaded the latest updates, and it still happens.  Here's the output from the terminal:

```
/usr/bin/compiz.real (core) - Error: no 'cube' plugin with ABI version '20070917' loaded

/usr/bin/compiz.real (3d) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin '3d'
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
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 14925
Reading symbols from /usr/lib/libXcomposite.so.1...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libSM.so.6...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libXcursor.so.1...done.
Loaded symbols for /usr/lib/libXcursor.so.1
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
Reading symbols from /usr/lib/libz.so.1...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213729088 (LWP 14925)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libgobject-2.0.so.0...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libzoom.so...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libwinrules.so...done.
Loaded symbols for /usr/lib/compiz/libwinrules.so
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libregex.so...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libdbus.so...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libcube.so...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libscreensaver.so...done.
Loaded symbols for /usr/lib/compiz/libscreensaver.so
Reading symbols from /usr/lib/libXss.so.1...done.
Loaded symbols for /usr/lib/libXss.so.1
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1Undefined command: "-e".  Try "help".

0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213729088 (LWP 14925)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c5e6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c05a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5a3ccfc in crash_handler (sig=11) at crashhandler.c:59
        count = 1
#4  <signal handler called>
#5  0x08052c49 in allocatePrivateIndex (len=0x80799a0, indices=0x807999c, 
    reallocProc=0x805ae00 <reallocScreenPrivate>, closure=0x8079980)
    at privates.c:41
        i = 0
#6  0x0805da07 in allocScreenObjectPrivateIndex (parent=0x8079980)
    at screen.c:76
No locals.
#7  0x0805d949 in allocateScreenPrivateIndex (display=0x8079980)
    at screen.c:148
No locals.
#8  0xb57d3b69 in screenSaverInitDisplay (p=0x82bacc0, d=0x8079980)
    at screensaver.cpp:351
        sd = (ScreenSaverDisplay *) 0x836dd58
#9  0xb57d2e49 in screenSaverInitObject (p=0x82bacc0, o=0x8079980)
    at screensaver.cpp:397
        dispTab = {0xb57d3b0c <screenSaverInitDisplay>, 
  0xb57d34de <screenSaverInitScreen>, 0xb57d336e <screenSaverInitWindow>}
#10 0xb57dba8b in screensaverOptionsInitObjectWrapper (p=0x82bacc0, 
    o=0x8079980) at build/screensaver_options.c:641
        rv = 1
#11 0x0806f54d in initObjectTree (object=0x8079980, closure=0xbff1618c)
    at plugin.c:369
        p = (CompPlugin *) 0x82bacc0
        ctx = {plugin = 0x0, type = 4294967295}
#12 0x0806f7b4 in pushPlugin (p=0x82bacc0) at plugin.c:444
        ctx = {plugin = 0x82bacc0, object = 0x8079980}
#13 0x080585ee in eventLoop () at display.c:1017
        event = {type = 22, xany = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, window = 77}, xkey = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, window = 77, root = 18874413, 
    subwindow = 140, time = 657, x = 743, y = 111, x_root = 0, 
    y_root = 18874382, state = 0, keycode = 0, same_screen = 3073}, xbutton = {
    type = 22, serial = 6430, send_event = 0, display = 0x8085a10, 
    window = 77, root = 18874413, subwindow = 140, time = 657, x = 743, 
    y = 111, x_root = 0, y_root = 18874382, state = 0, button = 0, 
    same_screen = 3073}, xmotion = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, window = 77, root = 18874413, subwindow = 140, 
    time = 657, x = 743, y = 111, x_root = 0, y_root = 18874382, state = 0, 
    is_hint = 0 '\0', same_screen = 3073}, xcrossing = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    root = 18874413, subwindow = 140, time = 657, x = 743, y = 111, 
    x_root = 0, y_root = 18874382, mode = 0, detail = 0, same_screen = 3073, 
    focus = 136174192, state = 3083915600}, xfocus = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    mode = 18874413, detail = 140}, xexpose = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, window = 77, x = 18874413, y = 140, 
    width = 657, height = 743, count = 111}, xgraphicsexpose = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, drawable = 77, 
    x = 18874413, y = 140, width = 657, height = 743, count = 111, 
    major_code = 0, minor_code = 18874382}, xnoexpose = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, drawable = 77, 
    major_code = 18874413, minor_code = 140}, xvisibility = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    state = 18874413}, xcreatewindow = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, parent = 77, window = 18874413, 
    x = 140, y = 657, width = 743, height = 111, border_width = 0, 
    override_redirect = 18874382}, xdestroywindow = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, event = 77, window = 18874413}, 
  xunmap = {type = 22, serial = 6430, send_event = 0, display = 0x8085a10, 
    event = 77, window = 18874413, from_configure = 140}, xmap = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, event = 77, 
    window = 18874413, override_redirect = 140}, xmaprequest = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, parent = 77, 
    window = 18874413}, xreparent = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, event = 77, window = 18874413, parent = 140, x = 657, 
    y = 743, override_redirect = 111}, xconfigure = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, event = 77, window = 18874413, 
    x = 140, y = 657, width = 743, height = 111, border_width = 0, 
    above = 18874382, override_redirect = 0}, xgravity = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, event = 77, 
    window = 18874413, x = 140, y = 657}, xresizerequest = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    width = 18874413, height = 140}, xconfigurerequest = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, parent = 77, 
    window = 18874413, x = 140, y = 657, width = 743, height = 111, 
    border_width = 0, above = 18874382, detail = 0, value_mask = 0}, 
  xcirculate = {type = 22, serial = 6430, send_event = 0, display = 0x8085a10, 
    event = 77, window = 18874413, place = 140}, xcirculaterequest = {
    type = 22, serial = 6430, send_event = 0, display = 0x8085a10, 
    parent = 77, window = 18874413, place = 140}, xproperty = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    atom = 18874413, time = 140, state = 657}, xselectionclear = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, window = 77, 
    selection = 18874413, time = 140}, xselectionrequest = {type = 22, 
    serial = 6430, send_event = 0, display = 0x8085a10, owner = 77, 
    requestor = 18874413, selection = 140, target = 657, property = 743, 
    time = 111}, xselection = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, requestor = 77, selection = 18874413, target = 140, 
    property = 657, time = 743}, xcolormap = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, window = 77, colormap = 18874413, 
    new = 140, state = 657}, xclient = {type = 22, serial = 6430, 
    send_event = 0, display = 0x8085a10, window = 77, message_type = 18874413, 
    format = 140, data = {
      b = "\221\002\000\000&#65533;\002\000\000o\000\000\000\000\000\000\000\016\000 \001", s = {657, 0, 743, 0, 111, 0, 0, 0, 14, 288}, l = {657, 743, 111, 0, 
        18874382}}}, xmapping = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, window = 77, request = 18874413, first_keycode = 140, 
    count = 657}, xerror = {type = 22, display = 0x191e, resourceid = 0, 
    serial = 134765072, error_code = 77 'M', request_code = 0 '\0', 
    minor_code = 0 '\0'}, xkeymap = {type = 22, serial = 6430, send_event = 0, 
    display = 0x8085a10, window = 77, 
    key_vector = "-\000 \001\214\000\000\000\221\002\000\000&#65533;\002\000\000o\000\000\000\000\000\000\000\016\000 \001\000\000\000"}, pad = {22, 6430, 0, 
    134765072, 77, 18874413, 140, 657, 743, 111, 0, 18874382, 0, 0, 3073, 
    136174192, -1211051696, 136151884, 136165720, 136176136, 136352920, 
    136176200, 136165592, 136285136}}
        timeDiff = <value optimized out>
        tv = {tv_sec = 1190252986, tv_usec = 692702}
        d = (CompDisplay *) 0x83450ec
        s = (CompScreen *) 0x83450ec
        w = <value optimized out>
        time = <value optimized out>
        timeToNextRedraw = 0
        damageMask = 4
        mask = <value optimized out>
#14 0x08052803 in main (argc=5, argv=0xbff16774) at main.c:461
        size = 1
        ctx = {offset = 3960, pluginData = 0x807a008 "\003", 
  textureFilterData = 0x0, refreshRateData = 0x0}
        displayName = 0x0
        plugin = {0xbff169e6 "ccp", 0xb7a9425c "trstr", 0xb7a9425f "tr", 0x0, 
  0x0, 0x1 <Address 0x1 out of bounds>, 0x364 <Address 0x364 out of bounds>, 
  0xb7a80ae0 "&#65533;S&#65533;&#65533;\020ii\r", 0xb7ec6d58 "", 0xb7a9425b "strstr", 
  0xb7bdb7a8 "", 0xb7a93078 "&#65533;", 0x1 <Address 0x1 out of bounds>, 
  0xb7f5eff4 "(\237\001", 0xb7aae468 "<&#65533;&#65533;&#65533;", 0xbff163a8 "hb&#65533;&#65533;Xm&#65533;&#65533;", 
  0xbff163c4 "", 0xb7f4e103 "\203&#65533;", 0xb7a93078 "&#65533;", 0xbff163a8 "hb&#65533;&#65533;Xm&#65533;&#65533;", 
  0xb7f5f83c "&#65533;y\034\b#", 0x0, 0xb7a80ae0 "&#65533;S&#65533;&#65533;\020ii\r", 
  0x1 <Address 0x1 out of bounds>, 0x0, 0x1 <Address 0x1 out of bounds>, 
  0xbff1633c "\001", 
  0xb7f54fa8 "\205&#65533;t\027\2118\203&#65533;\b\211F\004\211&#65533;\213]&#65533;\213u&#65533;\213}&#65533;\211&#65533;]&#65533;1&#65533;&#65533;&#65533;\211&#65533;\215&#65533;'", 0x11 <Address 0x11 out of bounds>, 
  0x8 <Address 0x8 out of bounds>, 0xb7f45468 "", 
  0xbff163b4 "&#65533;\232&#65533;\a&#65533;&#65533;&#65533;&#65533;&#65533;&#10935;x0&#65533;&#65533;", 0xb7a7f000 "", 
  0x1 <Address 0x1 out of bounds>, 0xbff16370 "\210", 0xbff163f0 "M", 
  0xb7aae2b0 "", 0xb7a9425b "strstr", 
  0x1000000 <Address 0x1000000 out of bounds>, 
  0x1c93db57 <Address 0x1c93db57 out of bounds>, 0x0, 0x0, 
  0xb7f5d434 "_dl_allocate_tls_init", 0x0, 0xb7f5d434 "_dl_allocate_tls_init", 
  0xb7f45700 "l\236\001", 0x88 <Address 0x88 out of bounds>, 0x0, 0x0, 0x0, 
  0xb7a96300 "U\211&#65533;\203&#65533;\024\211]&#65533;\213M\f\211u&#65533;\211}&#65533;&#65533;C&#65533;&#65533;&#65533;\201&#65533;&#65533;
  0x10000004 <Address 0x10000004 out of bounds>, 
  0xb7f31000 <Address 0xb7f31000 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x0, 0xb7bd6268 "\030G", 0xb7ec6d58 "", 0x0, 
  0x7ab9ab2 <Address 0x7ab9ab2 out of bounds>, 0xb7f5eff4 "(\237\001", 
  0xb7aae2b0 "", 0xb7a93078 "&#65533;", 
  0xbff16400 "&#65533;\022&#65533;&#65533;&#65533;\022&#65533;&#65533;&#65533;d&#65533; &#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4d&#65533;&#65533;&#65533;f&#65533;&#65533;zg&#65533;&#65533;&#65533;d&#65533;&#65533;&#65533;\022&#65533;&#65533;", 
  0xb7f51e52 "\213U&#65533;\203&#65533;\024\211&#65533;1&#65533;\205&#65533;t\t\205&#65533;t\002\213\001\003B\004\213\213\030&#65533;&#65533;&#65533;\205&#65533;u\t\213M&#65533;\213U&#65533;\211\004\021\215e&#65533;[^_]&#65533;1&#65533;&#65533;\223\215\203&#65533;&#65533;&#65533;&#65533;\211D$\f\215\203&#65533;&#65533;&#65533;&#65533;\211D$\004\215\203&#65533;&#65533;&#65533;&#65533;&#65533;D$\bM", 0xb7aae468 "<&#65533;&#65533;&#65533;", 
  0xb7a80ae0 "&#65533;S&#65533;&#65533;\020ii\r", 0x1 <Address 0x1 out of bounds>, 
  0x1 <Address 0x1 out of bounds>, 0x0, 0xb7a9425b "strstr", 
  0x34 <Address 0x34 out of bounds>, 0xb7a92000 "\177ELF\001\001\001", 
  0x500140b8 <Address 0x500140b8 out of bounds>, 
  0x4d <Address 0x4d out of bounds>, 0x0, 0xb7a7f6bc "", 0xbff16434 "Linux", 
  0xb7aa12ba "MP", 0xb7aa12bc "", 
  0x20f164f7 <Address 0x20f164f7 out of bounds>, 
  0xbff164fd " Fri Aug 31 00:55:27 UTC 2007", 0xb7a7f6bc "", 
  0xbff16434 "Linux", 0xbff166d8 "Hg&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V\a\bHg&#65533;&#65533;&#65533;N&#65533;&#65533;\005", 
  0xb7a9677a "\205&#65533;\017\225&#65533;\017&#65533;&#65533;\211\203&#65533;!", 
  0xbff164f7 "#2 SMP Fri Aug 31 00:55:27 UTC 2007", 0xb7aa12b9 "SMP", 0x0, 
  0x0, 0xbff16638 "<&#65533;&#65533;&#65533;", 0x756e694c <Address 0x756e694c out of bounds>, 
  0x78 <Address 0x78 out of bounds>, 0x0 <repeats 14 times>, 
  0x656c6100 <Address 0x656c6100 out of bounds>, 
  0x65642d78 <Address 0x65642d78 out of bounds>, 
  0x6f746b73 <Address 0x6f746b73 out of bounds>, 
  0x70 <Address 0x70 out of bounds>, 0x0 <repeats 12 times>, 
  0x2e320000 <Address 0x2e320000 out of bounds>, 
  0x30322e36 <Address 0x30322e36 out of bounds>, 
  0x2d36312d <Address 0x2d36312d out of bounds>, 
  0x656e6567 <Address 0x656e6567 out of bounds>, 
  0x636972 <Address 0x636972 out of bounds>, 0x0 <repeats 11 times>, 
  0x23000000 <Address 0x23000000 out of bounds>, 
  0x4d532032 <Address 0x4d532032 out of bounds>, 
  0x72462050 <Address 0x72462050 out of bounds>, 
  0x75412069 <Address 0x75412069 out of bounds>, 
  0x31332067 <Address 0x31332067 out of bounds>, 
  0x3a303020 <Address 0x3a303020 out of bounds>, 
  0x323a3535 <Address 0x323a3535 out of bounds>, 
  0x54552037 <Address 0x54552037 out of bounds>, 
  0x30322043 <Address 0x30322043 out of bounds>, 
  0x3730 <Address 0x3730 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x36383669 <Address 0x36383669 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x0, 0x0, 0x0, 0x804fd1c "GLIBC_2.1", 
  0xd696910 <Address 0xd696910 out of bounds>, 0xb7bdafa8 "&#65533;*", 
  0xbff165a4 "(f&#65533;&#65533;B&#65533;&#65533;&#65533;", 
  0xb7f4db79 "\205&#65533;\017\204r&#65533;&#65533;&#65533;\213E&#65533;\213@\b\205&#65533;\017\205b&#65533;&#65533;&#65533;\205&#65533;\017\205Z&#65533;&#65533;&#65533;f\203}&#65533;", 0xb7be0cd4 "GLIBC_2.0", 0x804fd12 "GLIBC_2.0", 
  0xb7ec6d0c "cursor.so.1", 0xb7ec6cfc "\bm&#65533;&#65533;", 
  0xb7a80020 "\022&#65533;\004\b\020ii\r", 
  0xbff10002 ";?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--->{{;?77w?--"..., 
  0xb7f52c69 "\205&#65533;u&#65533;\203&#65533;\b&#65533;\001", 0x804d89d "libc.so.6", 
  0xb7ec6d08 "libXcursor.so.1", 0xb7f5eff4 "(\237\001", 0xb7aaefa4 "Xm&#65533;&#65533;", 
  0xe <Address 0xe out of bounds>, 0xbff16628 "&#65533;f&#65533;&#65533;\003&#65533;&#65533;&#65533;L&#65533;\004\b&#65533;f&#65533;&#65533;<&#65533;&#65533;&#65533;", 
  0xb7f4df42 "\205&#65533;t&#65533;&#65533;\235&#65533;&#65533;&#65533;\220\215t&", 0x0, 0x0, 0x0, 0x0, 
  0x123 <Address 0x123 out of bounds>, 
  0x3d8f5 <Address 0x3d8f5 out of bounds>, 0xbff165f4 "", 0xbff165f4 "", 
  0xbff166e4 "&#65533;V\a\bHg&#65533;&#65533;&#65533;N&#65533;&#65533;\005", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0xb7ec6d58 "", 
  0x1a <Address 0x1a out of bounds>, 0xb7bd2c28 "", 
  0xb7bd2a28 "/N=&#65533;&#65533;\030L\017&#65533;&#65533;-&#65533;\204\"\233|&#65533;&#65533;\217&#65533;\205\"\233|&#65533;&#65533;&#65533;=&#65533;\"\225&#65533;8&#65533;\031u&#65533;\001&#65533;\022&#65533;BY\020&#65533;&#65533;&#52598;w\035\rG&#65533;&#65533;%&#65533;V1&#65533;&#65533;r1\035\a;&#65533;L\214\t)\020\t~\222\0348&#65533;&#65533;0j&#65533;&#65533;{\004\\H&#65533;&#1313;\034&#65533;\002&#65533;&#65533;\0179&#65533;&#65533;0X?\227|\030\034s&#65533;T\200&#65533;s&#65533;\202c\002;H\205\0336\rf&#65533;2v&#65533;&#1384;&#65533;K&#65533;&#65533;\234#\217&#65533;\036h\233&#65533;\230&#65533;&#65533;\234\002Y1\n&#65533;\006&#2045;&#65533;e\235J\032\223&#65533;P&#65533;&#65533;\020\205)%~\016|\030&#65533;&#65533;8\a\221\222&#65533;\206&#65533;&#65533;:V&#65533;&#65533;I&#65533;$\202&#65533;7&#65533;Qho&#65533;&#65533;&#65533;\017l"..., 
  0x804da6d "__libc_start_main", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0x804da79 "_main", 
  0x804da71 "bc_start_main"...}
        i = <value optimized out>
        nPlugin = 1
        disableSm = 1
        clientId = 0x0
        refreshRateArg = 0x0
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c5e6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7c05a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb5a3ccfc in crash_handler (sig=11) at crashhandler.c:59
#4  <signal handler called>
#5  0x08052c49 in allocatePrivateIndex (len=0x80799a0, indices=0x807999c, 
    reallocProc=0x805ae00 <reallocScreenPrivate>, closure=0x8079980)
    at privates.c:41
#6  0x0805da07 in allocScreenObjectPrivateIndex (parent=0x8079980)
    at screen.c:76
#7  0x0805d949 in allocateScreenPrivateIndex (display=0x8079980)
    at screen.c:148
#8  0xb57d3b69 in screenSaverInitDisplay (p=0x82bacc0, d=0x8079980)
    at screensaver.cpp:351
#9  0xb57d2e49 in screenSaverInitObject (p=0x82bacc0, o=0x8079980)
    at screensaver.cpp:397
#10 0xb57dba8b in screensaverOptionsInitObjectWrapper (p=0x82bacc0, 
    o=0x8079980) at build/screensaver_options.c:641
#11 0x0806f54d in initObjectTree (object=0x8079980, closure=0xbff1618c)
    at plugin.c:369
#12 0x0806f7b4 in pushPlugin (p=0x82bacc0) at plugin.c:444
#13 0x080585ee in eventLoop () at display.c:1017
#14 0x08052803 in main (argc=5, argv=0xbff16774) at main.c:461
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 14925

[CRASH_HANDLER]: "/tmp/compiz_crash-14925.out" created!

Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"

```

---

### Post by Yes on 2007-09-22
I just installed the latest updates, and my problem seems to be improving... I can start compiz, and it won't crash.  In fact, it seems to work fine, except my gnome-panels disappear when I start it.  Is anyone else having this problem?

---

### Post by HokeyFry on 2007-09-23
> **Yes said:**
> I just installed the latest updates, and my problem seems to be improving... I can start compiz, and it won't crash.  In fact, it seems to work fine, except my gnome-panels disappear when I start it.  Is anyone else having this problem?

i dont know if its used in Compiz-Fusion, but try running emerald --replace if emerald is still the window manager (I use Compiz, not Compiz-Fusion, but I had a similar issue). see if that fixes it

---

### Post by Yes on 2007-09-23
Nope, that doesn't do anything.  Thanks, though.

---

### Post by bapoumba on 2007-09-23
Moved to "Desktop Effects & Customization".

---

### Post by Yes on 2007-09-25
Is there any way to install previous versions of compiz-fusion?  I think that seems like the easiest solution.  All my settings will be saved if I reinstall compiz, right?

---

### Post by sup3roque on 2007-09-27
I have exacly the same problems... 

/usr/bin/compiz.real (3d) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin '3d'

:(

---

### Post by CareyB on 2007-11-23
I had an odd time installing these two as well.  Here's what worked:

Completely uninstall beryl, compiz, compiz-fusion, and emerald.  Install Compiz-Fusion, and Emerald, then restart.

I hate restarting Linux.  It should never be necessary, but this was the expedient solution.  i.e. Faster than figuring out what was wrong.

---

