---
title: "Compiz is giving me errors?"
date: 2009-01-29
forum: General Help
---

### Post by kevin11951 on 2009-01-29
```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x08ed6dd8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7bfc454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7bfe4b6]
/usr/lib/libGL.so.1[0xb7d74311]
======= Memory map: ========
08048000-0807c000 r-xp 00000000 08:05 4186119    /usr/bin/compiz.real
0807c000-0807d000 r--p 00033000 08:05 4186119    /usr/bin/compiz.real
0807d000-0807e000 rw-p 00034000 08:05 4186119    /usr/bin/compiz.real
08da7000-09640000 rw-p 08da7000 00:00 0          [heap]
b5864000-b586b000 r--s 00000000 08:05 3719285    /usr/lib/gconv/gconv-modules.cache
b586b000-b58aa000 r--p 00000000 08:05 3744234    /usr/lib/locale/en_US.utf8/LC_CTYPE
b58aa000-b59b3000 r--p 00000000 08:05 2359297    /usr/lib/locale/locale-archive
b6400000-b6421000 rw-p b6400000 00:00 0 
b6421000-b6500000 ---p b6421000 00:00 0 
b657c000-b6586000 r-xp 00000000 08:05 4530222    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6586000-b6587000 r--p 00009000 08:05 4530222    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6587000-b6588000 rw-p 0000a000 08:05 4530222    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6588000-b6591000 r-xp 00000000 08:05 4530224    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6591000-b6592000 r--p 00008000 08:05 4530224    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6592000-b6593000 rw-p 00009000 08:05 4530224    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6593000-b659a000 r-xp 00000000 08:05 4530220    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b659a000-b659b000 r--p 00006000 08:05 4530220    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b659b000-b659c000 rw-p 00007000 08:05 4530220    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b659c000-b65b1000 r-xp 00000000 08:05 4530219    /lib/tls/i686/cmov/libnsl-2.8.90.so
b65b1000-b65b2000 r--p 00014000 08:05 4530219    /lib/tls/i686/cmov/libnsl-2.8.90.so
b65b2000-b65b3000 rw-p 00015000 08:05 4530219    /lib/tls/i686/cmov/libnsl-2.8.90.so
b65b3000-b65b5000 rw-p b65b3000 00:00 0 
b65b5000-b65dd000 r-xp 00000000 08:05 3833968    /lib/libpcre.so.3.12.1
b65dd000-b65de000 r--p 00027000 08:05 3833968    /lib/libpcre.so.3.12.1
b65de000-b65df000 rw-p 00028000 08:05 3833968    /lib/libpcre.so.3.12.1
b65df000-b65f4000 r-xp 00000000 08:05 4530227    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65f4000-b65f5000 r--p 00014000 08:05 4530227    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65f5000-b65f6000 rw-p 00015000 08:05 4530227    /lib/tls/i686/cmov/libpthread-2.8.90.so
b65f6000-b65f8000 rw-p b65f6000 00:00 0 
b65f8000-b6634000 r-xp 00000000 08:05 3712137    /usr/lib/libgobject-2.0.so.0.1800.2
b6634000-b6635000 r--p 0003b000 08:05 3712137    /usr/lib/libgobject-2.0.so.0.1800.2
b6635000-b6636000 rw-p 0003c000 08:05 3712137    /usr/lib/libgobject-2.0.so.0.1800.2
b6636000-b666c000 r-xp 00000000 08:05 3833908    /lib/libdbus-1.so.3.4.0
b666c000-b666d000 r--p 00035000 08:05 3833908    /lib/libdbus-1.so.3.4.0
b666d000-b666e000 rw-p 00036000 08:05 3833908    /lib/libdbus-1.so.3.4.0
b666e000-b6689000 r-xp 00000000 08:05 3712756    /usr/lib/libdbus-glib-1.so.2.1.0
b6689000-b668a000 r--p 0001a000 08:05 3712756    /usr/lib/libdbus-glib-1.so.2.1.0
b668a000-b668b000 rw-p 0001b000 08:05 3712756    /usr/lib/libdbus-glib-1.so.2.1.0
b668b000-b6692000 r-xp 00000000 08:05 4530229    /lib/tls/i686/cmov/librt-2.8.90.so
b6692000-b6693000 r--p 00007000 08:05 4530229    /lib/tls/i686/cmov/librt-2.8.90.so
b6693000-b6694000 rw-p 00008000 08:05 4530229    /lib/tls/i686/cmov/librt-2.8.90.so
b6694000-b6698000 r-xp 00000000 08:05 3712180    /usr/lib/libgthread-2.0.so.0.1800.2
b6698000-b6699000 r--p 00003000 08:05 3712180    /usr/lib/libgthread-2.0.so.0.1800.2
b6699000-b669a000 rw-p 00004000 08:05 3712180    /usr/lib/libgthread-2.0.so.0.1800.2
b669a000-b66e3000 r-xp 00000000 08:05 3712547    /usr/lib/libORBit-2.so.0.1.0
b66e3000-b66eb000 r--p 00049000 08:05 3712547    /usr/lib/libORBit-2.so.0.1.0
b66eb000-b66ed000 rw-p 00051000 08:05 3712547    /usr/lib/libORBit-2.so.0.1.0
b66ed000-b67a2000 r-xp 00000000 08:05 3711750    /usr/lib/libglib-2.0.so.0.1800.2
b67a2000-b67a3000 r--p 000b4000 08:05 3711750    /usr/lib/libglib-2.0.so.0.1800.2
b67a3000-b67a4000 rw-p 000b5000 08:05 3711750    /usr/lib/libglib-2.0.so.0.1800.2
b67a4000-b67d2000 r-xp 00000000 08:05 3712855    /usr/lib/libgconf-2.so.4.1.5
b67d2000-b67d3000 ---p 0002e000 08:05 3712855    /usr/lib/libgconf-2.so.4.1.5
b67d3000-b67d4000 r--p 0002e000 08:05 3712855    /usr/lib/libgconf-2.so.4.1.5
b67d4000-b67d6000 rw-p 0002f000 08:05 3712855    /usr/lib/libgconf-2.so.4.1.5
b67ea000-b67fe000 r-xp 00000000 08:05 3712725    /usr/lib/libcompizconfig.so.0.0.0
b67fe000-b67ff000 r--p 00013000 08:05 3712725    /usr/lib/libcompizconfig.so.0.0.0
b67ff000-b6800000 rw-p 00014000 08:05 3712725    /usr/lib/libcompizconfig.so.0.0.0
b6804000-b6807000 r-xp 00000000 08:05 3711755    /usr/lib/libgmodule-2.0.so.0.1800.2
b6807000-b6808000 r--p 00002000 08:05 3711755    /usr/lib/libgmodule-2.0.so.0.1800.2
b6808000-b6809000 rw-p 00003000 08:05 3711755    /usr/lib/libgmodule-2.0.so.0.1800.2
b6809000-b6812000 r-xp 00000000 08:05 3727885    /usr/lib/compizconfig/backends/libgconf.so
b6812000-b6813000 r--p 00008000 08:05 3727885    /usr/lib/compizconfig/backends/libgconf.so
b6813000-b6814000 rw-p 00009000 08:05 3727885    /usr/lib/compizconfig/backends/libgconf.so
b6819000-b6a19000 rw-s 045be000 00:0e 18292      /dev/nvidia0
b6a19000-b6b19000 rw-s 249ef000 00:0e 18292      /dev/nvidia0
b6b19000-b6b1a000 rw-s c6c06000 00:0e 18292      /dev/nvidia0
b6b1a000-b6b5a000 rw-s 0d2ce000 00:0e 18292      /dev/nvidia0
b6b5a000-b6b7a000 rw-s 0cc81000 00:0e 18292      /dev/nvidia0
b6c69000-b6c76000 r-xp 00000000 08:05 3833878    /lib/libgcc_s.so.1
b6c76000-b6c77000 r--p 0000c000 08:05 3833878    /lib/libgcc_s.so.1
b6c77000-b6c78000 rw-p 0000d000 08:05 3833878    /lib/libgcc_s.so.1
b6c8c000-b6cc0000 rw-p b6c8c000 00:00 0 
b6cc0000-b6ce1000 rw-s 00000000 00:09 7831552    /SYSV00000000 (deleted)
b6ce1000-b6ce3000 rw-p b6ce1000 00:00 0 
b6ce3000-b6ce4000 r-xp 00000000 08:05 3744011    /usr/lib/tls/libnvidia-tls.so.180.17
b6ce4000-b6ce5000 rw-p 00000000 08:05 3744011    /usr/lib/tls/libnvidia-tls.so.180.17
b6ce5000-b6ce6000 rw-p b6ce5000 00:00 0 
b6ce6000-b7952000 r-xp 00000000 08:05 3711449    /usr/lib/libGLcore.so.180.17
b7952000-b7b42000 rwxp 00c6c000 08:05 3711449    /usr/lib/libGLcore.so.180.17
b7b42000-b7b4e000 rwxp b7b42000 00:00 0 
b7b4e000-b7b62000 r-xp 00000000 08:05 3713523    /usr/lib/libz.so.1.2.3.3
b7b62000-b7b64000 rw-p 00013000 08:05 3713523    /usr/lib/libz.so.1.2.3.3
b7b64000-b7b6c000 r-xp 00000000 08:05 3712604    /usr/lib/libXrender.so.1.3.0
b7b6c000-b7b6d000 r--p 00007000 08:05 3712604    /usr/lib/libXrender.so.1.3.0
b7b6d000-b7b6e000 rw-p 00008000 08:05 3712604    /usr/lib/libXrender.so.1.3.0
b7b6e000-b7b72000 r-xp 00000000 08:05 3712578    /usr/lib/libXdmcp.so.6.0.0
b7b72000-b7b73000 rw-p 00003000 08:05 3712578    /usr/lib/libXdmcp.so.6.0.0
b7b73000-b7b75000 r-xp 00000000 08:05 3712567    /usr/lib/libXau.so.6.0.0
b7b75000-b7b76000 rw-p 00001000 08:05 3712567    /usr/lib/libXau.so.6.0.0
b7b76000-b7b77000 rw-p b7b76000 00:00 0 
b7b77000-b7b78000 r-xp 00000000 08:05 3713509    /usr/lib/libxcb-xlib.so.0.0.0
b7b78000-b7b79000 r--p 00000000 08:05 3713509    /usr/lib/libxcb-xlib.so.0.0.0
b7b79000-b7b7a000 rw-p 00001000 08:05 3713509    /usr/lib/libxcb-xlib.so.0.0.0
b7b7a000-b7b87000 r-xp 00000000 08:05 3712582    /usr/lib/libXext.so.6.4.0
b7b87000-b7b89000 rw-p 0000c000 08:05 3712582    /usr/lib/libXext.so.6.4.0
b7b89000-b7b8b000 r-xp 00000000 08:05 4530216    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b8b000-b7b8c000 r--p 00001000 08:05 4530216    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b8c000-b7b8d000 rw-p 00002000 08:05 4530216    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b8d000-b7ce5000 r-xp 00000000 08:05 4530209    /lib/tls/i686/cmov/libc-2.8.90.so
b7ce5000-b7ce7000 r--p 00158000 08:05 4530209    /lib/tls/i686/cmov/libc-2.8.90.so
b7ce7000-b7ce8000 rw-p 0015a000 08:05 4530209    /lib/tls/i686/cmov/libc-2.8.90.so
b7ce8000-b7ceb000 rw-p b7ce8000 00:00 0 
b7ceb000-b7d0f000 r-xp 00000000 08:05 4530217    /lib/tls/i686/cmov/libm-2.8.90.so
b7d0f000-b7d10000 r--p 00023000 08:05 4530217    /lib/tls/i686/cmov/libm-2.8.90.so
b7d10000-b7d11000 rw-p 00024000 08:05 4530217    /lib/tls/i686/cmov/libm-2.8.90.so
b7d11000-b7d9e000 r-xp 00000000 08:05 3711425    /usr/lib/libGL.so.180.17
b7d9e000-b7dbc000 rwxp 0008d000 08:05 3711425    /uAborted

```

Any incites about what is going on here?

---

### Post by swoll1980 on 2009-01-29
It does look like you have a driver installed for your video card but it's not configured right it says xgl not present

---

### Post by kevin11951 on 2009-01-30
> **swoll1980 said:**
> It does look like you have a driver installed for your video card but it's not configured right it says xgl not present

what do i do?

---

### Post by Yellow Pasque on 2009-01-30
You don't need xgl since you have an nvidia card.
My gut instinct is that something is wrong with your video driver install. What video card do you have and how did you install the video drivers?

---

### Post by kevin11951 on 2009-01-31
> **Temüjin said:**
> You don't need xgl since you have an nvidia card.
My gut instinct is that something is wrong with your video driver install. What video card do you have and how did you install the video drivers?

i have an nvidia 8400m gs, and the closed source nvidia drivers version 180.22. Installed by compiling them.

---

### Post by kevin11951 on 2009-01-31
any help at all?

---

### Post by Crafty Kisses on 2009-01-31
What are the results of this command?
```
glxinfo | grep direct
```

---

### Post by kevin11951 on 2009-01-31
> **Codename said:**
> What are the results of this command?
```
glxinfo | grep direct
```

direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

---

### Post by kevin11951 on 2009-02-01
hello?

---

### Post by darko515 on 2009-03-19
i have the same problem, except that i'm using 64bit Ubuntu with nVidia 8800m GTS.

:(

---

### Post by hessczoo on 2009-04-01
I too, get this same error. I find nothing on launchpad pertaining to the issue. Anyone have any insight?

---

### Post by hessczoo on 2009-04-02
Update your x11-common and it will fix it.

---

