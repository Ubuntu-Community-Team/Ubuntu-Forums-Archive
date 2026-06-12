---
title: "compiz-beryl-whatever dead after update"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Vlatko on 2006-09-25
i just updated my ubuntu, the whole 70mbs, and after rebooting i have no titles in windows, no top panel..

what went wrong? i don't know where to look, or what to look for. compiz-beryl i'm confused.

---

### Post by Vlatko on 2006-09-25
i tried to run compiz-start and it crahsed creating this log file in /tmp/

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz, process 5510
(no debugging symbols found)
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
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
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/compiz/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /usr/lib/compiz/libcsm.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcsm.so
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
0xffffe410 in __kernel_vsyscall ()
(gdb) 

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e98933 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e423c9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7fbcb62 in crash_handler () from /usr/lib/compiz/libcrashhandler.so
#4  <signal handler called>
#5  0xb7c56af0 in ?? () from /usr/lib/compiz/libdecoration.so
#6  0x00000008 in ?? ()
#7  0xb7c56d06 in ?? () from /usr/lib/compiz/libdecoration.so
#8  0x080f5fe0 in ?? ()
#9  0x080da7f8 in ?? ()
#10 0x080f82d8 in ?? ()
#11 0x080da7f8 in ?? ()
#12 0xbf9e2258 in ?? ()
#13 0x08072e92 in initPluginForScreen ()
#14 0x08072e92 in initPluginForScreen ()
#15 0xb7cb216c in csm_save_option () from /usr/lib/compiz/libcsm.so
#16 0x08072d67 in initPluginForDisplay ()
#17 0xb7cb209c in csm_save_option () from /usr/lib/compiz/libcsm.so
#18 0x0807334a in pushPlugin ()
#19 0x0805ca82 in eventLoop ()
#20 0x0805ab3b in main ()
Detaching from program: /usr/bin/compiz, process 5510
```

---

