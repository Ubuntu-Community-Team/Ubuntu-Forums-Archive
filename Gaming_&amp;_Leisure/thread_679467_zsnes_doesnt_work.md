---
title: "zsnes doesnt work"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by AvengingAngel718 on 2008-01-27
so i just went through a bit of a hassle trying to install zsnes from source code, realized i could just do an apt-get install, did that and for a moment i was happy. then i tried to start it up, and a window flashed up on my screen for about a second then closed. this happens every time i try to play. the same thing happened to the person who wrote this thread:

[http://ubuntuforums.org/showthread.php?t=678252](http://ubuntuforums.org/showthread.php?t=678252)

apparently he fixed it by changing one of the config files. would anyone be able to help me do this? i took a look at them but they seemed a little to complicated for me.

---

### Post by heatblazer on 2008-01-27
Same here. When I start it a quick window pops up and vanishes. No idea what is going on really... I remeber that I was using ZSNES on 7.04 but now I doesen`t work on 7.10.

---

### Post by FranMichaels on 2008-01-27
Run zsnes from terminal (just type zsnes)
and see if there is any error output.

If you see something about mcop, points down to my signature. Fix is there.

If it's something else, post any useful error message and I'll try and help. :KS

---

### Post by kbless7 on 2008-01-27
I'm betting on a mcop error.  Follow the above post

---

### Post by heatblazer on 2008-01-27
zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** glibc detected *** zsnes: free(): invalid pointer: 0x08948f78 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7c4bd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7c4f800]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7e13d81]
/usr/lib/libmcop.so.1(_ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x1a4)[0xac704e34]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x5f)[0xac6e106f]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDefC1ERNS_6BufferE+0xa4)[0xac6e12f4]
/usr/lib/libmcop.so.1(_ZN4Arts10IDLFileReg7startupEv+0xb5)[0xac6e1ef5]
/usr/lib/libmcop.so.1(_ZN4Arts14StartupManager7startupEv+0x3e)[0xac6b5dbe]
/usr/lib/libmcop.so.1(_ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x830)[0xac6ea840]
/usr/lib/libartscbackend.so.0(arts_backend_init+0xa0)[0xad16d360]
/usr/lib/libartsc.so.0(arts_init+0x239)[0xb788d8d9]
/usr/lib/ao/plugins-2/libarts.so(ao_plugin_test+0x17)[0xb7fbc987]
/usr/lib/libao.so.2(ao_default_driver_id+0x63)[0xb7ef0253]
zsnes[0x82ebf05]
======= Memory map: ========
08048000-08305000 r-xp 00000000 08:02 4202534    /usr/bin/zsnes
08305000-08344000 rw-p 002bc000 08:02 4202534    /usr/bin/zsnes
08344000-08c07000 rw-p 08344000 00:00 0          [heap]
ac400000-ac421000 rw-p ac400000 00:00 0 
ac421000-ac500000 ---p ac421000 00:00 0 
ac50a000-ac540000 r-xp 00000000 08:02 2454108    /usr/lib/libkmedia2_idl.so.1.0.0
ac540000-ac54e000 rw-p 00035000 08:02 2454108    /usr/lib/libkmedia2_idl.so.1.0.0
ac54e000-ac552000 r-xp 00000000 08:02 2454888    /usr/lib/libogg.so.0.5.3
ac552000-ac553000 rw-p 00003000 08:02 2454888    /usr/lib/libogg.so.0.5.3
ac553000-ac56d000 r-xp 00000000 08:02 4349645    /usr/lib/libvorbis.so.0.4.0
ac56d000-ac57b000 rw-p 0001a000 08:02 4349645    /usr/lib/libvorbis.so.0.4.0
ac57b000-ac586000 r-xp 00000000 08:02 4349654    /usr/lib/libvorbisenc.so.2.0.3
ac586000-ac674000 rw-p 0000b000 08:02 4349654    /usr/lib/libvorbisenc.so.2.0.3
ac674000-ac714000 r-xp 00000000 08:02 2454109    /usr/lib/libmcop.so.1.0.0
ac714000-ac722000 rw-p 000a0000 08:02 2454109    /usr/lib/libmcop.so.1.0.0
ac722000-ac7b2000 r-xp 00000000 08:02 2454100    /usr/lib/libartsflow_idl.so.1.0.0
ac7b2000-ac7da000 rw-p 00090000 08:02 2454100    /usr/lib/libartsflow_idl.so.1.0.0
ac7da000-ac828000 r-xp 00000000 08:02 2454112    /usr/lib/libsoundserver_idl.so.1.0.0
ac828000-ac83f000 rw-p 0004e000 08:02 2454112    /usr/lib/libsoundserver_idl.so.1.0.0
ac83f000-ac948000 r-xp 00000000 08:02 2454099    /usr/lib/libartsflow.so.1.0.0
ac948000-ac966000 rw-p 00108000 08:02 2454099    /usr/lib/libartsflow.so.1.0.0
ac966000-ac9ec000 rw-p ac966000 00:00 0 
ac9ec000-accec000 rw-s 0000b000 00:0e 17156      /dev/dri/card0
accec000-acfec000 rw-s 0000a000 00:0e 17156      /dev/dri/card0
acfec000-ad151000 rw-p acfec000 00:00 0 
ad164000-ad172000 r-xp 00000000 08:02 2454096    /usr/lib/libartscbackend.so.0.0.0
ad172000-ad175000 rw-p 0000d000 08:02 2454096    /usr/lib/libartscbackend.so.0.0.0
ad175000-ad183000 rw-p ad19a000 00:00 0 
ad183000-ad184000 rw-p ad183000 00:00 0 
ad185000-ad18c000 r-xp 00000000 08:02 2454014    /usr/lib/libvorbisfile.so.3.2.0
ad18c000-ad18d000 rw-p 00006000 08:02 2454014    /usr/lib/libvorbisfile.so.3.2.0
ad18d000-ad197000 rw-p ad18d000 00:00 0 
ad197000-ad19a000 rw-s 0029d000 00:0e 17156      /dev/dri/card0
ad19a000-ad19c000 rw-p ad19a000 00:00 0 
ad19c000-ad19d000 r-xp 00000000 08:02 2458779    /usr/lib/gconv/ISO8859-1.so
ad19d000-ad19f000 rw-p 00000000 08:02 2458779    /usr/lib/gconv/ISO8859-1.so
ad19f000-ad1e0000 rw-p ad19f000 00:00 0 
ad1e0000-ad2e0000 rw-s 0029a000 00:0e 17156      /dev/dri/card0
ad2e0000-ad920000 rw-s 00007000 00:0e 17156      /dev/dri/card0
ad920000-ada20000 rw-s 00006000 00:0e 17156      /dev/dri/card0
ada20000-ada30000 rw-s 00004000 00:0e 17156      /dev/dri/card0
ada30000-b5a10000 rw-s 00003000 00:0e 17156      /dev/dri/card0
b5a10000-b5ac0000 r-xp 00000000 08:02 2454295    /usr/lib/libstdc++.so.5.0.7
b5ac0000-b5ac5000 rw-p 000af000 08:02 2454295    /usr/lib/libstdc++.so.5.0.7
b5ac5000-b5aca000 rw-p b5ac5000 00:00 0 
b5aca000-b6358000 r-xp 00000000 08:02 2455517    /usr/lib/dri/fglrx_dri.so
b6358000-b63a3000 rw-p 0088e000 08:02 2455517    /usr/lib/dri/fglrx_dri.so
b63a3000-b642d000 rw-p b63a3000 00:00 0 
b642d000-b6431000 r-xp 00000000 08:02 2453625    /usr/lib/libXfixes.so.3.1.0
b6431000-b6432000 rw-p 00003000 08:02 2453625    /usr/lib/libXfixes.so.3.1.0
b6432000-b643a000 r-xp 00000000 08:02 2453827    /usr/lib/libXcursor.so.1.0.2
b643a000-b643b000 rw-p 00007000 08:02 2453827    /usr/lib/libXcursor.so.1.0.2
b643b000-b6440000 r-xp 00000000 08:02 2453840    /usr/lib/libXrandr.so.2.1.0
b6440000-b6441000 rw-p 00005000 08:02 2453840    /usr/lib/libXrandr.so.2.1.0
b6441000-b6448000 r-xp 00000000 08:02 2453417    /usr/lib/libXrender.so.1.3.0
b6448000-b6449000 rw-p 00006000 08:02 2453417    /usr/lib/libXrender.so.1.3.0
b6449000-b644a000 ---p b6449000 00:00 0 
b644a000-b6c4a000 rwxp b644a000 00:00 0 
b6c4a000-b7779000 rw-p b6c4a000 00:00 0 
b7779000-b77b0000 r-xp 00000000 08:02 2456120    /usr/lib/libpulse.so.0.2.0
b77b0000-b77b1000 rw-p 00037000 08:02 2456120    /usr/lib/libpulse.so.0.2.0
b77b1000-b77b8000 r--s 00000000 08:02 2452922    /usr/lib/gconv/gconv-modules.cache
b77b8000-b77ba000 rw-s 00002000 00:0e 17156      /dev/dri/card0
b77ba000-b77c1000 rwxp b77ba000 00:00 0 
b77c1000-b787d000 r-xp 00000000 08:02 2453516    /usr/lib/libglib-2.0.so.0.1400.1
b787d000-b787e000 rw-p 000bc000 08:02 2453516    /usr/lib/libglib-2.0.so.0.1400.1
b787e000-b7885000 r-xp 00000000 08:02 981229     /lib/tls/i686/cmov/librt-2.6.1.so
b7885000-b7887000 rw-p 00006000 08:02 981229     /lib/tls/i686/cmov/librt-2.6.1.so
b7887000-b788b000 r-xp 00000000 08:02 2453538    /usr/lib/libgthread-2.0.so.0.1400.1
b788b000-b788c000 rw-p 00003000 08:02 2453538    /usr/lib/libgthread-2.0.so.0.1400.1
b788c000-b7891000 r-xp 00000000 08:02 2454504    /usr/lib/libartsc.so.0.0.0
b7891000-b7892000 rw-p 00004000 08:02 2454504    /usr/lib/libartsc.so.0.0.0
b7892000-b78b2000 r-xp 00000000 08:02 2454402    /usr/lib/libaudiofile.so.0.0.2
b78b2000-b78b4000 rw-p 00020000 08:02 2454402    /usr/lib/libaudiofile.so.0.0.2
b78b4000-b78b5000 rw-s 00005000 00:0e 17156      /dev/dri/card0
b78b5000-b78b8000 r-xp 00000000 08:02 981228     /lib/libcap.so.1.10
b78b8000-b78b9000 rw-p 00002000 08:02 981228     /lib/libcap.so.1.10
b78b9000-b78bc000 r-xp 00000000 08:02 2456121    /usr/lib/libpulse-simple.so.0.0.0
b78bc000-b78bd000 rw-p 00002000 08:02 2456121    /usr/lib/libpulse-simple.so.0.0.0
b78bd000-b78bf000 r-xp 00000000 08:02 2453285    /usr/lib/ao/plugins-2/libpulse.so
b78bf000-b78c0000 rw-p 00001000 08:02 2453285    /usr/lib/ao/plugins-2/libpulse.so
b78c0000-b78c3000 r-xp 00000000 08:02 2452842    /usr/lib/ao/plugins-2/libalsa09.so
b78c3000-b78c4000 rw-p 00002000 08:02 2452842    /usr/lib/ao/plugins-2/libalsa09.so
b78c4000-b78d9000 r-xp 00000000 08:02 2454974    /usr/lib/libICE.so.6.3.0
b78d9000-b78db000 rw-p 00014000 08:02 2454974    /usr/lib/libICE.so.6.3.0
b78db000-b78dc000 rw-p b78db000 00:00 0 
b78dc000-b7929000 r-xp 00000000 08:02 2454357    /usr/lib/libXt.so.6.0.0
b7929000-b792d000 rw-p 0004c000 08:02 2454357    /usr/lib/libXt.so.6.0.0
b792d000-b7942000 r-xp 00000000 08:02 2455637    /usr/lib/libaudio.so.2.4
b7942000-b7943000 rw-p 00014000 08:02 2455637    /usr/lib/libaudio.so.2.4
b7943000-b7946000 r-xp 00000000 08:02 2453522    /usr/lib/libgmodule-2.0.so.0.1400.1
b7946000-b7947000 rw-p 00002000 08:02 2453522    /usr/lib/libgmodule-2.0.so.0.1400.1
b7947000-b7950000 r-xp 00000000 08:02 2454633    /usr/lib/libesd.so.0.2.38
b7950000-b7951000 rw-p 00009000 08:02 2454633    /usr/lib/libesd.so.0.2.38
b7951000-b7952000 r-xp 00000000 08:02 2453282    /usr/lib/ao/plugins-2/libesd.so
b7952000-b7953000 rw-p 00000000 08:02 2453282    /usr/lib/ao/plugins-2/libesd.so
b7953000-b795c000 r-xp 00000000 08:02 981199     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b795c000-b795e000 rw-p 00008000 08:02 981199     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b795e000-b7966000 r-xp 00000000 08:02 981203     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7966000-b7968000 rw-p 00007000 08:02 981203     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7968000-b797c000 r-xp 00000000 08:02 981190     /lib/tls/i686/cmov/libnsl-2.6.1.so
b797c000-b797e000 rw-p 00013000 08:02 981190     /lib/tls/i686/cmov/libnsl-2.6.1.so
b797e000-b7980000 rw-p b797e000 00:00 0 
b7980000-b7987000 r-xp 00000000 08:02 981192     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7987000-b7989000 rw-p 00006000 08:02 981192     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7989000-b798b000 rw-p b7989000 00:00 0 
b798b000-b798f000 r-xp 00000000 08:02 2453394    /usr/lib/libXdmcp.so.6.0.0
b798f000-b7990000 rw-p 00003000 08:02 2453394    /usr/lib/libXdmcp.so.6.0.0
b7990000-b7992000 r-xp 00000000 08:02 2452823    /usr/lib/libXau.so.6.0.0
b7992000-b7993000 rw-p 00001000 08:02 2452823    /usr/lib/libXau.so.6.0.0
b7993000-b7a80000 r-xp 00000000 08:02 2453414    /usr/lib/libX11.so.6.2.0
b7a80000-b7a84000 rw-p 000ed000 08:02 2453414    /usr/lib/libX11.so.6.2.0
b7a84000-b7a91000 r-xp 00000000 08:02 2453669    /usr/lib/libXext.so.6.4.0
b7a91000-b7a92000 rw-p 0000d000 08:02 2453669    /usr/lib/libXext.so.6.4.0
b7a92000-b7a93000 rw-p b7a92000 00:00 0 
b7a93000-b7aa1000 r-xp 00000000 08:02 2454943    /usr/lib/libdirect-0.9.so.25.0.0
b7aa1000-b7aa2000 rw-p 0000e000 08:02 2454943    /usr/lib/libdirect-0.9.so.25.0.0
b7aa2000-b7aa7000 r-xp 00000000 08:02 2454945    /usr/lib/libfusion-0.9.so.25.0.0
b7aa7000-b7aa8000 rw-p 00004000 08:02 2454945    /usr/lib/libfusion-0.9.so.25.0.0
b7aa8000-b7afd000 r-xp 00000000 08:02 2454944    /usr/lib/libdirectfb-0.9.so.25.0.0
b7afd000-b7aff000 rw-p 00055000 08:02 2454944    /usr/lib/libdirectfb-0.9.so.25.0.0
b7aff000-b7b01000 r-xp 00000000 08:02 981165     /lib/tls/i686/cmov/libdl-2.6.1.so
b7b01000-b7b03000 rw-p 00001000 08:02 981165     /lib/tls/i686/cmov/libdl-2.6.1.so
b7b03000-b7bc4000 r-xp 00000000 08:02 2453007    /usr/lib/libasound.so.2.0.0
b7bc4000-b7bc9000 rw-p 000c0000 08:02 2453007    /usr/lib/libasound.so.2.0.0
b7bc9000-b7bdd000 r-xp 00000000 08:02 981215     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7bdd000-b7bdf000 rw-p 00013000 08:02 981215     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7bdf000-b7be2000 rw-p b7bdf000 00:00 0 
b7be2000-b7d26000 r-xp 00000000 08:02 981145     /lib/tls/i686/cmov/libc-2.6.1.so
b7d26000-b7d27000 r--p 00143000 08:02 981145     /lib/tls/i686/cmov/libc-2.6.1.so
b7d27000-b7d29000 rw-p 00144000 08:02 981145     /lib/tls/i686/cmov/libc-2.6.1.so
b7d29000-b7d2c000 rw-p b7d29000 00:00 0 
b7d2c000-b7d36000 r-xp 00000000 08:02 981251     /lib/libgcc_s.so.1
b7d36000-b7d37000 rw-p 0000a000 08:02 981251     /lib/libgcc_s.so.1
b7d37000-b7d5a000 r-xp 00000000 08:02 981171     /lib/tls/i686/cmov/libm-2.6.1.so
b7d5a000-b7d5c000 rw-p 00023000 08:02 981171     /lib/tls/i686/cmov/libm-2.6.1.so
b7d5c000-b7e44000 r-xp 00000000 08:02 2453691    /usr/lib/libstdc++.so.6.0.9
b7e44000-b7e47000 r--p 000e8000 08:02 2453691    /usr/lib/libstdc++.so.6.0.9
b7e47000-b7e49000 rw-p 000eb000 08:02 2453691    /usr/lib/libstdc++.so.6.0.9
b7e49000-b7e4f000 rw-p b7e49000 00:00 0 
b7e4f000-b7ee7000 r-xp 00000000 08:02 2454670    /usr/lib/libGL.so.1.2
b7ee7000-b7eec000 rw-p 00098000 08:02 2454670    /usr/lib/libGL.so.1.2
b7eec000-b7eef000 rw-p b7eec000 00:00 0 
b7eef000-b7ef2000 r-xp 00000000 08:02 2453286    /usr/lib/libao.so.2.1.3
b7ef2000-b7ef3000 rw-p 00003000 08:02 2453286    /usr/lib/libao.so.2.1.3
b7ef3000-b7f15000 r-xp 00000000 08:02 2453001    /usr/lib/libpng12.so.0.15.0
b7f15000-b7f16000 rw-p 00021000 08:02 2453001    /usr/lib/libpng12.so.0.15.0
b7f16000-b7f17000 rw-p b7f16000 00:00 0 
b7f17000-b7f7c000 r-xp 00000000 08:02 2454475    /usr/lib/libSDL-1.2.so.0.11.0
b7f7c000-b7f7e000 rw-p 00065000 08:02 2454475    /usr/lib/libSDL-1.2.so.0.11.0
b7f7e000-b7fa6000 rw-p b7f7e000 00:00 0 
b7fa6000-b7fba000 r-xp 00000000 08:02 4284245    /usr/lib/libz.so.1.2.3.3
b7fba000-b7fbb000 rw-p 00013000 08:02 4284245    /usr/lib/libz.so.1.2.3.3
b7fbb000-b7fbc000 rw-p b7fbb000 00:00 0 
b7fbc000-b7fbd000 r-xp 00000000 08:02 2453281    /usr/lib/ao/plugins-2/libarts.so
b7fbd000-b7fbe000 rw-p 00000000 08:02 2453281    /usr/lib/ao/plugins-2/libarts.so
b7fbe000-b7fc5000 r-xp 00000000 08:02 2454296    /usr/lib/libSM.so.6.0.0
b7fc5000-b7fc6000 rw-p 00006000 08:02 2454296    /usr/lib/libSM.so.6.0.0
b7fc6000-b7fc7000 r-xp 00000000 08:02 2453283    /usr/lib/ao/plugins-2/libnas.so
b7fc7000-b7fc8000 rw-p 00001000 08:02 2453283    /usr/lib/ao/plugins-2/libnas.so
b7fc8000-b7fca000 r-xp 00000000 08:02 2453284    /usr/lib/ao/plugins-2/liboss.so
b7fca000-b7fcb000 rw-p 00001000 08:02 2453284    /usr/lib/ao/plugins-2/liboss.so
b7fcb000-b7fcd000 rw-p b7fcb000 00:00 0 
b7fcd000-b7fe7000 r-xp 00000000 08:02 981258     /lib/ld-2.6.1.so
b7fe7000-b7fe9000 rw-p 00019000 08:02 981258     /lib/ld-2.6.1.so
bfbcd000-bfbe0000 rwxp bfbcd000 00:00 0          [stack]
bfbe0000-bfbe3000 rw-p bfbe0000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

---

### Post by heatblazer on 2008-01-27
That was the output when I typed ZSNES in my terminal... Any ideas?

---

### Post by heatblazer on 2008-01-27
Fixed! I just typed :
zsnes -v 2 
and it is running in a window mode :) You can solve the thread :)

---

### Post by heatblazer on 2008-01-29
So what? Did you fixed your problem? If so - mark the topic for SOLVED so other users may find it as a useful hint.

---

### Post by FoxHappy on 2008-01-29
This worked for me:

```
zsnes -v 11 -ad oss
```

---

### Post by OnyxWeapon on 2008-02-01
i'm having the exact same issue as heatblazer. and his fix didn't work for me. any ideas?

---

### Post by OnyxWeapon on 2008-02-01
like blazer i see this:

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** glibc detected *** zsnes: free(): invalid pointer: 0x08948f68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7ba9d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bad800]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7d71d81]
/usr/lib/libmcop.so.1(_ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x1a4)[0xa7d97e34]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x5f)[0xa7d7406f]
/usr/lib/libmcop.so.1(_ZN4Arts9ModuleDefC1ERNS_6BufferE+0xa4)[0xa7d742f4]
/usr/lib/libmcop.so.1(_ZN4Arts10IDLFileReg7startupEv+0xb5)[0xa7d74ef5]
/usr/lib/libmcop.so.1(_ZN4Arts14StartupManager7startupEv+0x3e)[0xa7d48dbe]
/usr/lib/libmcop.so.1(_ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x830)[0xa7d7d840]
/usr/lib/libartscbackend.so.0(arts_backend_init+0xa0)[0xa8ff4360]
/usr/lib/libartsc.so.0(arts_init+0x239)[0xb7f208d9]
/usr/lib/ao/plugins-2/libarts.so(ao_plugin_test+0x17)[0xb7f25987]
/usr/lib/libao.so.2(ao_default_driver_id+0x63)[0xb7e4e253]
zsnes[0x82ebf05]
======= Memory map: ========
08048000-08305000 r-xp 00000000 08:06 130561     /usr/bin/zsnes
08305000-08344000 rw-p 002bc000 08:06 130561     /usr/bin/zsnes
08344000-08bcd000 rw-p 08344000 00:00 0          [heap]
a7a00000-a7a21000 rw-p a7a00000 00:00 0 
a7a21000-a7b00000 ---p a7a21000 00:00 0 
a7ba2000-a7bd8000 r-xp 00000000 08:06 1144851    /usr/lib/libkmedia2_idl.so.1.0.0
a7bd8000-a7be6000 rw-p 00035000 08:06 1144851    /usr/lib/libkmedia2_idl.so.1.0.0
a7be6000-a7c00000 r-xp 00000000 08:06 1144459    /usr/lib/libvorbis.so.0.4.0
a7c00000-a7c0e000 rw-p 0001a000 08:06 1144459    /usr/lib/libvorbis.so.0.4.0
a7c0e000-a7c19000 r-xp 00000000 08:06 1144461    /usr/lib/libvorbisenc.so.2.0.3
a7c19000-a7d07000 rw-p 0000b000 08:06 1144461    /usr/lib/libvorbisenc.so.2.0.3
a7d07000-a7da7000 r-xp 00000000 08:06 1144852    /usr/lib/libmcop.so.1.0.0
a7da7000-a7db5000 rw-p 000a0000 08:06 1144852    /usr/lib/libmcop.so.1.0.0
a7db5000-a7e45000 r-xp 00000000 08:06 1144843    /usr/lib/libartsflow_idl.so.1.0.0
a7e45000-a7e6d000 rw-p 00090000 08:06 1144843    /usr/lib/libartsflow_idl.so.1.0.0
a7e6d000-a7ebb000 r-xp 00000000 08:06 1144855    /usr/lib/libsoundserver_idl.so.1.0.0
a7ebb000-a7ed2000 rw-p 0004e000 08:06 1144855    /usr/lib/libsoundserver_idl.so.1.0.0
a7ed2000-a7fdb000 r-xp 00000000 08:06 1144842    /usr/lib/libartsflow.so.1.0.0
a7fdb000-a7ff9000 rw-p 00108000 08:06 1144842    /usr/lib/libartsflow.so.1.0.0
a7ff9000-a7ffe000 rw-p a7ff9000 00:00 0 
a800c000-a808d000 rw-p a800c000 00:00 0 
a808d000-a8783000 rw-s 0000b000 00:0e 18205      /dev/dri/card0
a8783000-a8e79000 rw-s 0000a000 00:0e 18205      /dev/dri/card0
a8e79000-a8fde000 rw-p a8e79000 00:00 0 
a8feb000-a8ff9000 r-xp 00000000 08:06 1144839    /usr/lib/libartscbackend.so.0.0.0
a8ff9000-a8ffc000 rw-p 0000d000 08:06 1144839    /usr/lib/libartscbackend.so.0.0.0
a8ffc000-a900a000 rw-p a9027000 00:00 0 
a900a000-a9011000 r--s 00000000 08:06 767276     /usr/lib/gconv/gconv-modules.cache
a9012000-a9019000 r-xp 00000000 08:06 1144463    /usr/lib/libvorbisfile.so.3.2.0
a9019000-a901a000 rw-p 00006000 08:06 1144463    /usr/lib/libvorbisfile.so.3.2.0
a901a000-a9024000 rw-p a901a000 00:00 0 
a9024000-a9027000 rw-s 00047000 00:0e 18205      /dev/dri/card0
a9027000-a902b000 r-xp 00000000 08:06 1144295    /usr/lib/libogg.so.0.5.3
a902b000-a902c000 rw-p 00003000 08:06 1144295    /usr/lib/libogg.so.0.5.3
a902c000-a906d000 rw-p a902c000 00:00 0 
a906d000-a921d000 rw-s 00044000 00:0e 18205      /dev/dri/card0
a921d000-a985d000 rw-s 00007000 00:0e 18205      /dev/dri/card0
a985d000-a995d000 rw-s 00006000 00:0e 18205      /dev/dri/card0
a995d000-a995e000 rw-s 00005000 00:0e 18205      /dev/dri/card0
a995e000-a996e000 rw-s 00004000 00:0e 18205      /dev/dri/card0
a996e000-b596e000 rw-s 00003000 00:0e 18205      /dev/dri/card0
b596e000-b5a1e000 r-xp 00000000 08:06 1143142    /usr/lib/libstdc++.so.5.0.7
b5a1e000-b5a23000 rw-p 000af000 08:06 1143142    /usr/lib/libstdc++.so.5.0.7
b5a23000-b5a28000 rw-p b5a23000 00:00 0 
b5a28000-b62b6000 r-xp 00000000 08:06 522257     /usr/lib/dri/fglrx_dri.so
b62b6000-b6301000 rw-p 0088e000 08:06 522257     /usr/lib/dri/fglrx_dri.so
b6301000-b638b000 rw-p b6301000 00:00 0 
b638b000-b638f000 r-xp 00000000 08:06 1143737    /usr/lib/libXfixes.so.3.1.0
b638f000-b6390000 rw-p 00003000 08:06 1143737    /usr/lib/libXfixes.so.3.1.0
b6390000-b6398000 r-xp 00000000 08:06 1143727    /usr/lib/libXcursor.so.1.0.2
b6398000-b6399000 rw-p 00007000 08:06 1143727    /usr/lib/libXcursor.so.1.0.2
b6399000-b63a0000 r-xp 00000000 08:06 1143757    /usr/lib/libXrender.so.1.3.0
b63a0000-b63a1000 rw-p 00006000 08:06 1143757    /usr/lib/libXrender.so.1.3.0
b63a1000-b63a3000 rw-p b63a1000 00:00 0 
b63a3000-b63a4000 r-xp 00000000 08:06 767223     /usr/lib/gconv/ISO8859-1.so
b63a4000-b63a6000 rw-p 00000000 08:06 767223     /usr/lib/gconv/ISO8859-1.so
b63a6000-b63a8000 rw-s 00002000 00:0e 18205      /dev/dri/card0
b63a8000-b63af000 rwxp b63a8000 00:00 0 
b63af000-b63b0000 ---p b63af000 00:00 0 
b63b0000-b6bb0000 rwxp b63b0000 00:00 0 
b6bb0000-b76df000 rw-p b6bb0000 00:00 0 
b76df000-b76e2000 r-xp 00000000 08:06 2154283    /lib/libcap.so.1.10
b76e2000-b76e3000 rw-p 00002000 08:06 2154283    /lib/libcap.so.1.10
b76e3000-b771a000 r-xp 00000000 08:06 1145037    /usr/lib/libpulse.so.0.2.0
b771a000-b771b000 rw-p 00037000 08:06 1145037    /usr/lib/libpulse.so.0.2.0
b771b000-b771e000 r-xp 00000000 08:06 1145038    /usr/lib/libpulse-simple.so.0.0.0
b771e000-b771f000 rw-p 00002000 08:06 1145038    /usr/lib/libpulse-simple.so.0.0.0
b771f000-b7734000 r-xp 00000000 08:06 1143692    /usr/lib/libICE.so.6.3.0
b7734000-b7736000 rw-p 00014000 08:06 1143692    /usr/lib/libICE.so.6.3.0
b7736000-b7737000 rw-p b7736000 00:00 0 
b7737000-b7784000 r-xp 00000000 08:06 1143761    /usr/lib/libXt.so.6.0.0
b7784000-b7788000 rw-p 0004c000 08:06 1143761    /usr/lib/libXt.so.6.0.0
b7788000-b779d000 r-xp 00000000 08:06 1144822    /usr/lib/libaudio.so.2.4
b779d000-b779e000 rw-p 00014000 08:06 1144822    /usr/lib/libaudio.so.2.4
b779e000-b779f000 rw-p b779e000 00:00 0 
b779f000-b77a4000 r-xp 00000000 08:06 1143755    /usr/lib/libXrandr.so.2.1.0
b77a4000-b77a5000 rw-p 00005000 08:06 1143755    /usr/lib/libXrandr.so.2.1.0
b77a5000-b77a8000 r-xp 00000000 08:06 1191501    /usr/lib/ao/plugins-2/libalsa09.so
b77a8000-b77a9000 rw-p 00002000 08:06 1191501    /usr/lib/ao/plugins-2/libalsa09.so
b77a9000-b77ab000 r-xp 00000000 08:06 1191505    /usr/lib/ao/plugins-2/liboss.so
b77ab000-b77ac000 rw-p 00001000 08:06 1191505    /usr/lib/ao/plugins-2/liboss.so
b77ac000-b77cc000 r-xp 00000000 08:06 1143797    /usr/lib/libaudiofile.so.0.0.2
b77cc000-b77ce000 rw-p 00020000 08:06 1143797    /usr/lib/libaudiofile.so.0.0.2
b77ce000-b77d7000 r-xp 00000000 08:06 1143913    /usr/lib/libesd.so.0.2.38
b77d7000-b77d8000 rw-p 00009000 08:06 1143913    /usr/lib/libesd.so.0.2.38
b77d8000-b7894000 r-xp 00000000 08:06 1144014    /usr/lib/libglib-2.0.so.0.1400.1
b7894000-b7895000 rw-p 000bc000 08:06 1144014    /usr/lib/libglib-2.0.so.0.1400.1
b7895000-b789c000 r-xp 00000000 08:06 2188202    /lib/tls/i686/cmov/librt-2.6.1.so
b789c000-b789e000 rw-p 00006000 08:06 2188202    /lib/tls/i686/cmov/librt-2.6.1.so
b789e000-b78a2000 r-xp 00000000 08:06 1144126    /usr/lib/libgthread-2.0.so.0.1400.1
b78a2000-b78a3000 rw-p 00003000 08:06 1144126    /usr/lib/libgthread-2.0.so.0.1400.1
b78a3000-b78a4000 rw-p b78a3000 00:00 0 
b78a4000-b78a6000 r-xp 00000000 08:06 1191506    /usr/lib/ao/plugins-2/libpulse.so
b78a6000-b78a7000 rw-p 00001000 08:06 1191506    /usr/lib/ao/plugins-2/libpulse.so
b78a7000-b78ae000 r-xp 00000000 08:06 1143710    /usr/lib/libSM.so.6.0.0
b78ae000-b78af000 rw-p 00006000 08:06 1143710    /usr/lib/libSM.so.6.0.0
b78af000-b78b0000 r-xp 00000000 08:06 1191504    /usr/lib/ao/plugins-2/libnas.so
b78b0000-b78b1000 rw-p 00001000 08:06 1191504    /usr/lib/ao/plugins-2/libnas.so
b78b1000-b78ba000 r-xp 00000000 08:06 2188189    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b78ba000-b78bc000 rw-p 00008000 08:06 2188189    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b78bc000-b78c4000 r-xp 00000000 08:06 2188193    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b78c4000-b78c6000 rw-p 00007000 08:06 2188193    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b78c6000-b78da000 r-xp 00000000 08:06 2188183    /lib/tls/i686/cmov/libnsl-2.6.1.so
b78da000-b78dc000 rw-p 00013000 08:06 2188183    /lib/tls/i686/cmov/libnsl-2.6.1.so
b78dc000-b78de000 rw-p b78dc000 00:00 0 
b78de000-b78e5000 r-xp 00000000 08:06 2188185    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b78e5000-b78e7000 rw-p 00006000 08:06 2188185    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b78e7000-b78e9000 rw-p b78e7000 00:00 0 
b78e9000-b78ed000 r-xp 00000000 08:06 1143731    /usr/lib/libXdmcp.so.6.0.0
b78ed000-b78ee000 rw-p 00003000 08:06 1143731    /usr/lib/libXdmcp.so.6.0.0
b78ee000-b78f0000 r-xp 00000000 08:06 1143720    /usr/lib/libXau.so.6.0.0
b78f0000-b78f1000 rw-p 00001000 08:06 1143720    /usr/lib/libXau.so.6.0.0
b78f1000-b79de000 r-xp 00000000 08:06 1143714    /usr/lib/libX11.so.6.2.0
b79de000-b79e2000 rw-p 000ed000 08:06 1143714    /usr/lib/libX11.so.6.2.0
b79e2000-b79ef000 r-xp 00000000 08:06 1143735    /usr/lib/libXext.so.6.4.0
b79ef000-b79f0000 rw-p 0000d000 08:06 1143735    /usr/lib/libXext.so.6.4.0
b79f0000-b79f1000 rw-p b79f0000 00:00 0 
b79f1000-b79ff000 r-xp 00000000 08:06 1143874    /usr/lib/libdirect-0.9.so.25.0.0
b79ff000-b7a00000 rw-p 0000e000 08:06 1143874    /usr/lib/libdirect-0.9.so.25.0.0
b7a00000-b7a05000 r-xp 00000000 08:06 1143940    /usr/lib/libfusion-0.9.so.25.0.0
b7a05000-b7a06000 rw-p 00004000 08:06 1143940    /usr/lib/libfusion-0.9.so.25.0.0
b7a06000-b7a5b000 r-xp 00000000 08:06 1143876    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a5b000-b7a5d000 rw-p 00055000 08:06 1143876    /usr/lib/libdirectfb-0.9.so.25.0.0
b7a5d000-b7a5f000 r-xp 00000000 08:06 2188178    /lib/tls/i686/cmov/libdl-2.6.1.so
b7a5f000-b7a61000 rw-p 00001000 08:06 2188178    /lib/tls/i686/cmov/libdl-2.6.1.so
b7a61000-b7b22000 r-xp 00000000 08:06 1143787    /usr/lib/libasound.so.2.0.0
b7b22000-b7b27000 rw-p 000c0000 08:06 1143787    /usr/lib/libasound.so.2.0.0
b7b27000-b7b3b000 r-xp 00000000 08:06 2188198    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b3b000-b7b3d000 rw-p 00013000 08:06 2188198    /lib/tls/i686/cmov/libpthread-2.6.1.so
b7b3d000-b7b40000 rw-p b7b3d000 00:00 0 
b7b40000-b7c84000 r-xp 00000000 08:06 2188172    /lib/tls/i686/cmov/libc-2.6.1.so
b7c84000-b7c85000 r--p 00143000 08:06 2188172    /lib/tls/i686/cmov/libc-2.6.1.so
b7c85000-b7c87000 rw-p 00144000 08:06 2188172    /lib/tls/i686/cmov/libc-2.6.1.so
b7c87000-b7c8a000 rw-p b7c87000 00:00 0 
b7c8a000-b7c94000 r-xp 00000000 08:06 2154307    /lib/libgcc_s.so.1
b7c94000-b7c95000 rw-p 0000a000 08:06 2154307    /lib/libgcc_s.so.1
b7c95000-b7cb8000 r-xp 00000000 08:06 2188180    /lib/tls/i686/cmov/libm-2.6.1.so
b7cb8000-b7cba000 rw-p 00023000 08:06 2188180    /lib/tls/i686/cmov/libm-2.6.1.so
b7cba000-b7da2000 r-xp 00000000 08:06 1144428    /usr/lib/libstdc++.so.6.0.9
b7da2000-b7da5000 r--p 000e8000 08:06 1144428    /usr/lib/libstdc++.so.6.0.9
b7da5000-b7da7000 rw-p 000eb000 08:06 1144428    /usr/lib/libstdc++.so.6.0.9
b7da7000-b7dad000 rw-p b7da7000 00:00 0 
b7dad000-b7e45000 r-xp 00000000 08:06 1143149    /usr/lib/libGL.so.1.2
b7e45000-b7e4a000 rw-p 00098000 08:06 1143149    /usr/lib/libGL.so.1.2
b7e4a000-b7e4d000 rw-p b7e4a000 00:00 0 
b7e4d000-b7e50000 r-xp 00000000 08:06 1143777    /usr/lib/libao.so.2.1.3
b7e50000-b7e51000 rw-p 00003000 08:06 1143777    /usr/lib/libao.so.2.1.3
b7e51000-b7e73000 r-xp 00000000 08:06 1144346    /usr/lib/libpng12.so.0.15.0
b7e73000-b7e74000 rw-p 00021000 08:06 1144346    /usr/lib/libpng12.so.0.15.0
b7e74000-b7e75000 rw-p b7e74000 00:00 0 
b7e75000-b7eda000 r-xp 00000000 08:06 1143708    /usr/lib/libSDL-1.2.so.0.11.0
b7eda000-b7edc000 rw-p 00065000 08:06 1143708    /usr/lib/libSDL-1.2.so.0.11.0
b7edc000-b7f04000 rw-p b7edc000 00:00 0 
b7f04000-b7f18000 r-xp 00000000 08:06 1144498    /usr/lib/libz.so.1.2.3.3
b7f18000-b7f19000 rw-p 00013000 08:06 1144498    /usr/lib/libz.so.1.2.3.3
b7f19000-b7f1a000 r-xp 00000000 08:06 1191503    /usr/lib/ao/plugins-2/libesd.so
b7f1a000-b7f1b000 rw-p 00000000 08:06 1191503    /usr/lib/ao/plugins-2/libesd.so
b7f1b000-b7f1e000 r-xp 00000000 08:06 1144024    /usr/lib/libgmodule-2.0.so.0.1400.1
b7f1e000-b7f1f000 rw-p 00002000 08:06 1144024    /usr/lib/libgmodule-2.0.so.0.1400.1
b7f1f000-b7f24000 r-xp 00000000 08:06 1144820    /usr/lib/libartsc.so.0.0.0
b7f24000-b7f25000 rw-p 00004000 08:06 1144820    /usr/lib/libartsc.so.0.0.0
b7f25000-b7f26000 r-xp 00000000 08:06 1191502    /usr/lib/ao/plugins-2/libarts.so
b7f26000-b7f27000 rw-p 00000000 08:06 1191502    /usr/lib/ao/plugins-2/libarts.so
b7f27000-b7f29000 rw-p b7f27000 00:00 0 
b7f29000-b7f43000 r-xp 00000000 08:06 2154260    /lib/ld-2.6.1.so
b7f43000-b7f45000 rw-p 00019000 08:06 2154260    /lib/ld-2.6.1.so
bfe9e000-bfeb1000 rwxp bfe9e000 00:00 0          [stack]
bfeb1000-bfeb4000 rw-p bfeb1000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)


however unlike blazer, none of the fixes work. am i forgetting something basic here?

---

### Post by heatblazer on 2008-02-02
Why don`t you try "zsnes -v 5" it`s just a video mode. Try various -v numbers and see what will happen.

---

