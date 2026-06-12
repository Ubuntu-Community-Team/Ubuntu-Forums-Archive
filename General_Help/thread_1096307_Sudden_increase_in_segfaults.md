---
title: "Sudden increase in segfaults"
date: 2009-03-14
forum: General Help
---

### Post by szim90 on 2009-03-14
Hello.

I logged on (in person) to my system today for the first time in a while (I've been using it for a file server while I've been away). Anyway, my system developed a number of unusual errors. Included software like ccsm, "Software Sources", "Update Manager" and others would simply fail to start. If I typed their command into a terminal, it would simply output "Segmentation Fault". 

The gnome panel sometimes does not load on boot either, and my graphics drivers decided to stop working. 

Is anyone else experiencing similar problems? I got "Update Manager" and "Software Sources" working again by reinstalling ubuntu-desktop, and I managed to get my graphics drivers back again, but the panel is still not always appearing, and applications are still failing to start. Is there some common dependency or config that could have become corrupt?

Any help toward a solution would be greatly appreciated.

Regards,
szim90


EDIT:
Update Manager and Aptitude are now crashing whenever they try to install. This time, they provided me with a backtrace
```

:~$ sudo aptitude install reportbug
[sudo] password for sean: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following NEW packages will be installed:
  reportbug 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 158kB of archives. After unpacking 541kB will be used.
Writing extended state information... Done
Get:1 http://mirror.cc.columbia.edu intrepid-updates/universe reportbug 3.41ubuntu2.1 [158kB]
Fetched 158kB in 0s (501kB/s) 
Selecting previously deselected package reportbug.
(Reading database ... 204477 files and directories currently installed.)
Unpacking reportbug (from .../reportbug_3.41ubuntu2.1_all.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up reportbug (3.41ubuntu2.1) ...

Processing triggers for menu ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
*** glibc detected *** aptitude: double free or corruption (out): 0x0824cfd8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7a09454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7a0b4b6]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7be60b1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb7bc28bd]
/usr/lib/libstdc++.so.6(_ZNSs6assignERKSs+0xb0)[0xb7bc4390]
aptitude[0x816ca9d]
aptitude[0x8172bf5]
aptitude[0x81743c2]
aptitude[0x81789a0]
aptitude[0x818645a]
aptitude[0x8149f3e]
aptitude[0x8121fbd]
aptitude[0x805fac2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb79b0685]
aptitude[0x805cbb1]
======= Memory map: ========
08048000-0824b000 r-xp 00000000 08:01 1802284    /usr/bin/aptitude
0824b000-0824c000 r--p 00202000 08:01 1802284    /usr/bin/aptitude
0824c000-0824d000 rw-p 00203000 08:01 1802284    /usr/bin/aptitude
0824d000-0824f000 rw-p 0824d000 00:00 0 
08e2d000-09f34000 rw-p 08e2d000 00:00 0          [heap]
b5c00000-b5c21000 rw-p b5c00000 00:00 0 
b5c21000-b5d00000 ---p b5c21000 00:00 0 
b5d76000-b5d77000 ---p b5d76000 00:00 0 
b5d77000-b6577000 rw-p b5d77000 00:00 0 
b664d000-b66b2000 rw-p b664d000 00:00 0 
b66b2000-b66bc000 r-xp 00000000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66bc000-b66bd000 r--p 00009000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66bd000-b66be000 rw-p 0000a000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b66be000-b66c7000 r-xp 00000000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66c7000-b66c8000 r--p 00008000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66c8000-b66c9000 rw-p 00009000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b66c9000-b66de000 r-xp 00000000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b66de000-b66df000 r--p 00014000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b66df000-b66e0000 rw-p 00015000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b66e0000-b66e2000 rw-p b66e0000 00:00 0 
b66e2000-b66e9000 r-xp 00000000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b66e9000-b66ea000 r--p 00006000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b66ea000-b66eb000 rw-p 00007000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b67c6000-b6c3c000 rw-p b67c6000 00:00 0 
b6c3c000-b786f000 r--s 00000000 08:01 2703397    /var/cache/apt/pkgcache.bin
b786f000-b7870000 rw-p b786f000 00:00 0 
b7870000-b78af000 r--p 00000000 08:01 1827708    /usr/lib/locale/en_US.utf8/LC_CTYPE
b78af000-b7990000 r--p 00000000 08:01 1827707    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7990000-b7991000 rw-p b7990000 00:00 0 
b7991000-b7993000 r-xp 00000000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b7993000-b7994000 r--p 00001000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b7994000-b7995000 rw-p 00002000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b7995000-b7996000 rw-p b7995000 00:00 0 
b7996000-b7998000 r-xp 00000000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b7998000-b7999000 r--p 00001000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b7999000-b799a000 rw-p 00002000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b799a000-b7af2000 r-xp 00000000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b7af2000-b7af4000 r--p 00158000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b7af4000-b7af5000 rw-p 0015a000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b7af5000-b7af8000 rw-p b7af5000 00:00 0 
b7af8000-b7b05000 r-xp 00000000 08:01 2124012    /lib/libgcc_s.so.1
b7b05000-b7b06000 r--p 0000c000 08:01 2124012    /lib/libgcc_s.so.1
b7b06000-b7b07000 rw-p 0000d000 08:01 2124012    /lib/libgcc_s.so.1
b7b07000-b7b2b000 r-xp 00000000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b7b2b000-b7b2c000 r--p 00023000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b7b2c000-b7b2d000 rw-p 00024000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b7b2d000-b7c10000 r-xp 00000000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7c10000-b7c14000 r--p 000e3000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7c14000-b7c15000 rw-p 000e7000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7c15000-b7c1c000 rw-p b7c15000 00:00 0 
b7c1c000-b7c31000 r-xp 00000000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7c31000-b7c32000 r--p 00014000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7c32000-b7c33000 rw-p 00015000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7c33000-b7c35000 rw-p b7c33000 00:00 0 
b7c35000-b7c49000 r-xp 00000000 08:01 1804505    /usr/lib/libz.so.1.2.3.3
b7c49000-b7c4b000 rw-p 00013000 08:01 1804505    /usr/lib/libz.so.1.2.3.3
b7c4b000-b7d90000 r-xp 00000000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b7d90000-b7d9c000 r--p 00145000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b7d9c000-b7d9d000 rw-p 00151000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b7d9d000-b7e0e000 r-xp 00000000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7e0e000-b7e0f000 r--p 00071000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7e0f000-b7e10000 rw-p 00072000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7e10000-b7ece000 r-xp 00000000 08:01 1802280    /usr/lib/libcwidget.so.3.0.0
b7ece000-b7ed1000 r--p 000be000 08:01 1802280    /usr/lib/libcwidget.so.3.0.0
b7ed1000-b7ed2000 rw-p 000c1000 08:01 1802280    /usr/lib/libcwidget.so.3.0.0
b7ed2000-b7ed7000 r-xp 00000000 08:01 1802278    /usr/lib/libsigc-2.0.so.0.0.0
b7ed7000-b7ed8000 r--p 00004000 08:01 1802278    /usr/lib/libsigc-2.0.so.0.0.0
b7ed8000-b7ed9000 rw-p 00005000 08:01 1802278    /usr/lib/libsigc-2.0.so.0.0.0
b7ed9000-b7eda000 rw-p b7ed9000 00:00 0 
b7eda000-b7f12000 r-xp 00000000 08:01 2121810    /lib/libncursesw.so.5.6
b7f12000-b7f15000 rw-p 00037000 08:01 2121810    /lib/libncursesw.so.5.6
b7f15000-b7fd4000 r-xp 00000000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b7fd4000-b7fd6000 r--p 000be000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b7fd6000-b7fd7000 rw-p 000c0000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b7fde000-b7fdf000 r--p 00000000 08:01 1827713    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fdf000-b7fe0000 r--p 00000000 08:01 1827716    /usr/lib/locale/en_US.utf8/LC_TIME
b7fe0000-b7fe1000 r--p 00000000 08:01 1827711    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fe1000-b7fe2000 r--p 00000000 08:01 1835012    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fe2000-b7fe3000 r--p 00000000 08:01 1827714    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fe3000-b7fe4000 r--p 00000000 08:01 1827712    /usr/lib/locale/en_US.utf8/LC_NAME
b7fe4000-b7fe5000 r--p 00000000 08:01 1827706    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fe5000-b7fe6000 r--p 00000000 08:01 1827715    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fe6000-b7fe7000 r--p 00000000 08:01 1827710    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fe7000-b7fee000 r--s 00000000 08:01 3604481    /usr/lib/gconv/gconv-modules.cache
b7fee000-b7fef000 r--p 00000000 08:01 1827709    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fef000-b7ff1000 rw-p b7fef000 00:00 0 
b7ff1000-b800b000 r-xp 00000000 08:01 2121792    /lib/ld-2.8.90.so
b800b000-b800c000 r-xp b800b000 00:00 0          [vdso]
b800c000-b800d000 r--p 0001a000 08:01 2121792    /lib/ld-2.8.90.so
b800d000-b800e000 rw-p 0001b000 08:01 2121792    /lib/ld-2.8.90.so
bfbf9000-bfc0e000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

```

~$ update-manager
/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py:414: GtkWarning: Theme directory 96x96/action of theme HumanAzul2 has no size field

  self.window_main.show()

(gksu:7227): Gtk-WARNING **: Theme directory 96x96/action of theme HumanAzul2 has no size field

======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7162454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb71644b6]
/usr/lib/libfreetype.so.6[0xb78b1e6d]
/usr/lib/libfreetype.so.6(ft_mem_free+0x1a)[0xb78b607a]
/usr/lib/libfreetype.so.6[0xb78ebd3f]
/usr/lib/libfreetype.so.6[0xb78ef815]
/usr/lib/libfreetype.so.6[0xb78c6a31]
/usr/lib/libfreetype.so.6[0xb78b82dd]
/usr/lib/libfreetype.so.6(FT_Open_Face+0x1d5)[0xb78ba785]
/usr/lib/libfreetype.so.6(FT_New_Face+0x48)[0xb78bb648]
/usr/lib/libXft.so.2[0xb753e6e9]
/usr/lib/libXft.so.2(XftFontOpenInfo+0xff)[0xb753ec6f]
/usr/lib/libXft.so.2(XftFontOpenPattern+0x56)[0xb753f256]
/usr/lib/libvte.so.9[0xb76b07f2]
/usr/lib/libvte.so.9[0xb76b19d7]
/usr/lib/libvte.so.9[0xb76b1c14]
/usr/lib/libvte.so.9[0xb76a32c6]
/usr/lib/libvte.so.9[0xb768bc14]
/usr/lib/libvte.so.9[0xb7694173]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb77fe3d4]
/usr/lib/libgobject-2.0.so.0[0xb77ef3c9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb77f0c4b]
/usr/lib/libgobject-2.0.so.0[0xb78068ee]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7dc)[0xb78087ac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7808c26]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xb1)[0xb7e79251]
/usr/sbin/synaptic[0x8070e07]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x8c)[0xb77fdaec]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb77f0c4b]
/usr/lib/libgobject-2.0.so.0[0xb7807095]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7dc)[0xb78087ac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7808c26]
/usr/lib/libgobject-2.0.so.0[0xb77f51f1]
/usr/lib/libgobject-2.0.so.0[0xb77f19af]
/usr/lib/libgobject-2.0.so.0(g_object_notify+0x1ed)[0xb77f7b4d]
/usr/lib/libgtk-x11-2.0.so.0(gtk_expander_set_expanded+0x115)[0xb7cea865]
/usr/lib/libgtk-x11-2.0.so.0[0xb7cea8d2]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x84)[0xb77fe3d4]
/usr/lib/libgobject-2.0.so.0[0xb77ef3c9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb77f0c4b]
/usr/lib/libgobject-2.0.so.0[0xb7806d3d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7dc)[0xb78087ac]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7808c26]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x87)[0xb7e76477]
/usr/lib/libgtk-x11-2.0.so.0[0xb7ceb2dc]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d5b036]
/usr/lib/libgobject-2.0.so.0[0xb77ef3c9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab)[0xb77f0c4b]
/usr/lib/libgobject-2.0.so.0[0xb7806d3d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x65b)[0xb780862b]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26)[0xb7808c26]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e7033e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xec)[0xb7d53b4c]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2e7)[0xb7d54ef7]
/usr/lib/libgdk-x11-2.0.so.0[0xb7aaf50a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb77636f8]
/usr/lib/libglib-2.0.so.0[0xb7766da3]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x71)[0xb7766f61]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_iteration+0x34)[0xb7d55204]
/usr/sbin/synaptic[0x80717f5]
/usr/sbin/synaptic[0x8072974]
/usr/sbin/synaptic[0x80af8ba]
/usr/sbin/synaptic[0x80890d4]
======= Memory map: ========
08048000-080f3000 r-xp 00000000 08:01 1803009    /usr/sbin/synaptic
080f3000-080f4000 r--p 000aa000 08:01 1803009    /usr/sbin/synaptic
080f4000-080f7000 rw-p 000ab000 08:01 1803009    /usr/sbin/synaptic
080f7000-080f8000 rw-p 080f7000 00:00 0 
08557000-0949f000 rw-p 08557000 00:00 0          [heap]
b2100000-b2121000 rw-p b2100000 00:00 0 
b2121000-b2200000 ---p b2121000 00:00 0 
b22ff000-b2a55000 r--p 00000000 08:01 2295272    /usr/share/fonts/truetype/sazanami/sazanami-gothic.ttf
b2a55000-b2aae000 rw-p b2a55000 00:00 0 
b2aae000-b3ec3000 r--p 00000000 08:01 1925145    /usr/share/fonts/truetype/arphic/uming.ttc
b3ec3000-b3f23000 rw-p b3ec3000 00:00 0 
b3f23000-b5338000 r--p 00000000 08:01 1925145    /usr/share/fonts/truetype/arphic/uming.ttc
b5338000-b5350000 r--p 00000000 08:01 1936223    /usr/share/fonts/type1/gsfonts/n022003l.pfb
b5350000-b538c000 r--p 00000000 08:01 2793569    /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf
b53d6000-b53f0000 r--p 00000000 08:01 2793558    /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf
b53f0000-b5437000 r--p 00000000 08:01 1925168    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
b5437000-b5483000 r--p 00000000 08:01 1925167    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b5483000-b5492000 r-xp 00000000 08:01 2121855    /lib/libbz2.so.1.0.4
b5492000-b5493000 r--p 0000f000 08:01 2121855    /lib/libbz2.so.1.0.4
b5493000-b5494000 rw-p 00010000 08:01 2121855    /lib/libbz2.so.1.0.4
b5494000-b54c5000 r-xp 00000000 08:01 1803968    /usr/lib/libcroco-0.6.so.3.0.1
b54c5000-b54c8000 rw-p 00030000 08:01 1803968    /usr/lib/libcroco-0.6.so.3.0.1
b54c8000-b54f8000 r-xp 00000000 08:01 1803572    /usr/lib/libgsf-1.so.114.0.8
b54f8000-b54fa000 r--p 0002f000 08:01 1803572    /usr/lib/libgsf-1.so.114.0.8
b54fa000-b54fb000 rw-p 00031000 08:01 1803572    /usr/lib/libgsf-1.so.114.0.8
b54fb000-b54fc000 rw-p b54fb000 00:00 0 
b54fc000-b552d000 r-xp 00000000 08:01 1802392    /usr/lib/librsvg-2.so.2.22.3
b552d000-b552e000 r--p 00030000 08:01 1802392    /usr/lib/librsvg-2.so.2.22.3
b552e000-b552f000 rw-p 00031000 08:01 1802392    /usr/lib/librsvg-2.so.2.22.3
b553a000-b5547000 r--p 00000000 08:01 1925162    /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMono.ttf
b5547000-b5548000 r-xp 00000000 08:01 3735583    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5548000-b5549000 r--p 00000000 08:01 3735583    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5549000-b554a000 rw-p 00001000 08:01 3735583    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b554a000-b55aa000 rw-s 00000000 00:09 2588726    /SYSV00000000 (deleted)
b55aa000-b55ab000 r--p 00000000 08:01 2105367    /usr/share/vte/termcap/xterm
b55ab000-b56af000 rw-p b55ab000 00:00 0 
b56af000-b572c000 r--p 00000000 08:01 1925136    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b572c000-b5974000 rw-p b572c000 00:00 0 
b5974000-b65a7000 r--s 00000000 08:01 2703397    /var/cache/apt/pkgcache.bin
b65a7000-b6607000 rw-s 00000000 00:09 2555957    /SYSV00000000 (deleted)
b6607000-b660d000 r-xp 00000000 08:01 1826868    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b660d000-b660e000 r--p 00005000 08:01 1826868    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b660e000-b660f000 rw-p 00006000 08:01 1826868    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b660f000-b6713000 rw-p b660f000 00:00 0 
b6713000-b679c000 r--p 00000000 08:01 1925166    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b679c000-b68a0000 rw-p b679c000 00:00 0 
b68a0000-b68a2000 r-xp 00000000 08:01 1859654    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68a2000-b68a3000 r--p 00001000 08:01 1859654    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68a3000-b68a4000 rw-p 00002000 08:01 1859654    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68a4000-b6939000 r--p 00000000 08:01 1925165    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6939000-b693f000 r--s 00000000 08:01 2704714    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b693f000-b6940000 r--s 00000000 08:01 2704837    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
b6940000-b6945000 r--s 00000000 08:01 2704825    /var/cache/fontconfig/e25ca923d7a08ab6b0777bd7eb77ea77-x86.cache-2
b6945000-b6948000 r--s 00000000 08:01 2704813    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6948000-b694a000 r--s 00000000 08:01 2704796    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b694a000-b6951000 r-xp 00000000 08:01 2139370    /lib/tls/i686/cmov/librt-2.8.90.so
b6951000-b6952000 r--p 00007000 08:01 2139370    /lib/tls/i686/cmov/librt-2.8.90.so
b6952000-b6953000 rw-p 00008000 08:01 2139370    /lib/tls/i686/cmov/librt-2.8.90.so
b6953000-b6956000 r--s 00000000 08:01 2704792    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b6956000-b6957000 r--s 00000000 08:01 2704789    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6957000-b695a000 r--s 00000000 08:01 2704774    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b695a000-b6961000 r--s 00000000 08:01 2704772    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6961000-b6964000 r--s 00000000 08:01 2704770    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6964000-b696c000 r--s 00000000 08:01 2704715    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b696c000-b6977000 r--s 00000000 08:01 2704767    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6977000-b6979000 r--s 00000000 08:01 2704758    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b6979000-b699b000 r--s 00000000 08:01 2704756    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b699b000-b69b4000 r--s 00000000 08:01 1876812    /usr/share/mime/mime.cache
b69b4000-b6db2000 r--p 00000000 08:01 2007749    /usr/share/icons/hicolor/icon-theme.cache
b6db2000-b6dd9000 r-xp 00000000 08:01 1826926    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6dd9000-b6dda000 r--p 00026000 08:01 1826926    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6dda000-b6ddb000 rw-p 00027000 08:01 1826926    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6ddb000-b6de5000 r-xp 00000000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6de5000-b6de6000 r--p 00009000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6de6000-b6de7000 rw-p 0000a000 08:01 2139359    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6de7000-b6df0000 r-xp 00000000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6df0000-b6df1000 r--p 00008000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6df1000-b6df2000 rw-p 00009000 08:01 2139361    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6df2000-b6e07000 r-xp 00000000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6e07000-b6e08000 r--p 00014000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6e08000-b6e09000 rw-p 00015000 08:01 2139349    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6e09000-b6e0b000 rw-p b6e09000 00:00 0 
b6e0b000-b6e12000 r-xp 00000000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6e12000-b6e13000 r--p 00006000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6e13000-b6e14000 rw-p 00007000 08:01 2139353    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b6e15000-b6e18000 r--s 00000000 08:01 2704752    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6e18000-b6e1f000 r--s 00000000 08:01 2704712    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6e1f000-b6e25000 r--s 00000000 08:01 2704582    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6e25000-b6e2c000 r--s 00000000 08:01 2704735    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6e2c000-b6e6b000 r--p 00000000 08:01 1827708    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e6b000-b6f4c000 r--p 00000000 08:01 1827707    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f4c000-b6f4f000 rw-p b6f4c000 00:00 0 
b6f4f000-b6f53000 r-xp 00000000 08:01 1805508    /usr/lib/libXdmcp.so.6.0.0
b6f53000-b6f54000 rw-p 00003000 08:01 1805508    /usr/lib/libXdmcp.so.6.0.0
b6f54000-b6f55000 rw-p b6f54000 00:00 0 
b6f55000-b6f57000 r-xp 00000000 08:01 1802506    /usr/lib/libXau.so.6.0.0
b6f57000-b6f58000 rw-p 00001000 08:01 1802506    /usr/lib/libXau.so.6.0.0
b6f58000-b6f59000 r-xp 00000000 08:01 1802630    /usr/lib/libxcb-xlib.so.0.0.0
b6f59000-b6f5a000 r--p 00000000 08:01 1802630    /usr/lib/libxcb-xlib.so.0.0.0
b6f5a000-b6f5b000 rw-p 00001000 08:01 1802630    /usr/lib/libxcb-xlib.so.0.0.0
b6f5b000-b6f88000 r-xp 00000000 08:01 2121808    /lib/libncurses.so.5.6
b6f88000-b6f8b000 rw-p 0002c000 08:01 2121808    /lib/libncurses.so.5.6
b6f8b000-b6fa0000 r-xp 00000000 08:01 1803532    /usr/lib/libICE.so.6.3.0
b6fa0000-b6fa1000 rw-p 00014000 08:01 1803532    /usr/lib/libICE.so.6.3.0
b6fa1000-b6fa4000 rw-p b6fa1000 00:00 0 
b6fa4000-b6fab000 r-xp 00000000 08:01 1805506    /usr/lib/libSM.so.6.0.0
b6fab000-b6fac000 r--p 00006000 08:01 1805506    /usr/lib/libSM.so.6.0.0
b6fac000-b6fad000 rw-p 00007000 08:01 1805506    /usr/lib/libSM.so.6.0.0
b6fad000-b6fd5000 r-xp 00000000 08:01 2121752    /lib/libpcre.so.3.12.1
b6fd5000-b6fd6000 r--p 00027000 08:01 2121752    /lib/libpcre.so.3.12.1
b6fd6000-b6fd7000 rw-p 00028000 08:01 2121752    /lib/libpcre.so.3.12.1
b6fd7000-b6ffb000 r-xp 00000000 08:01 1805530    /usr/lib/libexpat.so.1.5.2
b6ffb000-b6ffd000 r--p 00023000 08:01 1805530    /usr/lib/libexpat.so.1.5.2
b6ffd000-b6ffe000 rw-p 00025000 08:01 1805530    /usr/lib/libexpat.so.1.5.2
b6ffe000-b7015000 r-xp 00000000 08:01 1805511    /usr/lib/libxcb.so.1.0.0
b7015000-b7016000 r--p 00016000 08:01 1805511    /usr/lib/libxcb.so.1.0.0
b7016000-b7017000 rw-p 00017000 08:01 1805511    /usr/lib/libxcb.so.1.0.0
b7017000-b701d000 r-xp 00000000 08:01 1804408    /usr/lib/libxcb-render.so.0.0.0
b701d000-b701e000 r--p 00005000 08:01 1804408    /usr/lib/libxcb-render.so.0.0.0
b701e000-b701f000 rw-p 00006000 08:01 1804408    /usr/lib/libxcb-render.so.0.0.0
b701f000-b7020000 rw-p b701f000 00:00 0 
b7020000-b7023000 r-xp 00000000 08:01 1805622    /usr/lib/libxcb-render-util.so.0.0.0
b7023000-b7024000 r--p 00002000 08:01 1805622    /usr/lib/libxcb-render-util.so.0.0.0
b7024000-b7025000 rw-p 00003000 08:01 1805622    /usr/lib/libxcb-render-util.so.0.0.0
b7025000-b7049000 r-xp 00000000 08:01 1803290    /usr/lib/libpng12.so.0.27.0
b7049000-b704a000 r--p 00023000 08:01 1803290    /usr/lib/libpng12.so.0.27.0
b704a000-b704b000 rw-p 00024000 08:01 1803290    /usr/lib/libpng12.so.0.27.0
b704b000-b708a000 r-xp 00000000 08:01 1805603    /usr/lib/libpixman-1.so.0.12.0
b708a000-b708c000 r--p 0003e000 08:01 1805603    /usr/lib/libpixman-1.so.0.12.0
b708c000-b708d000 rw-p 00040000 08:01 1805603    /usr/lib/libpixman-1.so.0.12.0
b708d000-b70a5000 r-xp 00000000 08:01 2122311    /lib/libselinux.so.1
b70a5000-b70a6000 r--p 00017000 08:01 2122311    /lib/libselinux.so.1
b70a6000-b70a7000 rw-p 00018000 08:01 2122311    /lib/libselinux.so.1
b70a7000-b70af000 r-xp 00000000 08:01 1803575    /usr/lib/libXcursor.so.1.0.2
b70af000-b70b0000 rw-p 00007000 08:01 1803575    /usr/lib/libXcursor.so.1.0.2
b70b0000-b70b1000 rw-p b70b0000 00:00 0 
b70b1000-b70b6000 r-xp 00000000 08:01 1802839    /usr/lib/libXrandr.so.2.1.0
b70b6000-b70b7000 r--p 00005000 08:01 1802839    /usr/lib/libXrandr.so.2.1.0
b70b7000-b70b8000 rw-p 00006000 08:01 1802839    /usr/lib/libXrandr.so.2.1.0
b70b8000-b70c0000 r-xp 00000000 08:01 1803923    /usr/lib/libXi.so.6.0.0
b70c0000-b70c1000 r--p 00007000 08:01 1803923    /usr/lib/libXi.so.6.0.0
b70c1000-b70c2000 rw-p 00008000 08:01 1803923    /usr/lib/libXi.so.6.0.0
b70c2000-b70c4000 r-xp 00000000 08:01 1803387    /usr/lib/libXinerama.so.1.0.0
b70c4000-b70c5000 rw-p 00001000 08:01 1803387    /usr/lib/libXinerama.so.1.0.0
b70c5000-b70cd000 r-xp 00000000 08:01 1803425    /usr/lib/libXrender.so.1.3.0
b70cd000-b70ce000 r--p 00007000 08:01 1803425    /usr/lib/libXrender.so.1.3.0
b70ce000-b70cf000 rw-p 00008000 08:01 1803425    /usr/lib/libXrender.so.1.3.0
b70cf000-b70dc000 r-xp 00000000 08:01 1804840    /usr/lib/libXext.so.6.4.0
b70dc000-b70de000 rw-p 0000c000 08:01 1804840    /usr/lib/libXext.so.6.4.0
b70de000-b70e0000 r-xp 00000000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b70e0000-b70e1000 r--p 00001000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b70e1000-b70e2000 rw-p 00002000 08:01 2139300    /lib/tls/i686/cmov/libdl-2.8.90.so
b70e2000-b70e3000 rw-p b70e2000 00:00 0 
b70e3000-b70e7000 r-xp 00000000 08:01 1803585    /usr/lib/libXfixes.so.3.1.0
b70e7000-b70e8000 rw-p 00003000 08:01 1803585    /usr/lib/libXfixes.so.3.1.0
b70e8000-b70ea000 r-xp 00000000 08:01 1804637    /usr/lib/libXdamage.so.1.1.0
b70ea000-b70eb000 rw-p 00001000 08:01 1804637    /usr/lib/libXdamage.so.1.1.0
b70eb000-b70ed000 r-xp 00000000 08:01 1804626    /usr/lib/libXcomposite.so.1.0.0
b70ed000-b70ee000 r--p 00001000 08:01 1804626    /usr/lib/libXcomposite.so.1.0.0
b70ee000-b70ef000 rw-p 00002000 08:01 1804626    /usr/lib/libXcomposite.so.1.0.0
b70ef000-b70f1000 r-xp 00000000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b70f1000-b70f2000 r--p 00001000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b70f2000-b70f3000 rw-p 00002000 08:01 2139374    /lib/tls/i686/cmov/libutil-2.8.90.so
b70f3000-b724b000 r-xp 00000000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b724b000-b724d000 r--p 00158000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b724d000-b724e000 rw-p 0015a000 08:01 2139296    /lib/tls/i686/cmov/libc-2.8.90.so
b724e000-b7252000 rw-p b724e000 00:00 0 
b7252000-b725f000 r-xp 00000000 08:01 2124012    /lib/libgcc_s.so.1
b725f000-b7260000 r--p 0000c000 08:01 2124012    /lib/libgcc_s.so.1
b7260000-b7261000 rw-p 0000d000 08:01 2124012    /lib/libgcc_s.so.1
b7261000-b7344000 r-xp 00000000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7344000-b7348000 r--p 000e3000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7348000-b7349000 rw-p 000e7000 08:01 1804966    /usr/lib/libstdc++.so.6.0.10
b7349000-b734f000 rw-p b7349000 00:00 0 
b734f000-b7494000 r-xp 00000000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b7494000-b74a0000 r--p 00145000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b74a0000-b74a1000 rw-p 00151000 08:01 1802857    /usr/lib/libxapian.so.15.5.1
b74a1000-b7512000 r-xp 00000000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7512000-b7513000 r--p 00071000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7513000-b7514000 rw-p 00072000 08:01 1806512    /usr/lib/libept.so.0.5.25
b7514000-b7529000 r-xp 00000000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7529000-b752a000 r--p 00014000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b752a000-b752b000 rw-p 00015000 08:01 2139367    /lib/tls/i686/cmov/libpthread-2.8.90.so
b752b000-b752d000 rw-p b752b000 00:00 0 
b752d000-b7530000 r-xp 00000000 08:01 1803422    /usr/lib/liblaunchpad-integration.so.1.0.0
b7530000-b7531000 r--p 00002000 08:01 1803422    /usr/lib/liblaunchpad-integration.so.1.0.0
b7531000-b7532000 rw-p 00003000 08:01 1803422    /usr/lib/liblaunchpad-integration.so.1.0.0
b7532000-b7533000 rw-p b7532000 00:00 0 
b7533000-b7545000 r-xp 00000000 08:01 1803604    /usr/lib/libXft.so.2.1.2
b7545000-b7546000 r--p 00011000 08:01 1803604    /usr/lib/libXft.so.2.1.2
b7546000-b7547000 rw-p 00012000 08:01 1803604    /usr/lib/libXft.so.2.1.2
b7547000-b756b000 r-xp 00000000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b756b000-b756c000 r--p 00023000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b756c000-b756d000 rw-p 00024000 08:01 2139301    /lib/tls/i686/cmov/libm-2.8.90.so
b756d000-b7658000 r-xp 00000000 08:01 1802790    /usr/lib/libX11.so.6.2.0
b7658000-b7659000 r--p 000ea000 08:01 1802790    /usr/lib/libX11.so.6.2.0
b7659000-b765b000 rw-p 000eb000 08:01 1802790    /usr/lib/libX11.so.6.2.0
b765b000-b765c000 rw-p b765b000 00:00 0 
b765c000-b7666000 r-xp 00000000 08:01 1803757    /usr/lib/libpangox-1.0.so.0.2202.0
b7666000-b7667000 ---p 0000a000 08:01 1803757    /usr/lib/libpangox-1.0.so.0.2202.0
b7667000-b7668000 r--p 0000a000 08:01 1803757    /usr/lib/libpangox-1.0.so.0.2202.0
b7668000-b7669000 rw-p 0000b000 08:01 1803757    /usr/lib/libpangox-1.0.so.0.2202.0
b7669000-b766f000 r-xp 00000000 08:01 1803761    /usr/lib/libpangoxft-1.0.so.0.2202.0
b766f000-b7670000 r--p 00005000 08:01 1803761    /usr/lib/libpangoxft-1.0.so.0.2202.0
b7670000-b7671000 rw-p 00006000 08:01 1803761    /usr/lib/libpangoxft-1.0.so.0.2202.0
b7671000-b7725000 r-xp 00000000 08:01 1806514    /usr/lib/libvte.so.9.3.3
b7725000-b7727000 r--p 000b3000 08:01 1806514    /usr/lib/libvte.so.9.3.3
b7727000-b7729000 rw-p 000b5000 08:01 1806514    /usr/lib/libvte.so.9.3.3
b7729000-b772a000 rw-p b7729000 00:00 0 
b772a000-b77df000 r-xp 00000000 08:01 1802738    /usr/lib/libglib-2.0.so.0.1800.2
b77df000-b77e0000 r--p 000b4000 08:01 1802738    /usr/lib/libglib-2.0.so.0.1800.2
b77e0000-b77e1000 rw-p 000b5000 08:01 1802738    /usr/lib/libglib-2.0.so.0.1800.2
b77e1000-b77e4000 r-xp 00000000 08:01 1803439    /usr/lib/libgmodule-2.0.so.0.1800.2
b77e4000-b77e5000 r--p 00002000 08:01 1803439    /usr/lib/libgmodule-2.0.so.0.1800.2
b77e5000-b77e6000 rw-p 00003000 08:01 1803439    /usr/lib/libgmodule-2.0.so.0.1800.2
b77e6000-b7822000 r-xp 00000000 08:01 1803603    /usr/lib/libgobject-2.0.so.0.1800.2
b7822000-b7823000 r--p 0003b000 08:01 1803603    /usr/lib/libgobject-2.0.so.0.1800.2
b7823000-b7824000 rw-p 0003c000 08:01 1803603    /usr/lib/libgobject-2.0.so.0.1800.2
b7824000-b7864000 r-xp 00000000 08:01 1802503    /usr/lib/libpango-1.0.so.0.2202.0
b7864000-b7865000 ---p 00040000 08:01 1802503    /usr/lib/libpango-1.0.so.0.2202.0
b7865000-b7866000 r--p 00040000 08:01 1802503    /usr/lib/libpango-1.0.so.0.2202.0
b7866000-b7867000 rw-p 00041000 08:01 1802503    /usr/lib/libpango-1.0.so.0.2202.0
b7867000-b7892000 r-xp 00000000 08:01 1806447    /usr/lib/libfontconfig.so.1.3.0
b7892000-b7893000 r--p 0002a000 08:01 1806447    /usr/lib/libfontconfig.so.1.3.0
b7893000-b7894000 rw-p 0002b000 08:01 1806447    /usr/lib/libfontconfig.so.1.3.0
b7894000-b78a8000 r-xp 00000000 08:01 1804505    /usr/lib/libz.so.1.2.3.3
b78a8000-b78aa000 rw-p 00013000 08:01 1804505    /usr/lib/libz.so.1.2.3.3
b78aa000-b78ab000 rw-p b78aa000 00:00 0 
b78ab000-b791c000 r-xp 00000000 08:01 1802970    /usr/lib/libfreetype.so.6.3.18
b791c000-b7920000 r--p 00070000 08:01 1802970    /usr/lib/libfreetype.so.6.3.18
b7920000-b7921000 rw-p 00074000 08:01 1802970    /usr/lib/libfreetype.so.6.3.18
b7921000-b7991000 r-xp 00000000 08:01 1804802    /usr/lib/libcairo.so.2.10800.0
b7991000-b7993000 r--p 0006f000 08:01 1804802    /usr/lib/libcairo.so.2.10800.0
b7993000-b7994000 rw-p 00071000 08:01 1804802    /usr/lib/libcairo.so.2.10800.0
b7994000-b79f9000 r-xp 00000000 08:01 1802381    /usr/lib/libgio-2.0.so.0.1800.2
b79f9000-b79fa000 ---p 00065000 08:01 1802381    /usr/lib/libgio-2.0.so.0.1800.2
b79fa000-b79fb000 r--p 00065000 08:01 1802381    /usr/lib/libgio-2.0.so.0.1800.2
b79fb000-b79fc000 rw-p 00066000 08:01 1802381    /usr/lib/libgio-2.0.so.0.1800.2
b79fc000-b7a05000 r-xp 00000000 08:01 1803739    /usr/lib/libpangocairo-1.0.so.0.2202.0
b7a05000-b7a06000 r--p 00008000 08:01 1803739    /usr/lib/libpangocairo-1.0.so.0.2202.0
b7a06000-b7a07000 rw-p 00009000 08:01 1803739    /usr/lib/libpangocairo-1.0.so.0.2202.0
b7a07000-b7a1f000 r-xp 00000000 08:01 1802285    /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
b7a1f000-b7a20000 r--p 00017000 08:01 1802285    /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
b7a20000-b7a21000 rw-p 00018000 08:01 1802285    /usr/lib/libgdk_pixbuf-2.0.so.0.1400.4
b7a21000-b7a22000 rw-p b7a21000 00:00 0 
b7a22000-b7a48000 r-xp 00000000 08:01 1803749    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7a48000-b7a49000 r--p 00025000 08:01 1803749    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7a49000-b7a4a000 rw-p 00026000 08:01 1803749    /usr/lib/libpangoft2-1.0.so.0.2202.0
b7a4a000-b7a63000 r-xp 00000000 08:01 1803209    /usr/lib/libatk-1.0.so.0.2409.1
b7a63000-b7a65000 r--p 00018000 08:01 1803209    /usr/lib/libatk-1.0.so.0.2409.1
b7a65000-b7a66000 rw-p 0001a000 08:01 1803209    /usr/lib/libatk-1.0.so.0.2409.1
b7a66000-b7aee000 r-xp 00000000 08:01 1802282    /usr/lib/libgdk-x11-2.0.so.0.1400.4
b7aee000-b7aef000 ---p 00088000 08:01 1802282    /usr/lib/libgdk-x11-2.0.so.0.1400.4
b7aef000-b7af1000 r--p 00088000 08:01 1802282    /usr/lib/libgdk-x11-2.0.so.0.1400.4
b7af1000-b7af2000 rw-p 0008a000 08:01 1802282    /usr/lib/libgdk-x11-2.0.so.0.1400.4
b7af2000-b7c27000 r-xp 00000000 08:01 1804947    /usr/lib/libxml2.so.2.6.32
b7c27000-b7c28000 ---p 00135000 08:01 1804947    /usr/lib/libxml2.so.2.6.32
b7c28000-b7c2c000 r--p 00135000 08:01 1804947    /usr/lib/libxml2.so.2.6.32
b7c2c000-b7c2d000 rw-p 00139000 08:01 1804947    /usr/lib/libxml2.so.2.6.32
b7c2d000-b7c2e000 rw-p b7c2d000 00:00 0 
b7c2e000-b7fc3000 r-xp 00000000 08:01 1803630    /usr/lib/libgtk-x11-2.0.so.0.1400.4
b7fc3000-b7fc4000 ---p 00395000 08:01 1803630    /usr/lib/libgtk-x11-2.0.so.0.1400.4
b7fc4000-b7fc8000 r--p 00395000 08:01 1803630    /usr/lib/libgtk-x11-2.0.so.0.1400.4
b7fc8000-b7fca000 rw-p 00399000 08:01 1803630    /usr/lib/libgtk-x11-2.0.so.0.1400.4
b7fca000-b7fcc000 rw-p b7fca000 00:00 0 
b7fcc000-b7fe1000 r-xp 00000000 08:01 1803629    /usr/lib/libglade-2.0.so.0.0.7
b7fe1000-b7fe2000 r--p 00015000 08:01 1803629    /usr/lib/libglade-2.0.so.0.0.7
b7fe2000-b7fe3000 rw-p 00016000 08:01 1803629    /usr/lib/libglade-2.0.so.0.0.7
b7fe3000-b7fe4000 rw-p b7fe3000 00:00 0 
b7fe4000-b7ff4000 r-xp 00000000 08:01 1804383    /usr/lib/libapt-inst-libc6.8-6.so.1.1.0
b7ff4000-b7ff5000 r--p 00010000 08:01 1804383    /usr/lib/libapt-inst-libc6.8-6.so.1.1.0
b7ff5000-b7ff6000 rw-p 00011000 08:01 1804383    /usr/lib/libapt-inst-libc6.8-6.so.1.1.0
b7ff6000-b80b5000 r-xp 00000000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b80b5000-b80b7000 r--p 000be000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b80b7000-b80b8000 rw-p 000c0000 08:01 1806521    /usr/lib/libapt-pkg-libc6.8-6.so.4.6.0
b80b8000-b80bc000 r-xp 00000000 08:01 1826853    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b80bc000-b80bd000 r--p 00003000 08:01 1826853    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b80bd000-b80be000 rw-p 00004000 08:01 1826853    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b80be000-b80bf000 r--s 00000000 08:01 2704757    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b80bf000-b80c0000 r--p 00000000 08:01 1827713    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b80c0000-b80c1000 r--p 00000000 08:01 1827716    /usr/lib/locale/en_US.utf8/LC_TIME
b80c1000-b80c2000 r--p 00000000 08:01 1827711    /usr/lib/locale/en_US.utf8/LC_MONETARY
b80c2000-b80c3000 r--p 00000000 08:01 1835012    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b80c3000-b80c4000 r--p 00000000 08:01 1827714    /usr/lib/locale/en_US.utf8/LC_PAPER
b80c4000-b80c5000 r--p 00000000 08:01 1827712    /usr/lib/locale/en_US.utf8/LC_NAME
b80c5000-b80c6000 r--p 00000000 08:01 1827706    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b80c6000-b80c7000 r--p 00000000 08:01 1827715    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b80c7000-b80c8000 r--p 00000000 08:01 1827710    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b80c8000-b80cf000 r--s 00000000 08:01 3604481    /usr/lib/gconv/gconv-modules.cache
b80cf000-b80d0000 r--p 00000000 08:01 1827709    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b80d0000-b80d2000 rw-p b80d0000 00:00 0 
b80d2000-b80ec000 r-xp 00000000 08:01 2121792    /lib/ld-2.8.90.so
b80ec000-b80ed000 r-xp b80ec000 00:00 0          [vdso]
b80ed000-b80ee000 r--p 0001a000 08:01 2121792    /lib/ld-2.8.90.so
b80ee000-b80ef000 rw-p 0001b000 08:01 2121792    /lib/ld-2.8.90.so
bf8d4000-bf8ef000 rw-p bffe5000 00:00 0          [stack]

```

---

### Post by szim90 on 2009-03-18
Never mind. Apparently, the abundance in segfaults was caused by a ram chip failure, not by faulty software.

---

