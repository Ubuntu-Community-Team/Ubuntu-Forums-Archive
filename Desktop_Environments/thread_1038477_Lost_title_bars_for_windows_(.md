---
title: "Lost title bars for windows :("
date: 2009-01-12
forum: Desktop Environments
---

### Post by braindeadave on 2009-01-12
I seemed to have lost my title bars for my application windows. Every time i open an application or an application throws up an extra box it seems to expand top fill my destop area so i can no longer see or reach the desktop without closing the application down. I have tried the two main suggestions on these forums but i am getting various error messages:

command: compiz -- replace

dave@dave-desktop:~$ compiz -- replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

And sometimes this happens: 

dave@dave-desktop:~$ compiz -- replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x092285b0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c333f4]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7c35456]
/usr/lib/libGL.so.1[0xb7d9b0e1]
======= Memory map: ========
08048000-0807c000 r-xp 00000000 08:01 9724113    /usr/bin/compiz.real
0807c000-0807d000 r--p 00033000 08:01 9724113    /usr/bin/compiz.real
0807d000-0807e000 rw-p 00034000 08:01 9724113    /usr/bin/compiz.real
090fb000-09a1c000 rw-p 090fb000 00:00 0          [heap]
b4d61000-b4f61000 rw-s 357e8000 00:0e 17083      /dev/nvidia0
b4f81000-b4f88000 r--s 00000000 08:01 25264371   /usr/lib/gconv/gconv-modules.cache
b4f88000-b4fc7000 r--p 00000000 08:01 9798261    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b6500000-b6521000 rw-p b6500000 00:00 0 
b6521000-b6600000 ---p b6521000 00:00 0 
b66c6000-b66da000 r-xp 00000000 08:01 9726832    /usr/lib/libcompizconfig.so.0.0.0
b66da000-b66db000 r--p 00013000 08:01 9726832    /usr/lib/libcompizconfig.so.0.0.0
b66db000-b66dc000 rw-p 00014000 08:01 9726832    /usr/lib/libcompizconfig.so.0.0.0
b66dc000-b66e6000 r-xp 00000000 08:01 9880938    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66e6000-b66e7000 r--p 00009000 08:01 9880938    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66e7000-b66e8000 rw-p 0000a000 08:01 9880938    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66e8000-b66f1000 r-xp 00000000 08:01 9880942    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66f1000-b66f2000 r--p 00008000 08:01 9880942    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66f2000-b66f3000 rw-p 00009000 08:01 9880942    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66f3000-b66fa000 r-xp 00000000 08:01 9880934    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b66fa000-b66fb000 r--p 00006000 08:01 9880934    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b66fb000-b66fc000 rw-p 00007000 08:01 9880934    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b66fc000-b6711000 r-xp 00000000 08:01 9880932    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6711000-b6712000 r--p 00014000 08:01 9880932    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6712000-b6713000 rw-p 00015000 08:01 9880932    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6713000-b6715000 rw-p b6713000 00:00 0 
b6715000-b673d000 r-xp 00000000 08:01 9863281    /lib/libpcre.so.3.12.1
b673d000-b673e000 r--p 00027000 08:01 9863281    /lib/libpcre.so.3.12.1
b673e000-b673f000 rw-p 00028000 08:01 9863281    /lib/libpcre.so.3.12.1
b673f000-b6754000 r-xp 00000000 08:01 9880947    /lib/tls/i686/cmov/libpthread-2.8.90.so
b6754000-b6755000 r--p 00014000 08:01 9880947    /lib/tls/i686/cmov/libpthread-2.8.90.so
b6755000-b6756000 rw-p 00015000 08:01 9880947    /lib/tls/i686/cmov/libpthread-2.8.90.so
b6756000-b6758000 rw-p b6756000 00:00 0 
b6758000-b6794000 r-xp 00000000 08:01 9724604    /usr/lib/libgobject-2.0.so.0.1800.2
b6794000-b6795000 r--p 0003b000 08:01 9724604    /usr/lib/libgobject-2.0.so.0.1800.2
b6795000-b6796000 rw-p 0003c000 08:01 9724604    /usr/lib/libgobject-2.0.so.0.1800.2
b6796000-b67cc000 r-xp 00000000 08:01 9863220    /lib/libdbus-1.so.3.4.0
b67cc000-b67cd000 r--p 00035000 08:01 9863220    /lib/libdbus-1.so.3.4.0
b67cd000-b67ce000 rw-p 00036000 08:01 9863220    /lib/libdbus-1.so.3.4.0
b67ce000-b67e9000 r-xp 00000000 08:01 9726876    /usr/lib/libdbus-glib-1.so.2.1.0
b67e9000-b67ea000 r--p 0001a000 08:01 9726876    /usr/lib/libdbus-glib-1.so.2.1.0
b67ea000-b67eb000 rw-p 0001b000 08:01 9726876    /usr/lib/libdbus-glib-1.so.2.1.0
b67eb000-b67f2000 r-xp 00000000 08:01 9880951    /lib/tls/i686/cmov/librt-2.8.90.so
b67f2000-b67f3000 r--p 00007000 08:01 9880951    /lib/tls/i686/cmov/librt-2.8.90.so
b67f3000-b67f4000 rw-p 00008000 08:01 9880951    /lib/tls/i686/cmov/librt-2.8.90.so
b67f4000-b683d000 r-xp 00000000 08:01 9726375    /usr/lib/libORBit-2.so.0.1.0
b683d000-b6845000 r--p 00049000 08:01 9726375    /usr/lib/libORBit-2.so.0.1.0
b6845000-b6847000 rw-p 00051000 08:01 9726375    /usr/lib/libORBit-2.so.0.1.0
b6847000-b68fc000 r-xp 00000000 08:01 9724526    /usr/lib/libglib-2.0.so.0.1800.2
b68fc000-bAborted
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
Segmentation fault
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x140002f (Bottom Exp)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1400003 (Top Expand)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3e00830 (dave@dave-)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c001e2 (bin - File)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x100023e (Ubuntu For)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4000081 (Synaptic P)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x10002b2 (Debian -- )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c0001c (x-nautilus)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect




any suggestions?

---

### Post by coolethan on 2009-01-12
can't you still access the menu bars spanning the top and bottom of your screen? theres a desktop button on the bottom one that switches back to your desktop. you can try typing ctrl-alt-d and that will bring you too the desktop.

---

### Post by braindeadave on 2009-01-12
> **coolethan said:**
> can't you still access the menu bars spanning the top and bottom of your screen? theres a desktop button on the bottom one that switches back to your desktop. you can try typing ctrl-alt-d and that will bring you too the desktop.

Yes i can, but that does not solve the problem of being able to resize any of my application windows. which i would like to do.

---

### Post by coolethan on 2009-01-12
can you remember what exactly you did? i'm as lost as you are now.

---

### Post by theozzlives on 2009-01-12
Try:
```
emerald --replace
```

---

### Post by braindeadave on 2009-01-12
> **theozzlives said:**
> Try:
```
emerald --replace
```

dave@dave-desktop:~$ emerald -- replace
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
dave@dave-desktop:~$ compiz -- replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
Segmentation fault



^[[A^[[A^[[A^[[B



This is all very strange. It was working fine last night, then i boot up today and it's all messed up.?

---

