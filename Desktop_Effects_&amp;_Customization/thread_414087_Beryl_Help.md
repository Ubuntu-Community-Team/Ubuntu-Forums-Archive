---
title: "Beryl Help"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by SikEnCide on 2007-04-19
i want to install it on feisty and im not too sure i need help 

i did this

```
chris@Sik:~$ sudo apt-get install beryl-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libberylsettings0
Suggested packages:
  libberylsettings0-gconf libberylsettings0-kconfig
The following NEW packages will be installed:
  beryl-core libberylsettings0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 206kB of archives.
After unpacking 938kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libberylsettings0 beryl-core
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com feisty/universe libberylsettings0 0.2.1.dfsg+git20070318-0ubuntu2 [34.7kB]
Get:2 http://us.archive.ubuntu.com feisty/universe beryl-core 0.2.1.dfsg+git20070318-0ubuntu2 [171kB]
Fetched 206kB in 1m2s (3296B/s)                                                
Selecting previously deselected package libberylsettings0.
(Reading database ... 88050 files and directories currently installed.)
Unpacking libberylsettings0 (from .../libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb) ...
Selecting previously deselected package beryl-core.
Unpacking beryl-core (from .../beryl-core_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb) ...
Setting up libberylsettings0 (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up beryl-core (0.2.1.dfsg+git20070318-0ubuntu2) ...

```

 then ran this command to see if im ready for beryl 
```
chris@Sik:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

*** glibc detected *** beryl: double free or corruption (fasttop): 0x0809f708 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cae7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cb1e30]
/lib/tls/i686/cmov/libdl.so.2[0xb7b3c2d8]
/lib/tls/i686/cmov/libdl.so.2(dlopen+0x4f)[0xb7b3c9ff]
/usr/lib/libberylsettings.so.0[0xb7d8f0c9]
/usr/lib/libberylsettings.so.0(beryl_settings_context_set_backend+0xa7)[0xb7d8f6c7]
/usr/lib/libberylsettings.so.0(beryl_settings_context_new+0x31f)[0xb7d90daf]
beryl(addDisplay+0x4fb)[0x8057a9b]
beryl(main+0x543)[0x8052343]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7c5cebc]
beryl[0x8051cd1]
======= Memory map: ========
08048000-08080000 r-xp 00000000 08:03 1000771    /usr/bin/beryl
08080000-08081000 rw-p 00038000 08:03 1000771    /usr/bin/beryl
08081000-080a5000 rw-p 08081000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0 
b7021000-b7100000 ---p b7021000 00:00 0 
b71e6000-b71f1000 r-xp 00000000 08:03 753728     /lib/libgcc_s.so.1
b71f1000-b71f2000 rw-p 0000a000 08:03 753728     /lib/libgcc_s.so.1
b71f2000-b71fb000 r-xp 00000000 08:03 787604     /lib/tls/i686/cmov/libnss_files-2.5.so
b71fb000-b71fd000 rw-p 00008000 08:03 787604     /lib/tls/i686/cmov/libnss_files-2.5.so
b71fd000-b7205000 r-xp 00000000 08:03 787608     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7205000-b7207000 rw-p 00007000 08:03 787608     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7207000-b721a000 r-xp 00000000 08:03 787598     /lib/tls/i686/cmov/libnsl-2.5.so
b721a000-b721c000 rw-p 00012000 08:03 787598     /lib/tls/i686/cmov/libnsl-2.5.so
b721c000-b721e000 rw-p b721c000 00:00 0 
b721e000-b7225000 r-xp 00000000 08:03 787600     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7225000-b7227000 rw-p 00006000 08:03 787600     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7231000-b7296000 rw-p b7231000 00:00 0 
b7296000-b729a000 r-xp 00000000 08:03 1000709    /usr/lib/libXdmcp.so.6.0.0
b729a000-b729b000 rw-p 00003000 08:03 1000709    /usr/lib/libXdmcp.so.6.0.0
b729b000-b729d000 r-xp 00000000 08:03 1000698    /usr/lib/libXau.so.6.0.0
b729d000-b729e000 rw-p 00001000 08:03 1000698    /usr/lib/libXau.so.6.0.0
b729e000-b729f000 r-xp 00000000 08:03 1034269    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b729f000-b72a0000 rw-p 00000000 08:03 1034269    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b72a0000-b7aed000 r-xp 00000000 08:03 1000152    /usr/lib/libGLcore.so.1.0.9631
b7aed000-b7b22000 rwxp 0084d000 08:03 1000152    /usr/lib/libGLcore.so.1.0.9631
b7b22000-b7b26000 rwxp b7b22000 00:00 0 
b7b26000-b7b27000 rw-p b7b26000 00:00 0 
b7b27000-b7b3a000 r-xp 00000000 08:03 1001453    /usr/lib/libz.so.1.2.3
b7b3a000-b7b3b000 rw-p 00012000 08:03 1001453    /usr/lib/libz.so.1.2.3
b7b3b000-b7b3d000 r-xp 00000000 08:03 787593     /lib/tls/i686/cmov/libdl-2.5.so
b7b3d000-b7b3f000 rw-p 00001000 08:03 787593     /lib/tls/i686/cmov/libdl-2.5.so
b7b3f000-b7b46000 r-xp 00000000 08:03 1000735    /usr/lib/libXrender.so.1.3.0
b7b46000-b7b47000 rw-p 00006000 08:03 1000735    /usr/lib/libXrender.so.1.3.0
b7b47000-b7b54000 r-xp 00000000 08:03 1000713    /usr/lib/libXext.so.6.4.0
b7b54000-b7b55000 rw-p 0000d000 08:03 1000713    /usr/lib/libXext.so.6.4.0
b7b55000-b7c42000 r-xp 00000000 08:03 1000692    /usr/lib/libX11.so.6.2.0
b7c42000-b7c46000 rw-p 000ed000 08:03 1000692    /usr/lib/libX11.so.6.2.0
b7c46000-b7c47000 rw-p b7c46000 00:00 0 
b7c47000-b7d82000 r-xp 00000000 08:03 787587     /lib/tls/i686/cmov/libc-2.5.so
b7d82000-b7d83000 r--p 0013b000 08:03 787587     /lib/tls/i686/cmov/libc-2.5.so
b7d83000-b7d85000 rw-p 0013c000 08:03 787587     /lib/tls/i686/cmov/libc-2.5.so
b7d85000-b7d88000 rw-p b7d85000 00:00 0 
b7d88000-b7d96000 r-xp 00000000 08:03 1000481    /usr/lib/libberylsettings.so.0.0.0
b7d96000-b7d97000 rw-p 0000e000 08:03 1000481    /usr/lib/libberylsettings.so.0.0.0
b7d97000-b7dbc000 r-xp 00000000 08:03 787595     /lib/tls/i686/cmov/libm-2.5.so
b7dbc000-b7dbe000 rw-p 00024000 08:03 787595     /lib/tls/i686/cmov/libm-2.5.so
b7dbe000-b7e2f000 r-xp 00000000 08:03 1000151    /usr/lib/libGL.so.1.0.9631
b7e2f000-b7e49000 rwxp 00070000 08:03 1000151    /usr/lib/libGL.so.1.0.9631
b7e49000-b7e4a000 rwxp b7e49000 00:00 0 
b7e4a000-b7ede000 r-xp 00000000 08:03 1000995    /usr/lib/libglib-2.0.so.0.1200.11
b7ede000-b7edf000 rw-p 00093000 08:03 1000995    /usr/lib/libglib-2.0.so.0.1200.11
b7edf000-b7ee7000 r-xp 00000000 08:03 1001385    /usr/lib/libstartup-notification-1.so.0.0.0
b7ee7000-b7ee8000 rw-p 00007000 08:03 1001385    /usr/lib/libstartup-notification-1.so.0.0.0
b7ee8000-b7ee9000 rw-p b7ee8000 00:00 0 
b7ee9000-b7eeb000 r-xp 00000000 08:03 1000723    /usr/lib/libXinerama.so.1.0.0
b7eeb000-b7eec000 rw-p 00001000 08:03 1000723    /usr/lib/libXinerama.so.1.0.0
b7eec000-b7f01000 r-xp 00000000 08:03 1000670    /usr/lib/libICE.so.6.3.0
b7f01000-b7f03000 rw-p 00014000 08:03 1000670    /usr/lib/libICE.so.6.3.0
b7f03000-b7f04000 rw-p b7f03000 00:00 0 
b7f04000-b7f0c000 r-xp 00000000 08:03 1000688    /usr/lib/libSM.so.6.0.0
b7f0c000-b7f0d000 rw-p 00007000 08:03 1000688    /usr/lib/libSM.so.6.0.0
b7f0d000-b7f12000 r-xp 00000000 08:03 1000733    /usr/lib/libXrandr.so.2.1.0
b7f12000-b7f13000 rw-p 00005000 08:03 1000733    /usr/lib/libXrandr.so.2.1.0
b7f13000-b7f17000 r-xp 00000000 08:03 1000715    /usr/lib/libXfixes.so.3.1.0
b7f17000-b7f18000 rw-p 00003000 08:03 1000715    /usr/lib/libXfixes.so.3.1.0
b7f18000-b7f1a000 r-xp 00000000 08:03 1000707    /usr/lib/libXdamage.so.1.0.0
b7f1a000-b7f1b000 rw-p 00001000 08:03 1000707    /usr/lib/libXdamage.so.1.0.0
b7f1b000-b7f1c000 rw-p b7f1b000 00:00 0 
b7f1c000-b7f1e000 r-xp 00000000 08:03 1000703    /usr/lib/libXcomposite.so.1.0.0
b7f1e000-b7f1f000 rw-p 00001000 08:03 1000703    /usr/lib/libXcomposite.so.1.0.0
b7f1f000-b7f41000 r-xp 00000000 08:03 1001307    /usr/lib/libpng12.so.0.15.0
b7f41000-b7f42000 rw-p 00021000 08:03 1001307    /usr/lib/libpng12.so.0.15.0
b7f42000-b7f49000 r--s 00000000 08:03 360683     /usr/lib/gconv/gconv-modules.cache
b7f49000-b7f4a000 rw-p b7f49000 00:00 0 
b7f4a000-b7f4c000 rwxp 00000000 00:0d 2729       /dev/zero
b7f4c000-b7f4e000 rw-p b7f4c000 00:00 0 
b7f4e000-b7f67000 r-xp 00000000 08:03 753685     /lib/ld-2.5.so
b7f67000-b7f69000 rw-p 00019000 08:03 753685     /lib/ld-2.5.so
bff55000-bff69000 rwxp bff55000 00:00 0          [stack]
bff69000-bff6b000 rw-p bff69000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

does this mean im ready to install or .. or that my system can handle it.

also if it can can i have direction on how to proceed further with the installation.

---

### Post by SikEnCide on 2007-05-06
beryl works

---

