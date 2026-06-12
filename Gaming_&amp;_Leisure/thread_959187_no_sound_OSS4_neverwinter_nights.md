---
title: "no sound OSS4 neverwinter nights"
date: 2008-10-26
forum: Gaming &amp; Leisure
---

### Post by ankara on 2008-10-26
Hi, i recently changed to [OSS4]("http://www.opensound.com/") and have almost everything working as i want, with the most notible exception being Neverwinter Nights. the game runs perfectly, just with no sound. 
the terminal output of the program looks like this..
```
ALSA lib ../../src/confmisc.c:768:(parse_card) cannot find card 'NVidia'
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib ../../src/confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib ../../src/confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib ../../src/conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib ../../src/conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib ../../../src/pcm/pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
*** glibc detected *** ./nwmain: corrupted double-linked list: 0x0e0a8090 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf7c3dcb9]
/lib32/libc.so.6[0xf7c3f41e]
/lib32/libc.so.6(cfree+0x90)[0xf7c43080]
/usr/lib32/libGLcore.so.1[0xf75a9720]
/lib32/libc.so.6(exit+0xd4)[0xf7c01334]
/lib32/libc.so.6(__libc_start_main+0xe8)[0xf7be9458]
./nwmain(AIL_WAV_info+0x39)[0x804f851]
======= Memory map: ========
08048000-08623000 r-xp 00000000 08:05 3670723                            /home/backup/nwn/nwmain
08623000-087a1000 rwxp 005db000 08:05 3670723                            /home/backup/nwn/nwmain
087a1000-0ec5f000 rwxp 087a1000 00:00 0                                  [heap]
f591d000-f5b1d000 rwxs 1b17e000 00:0e 13663                              /dev/nvidia0
f5eb7000-f5eb8000 rwxs fdc06000 00:0e 13663                              /dev/nvidia0
f5f7c000-f5f7d000 rwxs fd060000 00:0e 13663                              /dev/nvidia0
f5f7d000-f5f9f000 rwxs 00000000 00:09 0                                  /SYSV00000000 (deleted)
f6200000-f6221000 rwxp f6200000 00:00 0 
f6221000-f6300000 ---p f6221000 00:00 0 
f63b0000-f63b4000 r-xp 00000000 08:11 255675                             /usr/lib32/libXfixes.so.3.1.0
f63b4000-f63b5000 rwxp 00003000 08:11 255675                             /usr/lib32/libXfixes.so.3.1.0
f63b5000-f63bd000 r-xp 00000000 08:11 255671                             /usr/lib32/libXcursor.so.1.0.2
f63bd000-f63be000 rwxp 00007000 08:11 255671                             /usr/lib32/libXcursor.so.1.0.2
f63c2000-f63c4000 rwxp f63c2000 00:00 0 
f63d2000-f63d3000 rwxs 3b2c7000 00:0e 13663                              /dev/nvidia0
f63d3000-f6412000 r-xp 00000000 08:11 227681                             /usr/lib/locale/en_GB.utf8/LC_CTYPE
f6412000-f6413000 r-xp 00000000 08:11 227682                             /usr/lib/locale/en_GB.utf8/LC_NUMERIC
f6413000-f6414000 r-xp 00000000 08:11 227683                             /usr/lib/locale/en_GB.utf8/LC_TIME
f6414000-f64f5000 r-xp 00000000 08:11 227684                             /usr/lib/locale/en_GB.utf8/LC_COLLATE
f64f5000-f64f6000 r-xp 00000000 08:11 227685                             /usr/lib/locale/en_GB.utf8/LC_MONETARY
f64f6000-f64f7000 r-xp 00000000 08:11 227687                             /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
f64f7000-f64f8000 r-xp 00000000 08:11 227688                             /usr/lib/locale/en_GB.utf8/LC_PAPER
f64f8000-f64f9000 ---p f64f8000 00:00 0 
f64f9000-f6cf9000 rwxp f64f9000 00:00 0 
f6d5d000-f6d5f000 rwxp f6d5d000 00:00 0 
f6d5f000-f6d63000 r-xp 00000000 08:11 255673                             /usr/lib32/libXdmcp.so.6.0.0
f6d63000-f6d64000 rwxp 00003000 08:11 255673                             /usr/lib32/libXdmcp.so.6.0.0
f6d64000-f6d7b000 r-xp 00000000 08:11 255669                             /usr/lib32/libxcb.so.1.0.0
f6d7b000-f6d7c000 rwxp 00016000 08:11 255669                             /usr/lib32/libxcb.so.1.0.0
f6d7c000-f6d7d000 r-xp 00000000 08:11 255668                             /usr/lib32/libxcb-xlib.so.0.0.0
f6d7d000-f6d7e000 rwxp 00000000 08:11 255668                             /usr/lib32/libxcb-xlib.so.0.0.0
f6d7e000-f6d80000 r-xp 00000000 08:11 255666                             /usr/lib32/libXau.so.6.0.0
f6d80000-f6d81000 rwxp 00001000 08:11 255666                             /usr/lib32/libXau.so.6.0.0
f6d81000-f6d93000 r-xp 00000000 08:11 255561                             /usr/lib32/libdirect-1.0.so.0.1.0
f6d93000-f6d94000 rwxp 00012000 08:11 255561                             /usr/lib32/libdirect-1.0.so.0.1.0
f6d94000-f6d95000 rwxp f6d94000 00:00 0 
f6d95000-f6d9c000 r-xp 00000000 08:11 255563                             /usr/lib32/libfusion-1.0.so.0.1.0
f6d9c000-f6d9d000 rwxp 00006000 08:11 255563                             /usr/lib32/libfusion-1.0.so.0.1.0
f6d9d000-f6dfe000 r-xp 00000000 08:11 255562                             /usr/lib32/libdirectfb-1.0.so.0.1.0
f6dfe000-f6e00000 rwxp 00060000 08:11 255562                             /usr/lib32/libdirectfb-1.0.so.0.1.0
f6e00000-f6ebf000 r-xp 00000000 08:11 255526                             /usr/lib32/libasound.so.2.0.0
f6ebf000-f6ec3000 rwxp 000bf000 08:11 255526                             /usr/lib32/libasound.so.2.0.0
f6ec3000-f6ecd000 r-xp 00000000 08:11 252481                             /usr/lib32/libgcc_s.so.1
f6ecd000-f6ece000 rwxp 0000a000 08:11 252481                             /usr/lib32/libgcc_s.so.1
f6ece000-f6fb6000 r-xp 00000000 08:11 254968                             /usr/lib32/libstdc++.so.6.0.9
f6fb6000-f6fb9000 r-xp 000e8000 08:11 254968                             /usr/lib32/libstdc++.so.6.0.9
f6fb9000-f6fbb000 rwxp 000eb000 08:11 254968                             /usr/lib32/libstdc++.so.6.0.9
f6fbb000-f6fc2000 rwxp f6fbb000 00:00 0 
f6fc2000-f6fc4000 r-xp 00000000 08:11 472052                             /lib32/libdl-2.7.so
f6fc4000-f6fc6000 rwxp 00001000 08:11 472052                             /lib32/libdl-2.7.so
f6fc6000-f70aa000 r-xp 00000000 08:11 255665                             /usr/lib32/libX11.so.6.2.0
f70aa000-f70ad000 rwxp 000e4000 08:11 255665                             /usr/lib32/libX11.so.6.2.0
f70ad000-f70ba000 r-xp 00000000 08:11 255674                             /usr/lib32/libXext.so.6.4.0
f70ba000-f70bb000 rwxp 0000d000 08:11 255674                             /usr/lib32/libXext.so.6.4.0
f70bb000-f70bc000 r-xp 00000000 08:11 360650                             /usr/lib32/tls/libnvidia-tls.so.169.12
f70bc000-f70bd000 rwxp 00000000 08:11 360650                             /usr/lib32/tls/libnvidia-tls.so.169.12
f70bd000-f7b91000 r-xp 00000000 08:11 255086                             /usr/lib32/libGLcore.so.169.12
f7b91000-f7bcd000 rwxp 00ad3000 08:11 255086                             /usr/lib32/libGLcore.so.169.12
f7bcd000-f7bd3000 rwxp f7bcd000 00:00 0 
f7bd3000-f7d1c000 r-xp 00000000 08:11 472049                             /lib32/libc-2.7.so
f7d1c000-f7d1d000 r-xp 00149000 08:11 472049                             /lib32/libc-2.7.so
f7d1d000-f7d1f000 rwxp 0014a000 08:11 472049                             /lib32/libc-2.7.so
f7d1f000-f7d22000 rwxp f7d1f000 00:00 0 
f7d22000-f7d87000 r-xp 00000000 08:11 255654                             /usr/lib32/libSDL-1.2.so.0.11.1
f7d87000-f7d89000 rwxp 00065000 08:11 255654                             /usr/lib32/libSDL-1.2.so.0.11.1
f7d89000-f7db1000 rwxp f7d89000 00:00 0 
f7db1000-f7e16000 r-xp 00000000 08:05 3670721                            /home/backup/nwn/miles/libmss.so.6.5.2
f7e16000-f7e21000 rwxp 00064000 08:05 3670721                            /home/backup/nwn/miles/libmss.so.6.5.2
f7e21000-f7e25000 rwxp f7e21000 00:00 0 
f7e25000-f7ea7000 r-xp 00000000 08:11 255582                             /usr/lib32/libGLU.so.1.3.070002
f7ea7000-f7ea8000 rwxp 00081000 08:11 255582                             /usr/lib32/libGLU.so.1.3.070002
f7ea8000-f7f30000 r-xp 00000000 08:11 255085                             /usr/lib32/libGL.so.169.12
f7f30000-f7f4b000 rwxp 00087000 08:11 255085                             /usr/lib32/libGL.so.169.12
f7f4b000-f7f4d000 rwxp f7f4b000 00:00 0 
f7f4d000-f7f61000 r-xp 00000000 08:11 472065                             /lib32/libpthread-2.7.so
f7f61000-f7f63000 rwxp 00013000 08:11 472065                             /lib32/libpthread-2.7.so
f7f63000-f7f65000 rwxp f7f63000 00:00 0 
f7f65000-f7f88000 r-xp 00000000 08:11 472053                             /lib32/libm-2.7.so
f7f88000-f7f8a000 rwxp 00023000 08:11 472053                             /lib32/libm-2.7.so
f7f8a000-f7f8b000 r-xp 00000000 08:11 227689                             /usr/lib/locale/en_GB.utf8/LC_NAME
f7f8b000-f7f8c000 r-xp 00000000 08:11 227690                             /usr/lib/locale/en_GB.utf8/LC_ADDRESS
f7f8c000-f7f8d000 r-xp 00000000 08:11 227691                             /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
f7f8d000-f7f8e000 r-xp 00000000 08:11 227692                             /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
f7f8e000-f7f8f000 r-xp 00000000 08:11 227693                             /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
f7f95000-f7f9c000 r-xp 00000000 08:11 255685                             /usr/lib32/libXrender.so.1.3.0
f7f9c000-f7f9d000 rwxp 00007000 08:11 255685                             /usr/lib32/libXrender.so.1.3.0
f7f9f000-f7fa1000 rwxp f7f9f000 00:00 0 
f7fa1000-f7fbe000 r-xp 00000000 08:11 472043                             /lib32/ld-2.7.so
f7fbe000-f7fc0000 rwxp 0001c000 08:11 472043                 Aborted
```


any ideas, much appreciated.
ta.

---

