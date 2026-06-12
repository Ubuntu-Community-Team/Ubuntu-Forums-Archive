---
title: "ZSNES crashes after playing around with video options"
date: 2010-06-24
forum: Gaming &amp; Leisure
---

### Post by philthyfill on 2010-06-24
I changed some video settings in ZSNES and it crashed. I tried to relaunch it but it continued to crash. Here's the output from the command line.

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
*** glibc detected *** zsnes: double free or corruption (!prev): 0x0913cac0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x1e6591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x1e7de8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x1eaecd]
/usr/lib/libSDL-1.2.so.0(SDL_FreeSurface+0xe8)[0xca2a38]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x6e)[0xca4dae]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x53)[0xc7c833]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xc7c8ce]
/usr/lib/libSDL-1.2.so.0(+0x616f)[0xc7d16f]
[0x7bd400]
/usr/lib/libasound.so.2(snd_config_search+0x99)[0x2f4c99]
/usr/lib/libasound.so.2(+0x232f8)[0x2f82f8]
/usr/lib/libasound.so.2(snd_config_searcha_hooks+0x45)[0x2f8ac5]
/usr/lib/libasound.so.2(+0x23dac)[0x2f8dac]
/usr/lib/libasound.so.2(snd_config_search_definition+0xbb)[0x2f8fab]
/usr/lib/libasound.so.2(snd_func_refer+0x169)[0x2f9f59]
/usr/lib/libasound.so.2(+0x24140)[0x2f9140]
/usr/lib/libasound.so.2(+0x1e0e3)[0x2f30e3]
/usr/lib/libasound.so.2(+0x1e132)[0x2f3132]
/usr/lib/libasound.so.2(+0x1e132)[0x2f3132]
/usr/lib/libasound.so.2(snd_config_expand+0x238)[0x2f77a8]
/usr/lib/libasound.so.2(snd_config_search_definition+0xe4)[0x2f8fd4]
/usr/lib/libasound.so.2(+0x4b8df)[0x3208df]
/usr/lib/libSDL-1.2.so.0(+0x35253)[0xcac253]
/usr/lib/libSDL-1.2.so.0(SDL_AudioInit+0xe9)[0xc7db79]
/usr/lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x97)[0xc7c977]
/usr/lib/libSDL-1.2.so.0(SDL_Init+0x27)[0xc7ca67]
zsnes[0x82f83da]
======= Memory map: ========
00110000-00128000 r-xp 00000000 08:02 393961     /usr/lib/libxcb.so.1.1.0
00128000-00129000 r--p 00017000 08:02 393961     /usr/lib/libxcb.so.1.1.0
00129000-0012a000 rw-p 00018000 08:02 393961     /usr/lib/libxcb.so.1.1.0
0012a000-0012e000 r-xp 00000000 08:02 393230     /usr/lib/libXdmcp.so.6.0.0
0012e000-0012f000 r--p 00003000 08:02 393230     /usr/lib/libXdmcp.so.6.0.0
0012f000-00130000 rw-p 00004000 08:02 393230     /usr/lib/libXdmcp.so.6.0.0
00130000-00138000 r-xp 00000000 08:02 130989     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00138000-00139000 r--p 00007000 08:02 130989     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00139000-0013a000 rw-p 00008000 08:02 130989     /lib/tls/i686/cmov/libnss_nis-2.11.1.so
0013a000-00144000 r-xp 00000000 08:02 130985     /lib/tls/i686/cmov/libnss_files-2.11.1.so
00144000-00145000 r--p 00009000 08:02 130985     /lib/tls/i686/cmov/libnss_files-2.11.1.so
00145000-00146000 rw-p 0000a000 08:02 130985     /lib/tls/i686/cmov/libnss_files-2.11.1.so
00146000-00147000 r-xp 00000000 08:02 394090     /usr/lib/ao/plugins-2/libnas.so
00147000-00148000 r--p 00001000 08:02 394090     /usr/lib/ao/plugins-2/libnas.so
00148000-00149000 rw-p 00002000 08:02 394090     /usr/lib/ao/plugins-2/libnas.so
00149000-0015e000 r-xp 00000000 08:02 393196     /usr/lib/libICE.so.6.3.0
0015e000-0015f000 r--p 00014000 08:02 393196     /usr/lib/libICE.so.6.3.0
0015f000-00160000 rw-p 00015000 08:02 393196     /usr/lib/libICE.so.6.3.0
00160000-00162000 rw-p 00000000 00:00 0 
00162000-00165000 r-xp 00000000 08:02 131053     /lib/libuuid.so.1.3.0
00165000-00166000 r--p 00002000 08:02 131053     /lib/libuuid.so.1.3.0
00166000-00167000 rw-p 00003000 08:02 131053     /lib/libuuid.so.1.3.0
00167000-00168000 r-xp 00000000 08:02 394089     /usr/lib/ao/plugins-2/libesd.so
00168000-00169000 r--p 00000000 08:02 394089     /usr/lib/ao/plugins-2/libesd.so
00169000-0016a000 rw-p 00001000 08:02 394089     /usr/lib/ao/plugins-2/libesd.so
0016a000-00171000 r-xp 00000000 08:02 131055     /lib/libwrap.so.0.7.6
00171000-00172000 r--p 00006000 08:02 131055     /lib/libwrap.so.0.7.6
00172000-00173000 rw-p 00007000 08:02 131055     /lib/libwrap.so.0.7.6
00175000-00179000 r-xp 00000000 08:02 393275     /usr/lib/libao.so.2.1.3
00179000-0017a000 r--p 00003000 08:02 393275     /usr/lib/libao.so.2.1.3
0017a000-0017b000 rw-p 00004000 08:02 393275     /usr/lib/libao.so.2.1.3
0017b000-002ce000 r-xp 00000000 08:02 130921     /lib/tls/i686/cmov/libc-2.11.1.so
002ce000-002cf000 ---p 00153000 08:02 130921     /lib/tls/i686/cmov/libc-2.11.1.so
002cf000-002d1000 r--p 00153000 08:02 130921     /lib/tls/i686/cmov/libc-2.11.1.so
002d1000-002d2000 rw-p 00155000 08:02 130921     /lib/tls/i686/cmov/libc-2.11.1.so
002d2000-002d5000 rw-p 00000000 00:00 0 
002d5000-00398000 r-xp 00000000 08:02 393288     /usr/lib/libasound.so.2.0.0
00398000-0039c000 r--p 000c2000 08:02 393288     /usr/lib/libasound.so.2.0.0
0039c000-0039d000 rw-p 000c6000 08:02 393288     /usr/lib/libasound.so.2.0.0
0039d000-00410000 r-xp 00000000 08:02 393400     /usr/lib/libdirectfb-1.2.so.0.8.0
00410000-00411000 ---p 00073000 08:02 393400     /usr/lib/libdirectfb-1.2.so.0.8.0
00411000-00412000 r--p 00073000 08:02 393400     /usr/lib/libdirectfb-1.2.so.0.8.0
00412000-00413000 rw-p 00074000 08:02 393400     /usr/lib/libdirectfb-1.2.so.0.8.0
00413000-00414000 rw-p 00000000 00:00 0 
00414000-00463000 r-xp 00000000 08:02 393256     /usr/lib/libXt.so.6.0.0
00463000-00464000 r--p 0004e000 08:02 393256     /usr/lib/libXt.so.6.0.0
00464000-00467000 rw-p 0004f000 08:02 393256     /usr/lib/libXt.so.6.0.0
00467000-00489000 r-xp 00000000 08:02 393298     /usr/lib/libaudiofile.so.0.0.2
00489000-0048a000 r--p 00021000 08:02 393298     /usr/lib/libaudiofile.so.0.0.2
0048a000-0048c000 rw-p 00022000 08:02 393298     /usr/lib/libaudiofile.so.0.0.2
0048c000-00498000 r-xp 00000000 08:02 393240     /usr/lib/libXi.so.6.1.0
00498000-00499000 r--p 0000c000 08:02 393240     /usr/lib/libXi.so.6.1.0
00499000-0049a000 rw-p 0000d000 08:02 393240     /usr/lib/libXi.so.6.1.0
0049a000-0049c000 r-xp 00000000 08:02 394091     /usr/lib/ao/plugins-2/liboss.so
0049c000-0049d000 r--p 00001000 08:02 394091     /usr/lib/ao/plugins-2/liboss.so
0049d000-0049e000 rw-p 00002000 08:02 394091     /usr/lib/ao/plugins-2/liboss.so
004a0000-004b5000 r-xp 00000000 08:02 131023     /lib/tls/i686/cmov/libpthread-2.11.1.so
004b5000-004b6000 r--p 00014000 08:02 131023     /lib/tls/i686/cmov/libpthread-2.11.1.so
004b6000-004b7000 rw-p 00015000 08:02 131023     /lib/tls/i686/cmov/libpthread-2.11.1.so
004b7000-004b9000 rw-p 00000000 00:00 0 
004bf000-004c8000 r-xp 00000000 08:02 393427     /usr/lib/libesd.so.0.2.39
004c8000-004c9000 r--p 00008000 08:02 393427     /usr/lib/libesd.so.0.2.39
004c9000-004ca000 rw-p 00009000 08:02 393427     /usr/lib/libesd.so.0.2.39
004cc000-004e0000 r-xp 00000000 08:02 393398     /usr/lib/libdirect-1.2.so.0.8.0
004e0000-004e1000 r--p 00013000 08:02 393398     /usr/lib/libdirect-1.2.so.0.8.0
004e1000-004e2000 rw-p 00014000 08:02 393398     /usr/lib/libdirect-1.2.so.0.8.0
004e2000-00522000 r-xp 00000000 08:02 393812     /usr/lib/libpulse.so.0.12.2
00522000-00523000 r--p 00040000 08:02 393812     /usr/lib/libpulse.so.0.12.2
00523000-00524000 rw-p 00041000 08:02 393812     /usr/lib/libpulse.so.0.12.2
00524000-0056d000 r-xp 00000000 08:02 393813     /usr/lib/libpulsecommon-0.9.21.so
0056d000-0056e000 r--p 00048000 08:02 393813     /usr/lib/libpulsecommon-0.9.21.so
0056e000-0056f000 rw-p 00049000 08:02 393813     /usr/lib/libpulsecommon-0.9.21.so
0056f000-00574000 r-xp 00000000 08:02 393742     /usr/lib/libogg.so.0.6.0
00574000-00575000 r--p 00004000 08:02 393742     /usr/lib/libogg.so.0.6.0
00575000-00576000 rw-p 00005000 08:02 393742     /usr/lib/libogg.so.0.6.0
00576000-0057e000 r-xp 00000000 08:02 393226     /usr/lib/libXcursor.so.1.0.2
0057e000-0057f000 r--p 00007000 08:02 393226     /usr/lib/libXcursor.so.1.0.2
0057f000-00580000 rw-p 00008000 08:02 393226     /usr/lib/libXcursor.so.1.0.2
0058f000-005e9000 r-xp 00000000 08:02 395988     /usr/lib/mesa/libGL.so.1.2
005e9000-005ee000 r--p 00059000 08:02 395988     /usr/lib/mesa/libGL.so.1.2
005ee000-005f3000 rwxp 0005e000 08:02 395988     /usr/lib/mesa/libGL.so.1.2
005f3000-005f4000 rwxp 00000000 00:00 0 
005f4000-0062b000 r-xp 00000000 08:02 130929     /lib/libdbus-1.so.3.4.0
0062b000-0062c000 r--p 00036000 08:02 130929     /lib/libdbus-1.so.3.4.0
0062c000-0062d000 rw-p 00037000 08:02 130929     /lib/libdbus-1.so.3.4.0
0062d000-00640000 r-xp 00000000 08:02 130979     /lib/tls/i686/cmov/libnsl-2.11.1.so
00640000-00641000 r--p 00012000 08:02 130979     /lib/tls/i686/cmov/libnsl-2.11.1.so
00641000-00642000 rw-p 00013000 08:02 130979     /lib/tls/i686/cmov/libnsl-2.11.1.so
00642000-00644000 rw-p 00000000 00:00 0 
00644000-0066b000 r-xp 00000000 08:02 393929     /usr/lib/libvorbis.so.0.4.3
0066b000-0066c000 r--p 00026000 08:02 393929     /usr/lib/libvorbis.so.0.4.3
0066c000-0066d000 rw-p 00027000 08:02 393929     /usr/lib/libvorbis.so.0.4.3
00681000-00685000 r-xp 00000000 08:02 393270     /usr/lib/libXxf86vm.so.1.0.0
00685000-00686000 r--p 00003000 08:02 393270     /usr/lib/libXxf86vm.so.1.0.0
00686000-00687000 rw-p 00004000 08:02 393270     /usr/lib/libXxf86vm.so.1.0.0
00687000-006e8000 r-xp 00000000 08:02 393861     /usr/lib/libsndfile.so.1.0.21
006e8000-006e9000 ---p 00061000 08:02 393861     /usr/lib/libsndfile.so.1.0.21
006e9000-006ea000 r--p 00061000 08:02 393861     /usr/lib/libsndfile.so.1.0.21
006ea000-006eb000 rw-p 00062000 08:02 393861     /usr/lib/libsndfile.so.1.0.21
006eb000-006ef000 rw-p 00000000 00:00 0 
006fd000-00720000 r-xp 00000000 08:02 131015     /lib/libpng12.so.0.42.0
00720000-00721000 r--p 00022000 08:02 131015     /lib/libpng12.so.0.42.0
00721000-00722000 rw-p 00023000 08:02 131015     /lib/libpng12.so.0.42.0
0073f000-00742000 r-xp 00000000 08:02 394088     /usr/lib/ao/plugins-2/libalsa09.so
00742000-00743000 r--p 00002000 08:02 394088     /usr/lib/ao/plugins-2/libalsa09.so
00743000-00744000 rw-p 00003000 08:02 394088     /usr/lib/ao/plugins-2/libalsa09.so
00770000-00774000 r-xp 00000000 08:02 393234     /usr/lib/libXfixes.so.3.1.0
00774000-00775000 r--p 00003000 08:02 393234     /usr/lib/libXfixes.so.3.1.0
00775000-00776000 rw-p 00004000 08:02 393234     /usr/lib/libXfixes.so.3.1.0
0077c000-00785000 r-xp 00000000 08:02 130935     /lib/libdrm.so.2.4.0
00785000-00786000 r--p 00008000 08:02 130935     /lib/libdrm.so.2.4.0
00786000-00787000 rw-p 00009000 08:02 130935     /lib/libdrm.so.2.4.0
007bd000-007be000 r-xp 00000000 00:00 0          [vdso]
007d1000-007ee000 r-xp 00000000 08:02 130952     /lib/libgcc_s.so.1
007ee000-007ef000 r--p 0001c000 08:02 130952     /lib/libgcc_s.so.1
007ef000-007f0000 rw-p 0001d000 08:02 130952     /lib/libgcc_s.so.1
007f0000-0083b000 r-xp 00000000 08:02 393183     /usr/lib/libFLAC.so.8.2.0
0083b000-0083c000 r--p 0004a000 08:02 393183     /usr/lib/libFLAC.so.8.2.0
0083c000-0083d000 rw-p 0004b000 08:02 393183     /usr/lib/libFLAC.so.8.2.0
008ab000-008b2000 r-xp 00000000 08:02 393213     /usr/lib/libSM.so.6.0.1
008b2000-008b3000 r--p 00006000 08:02 393213     /usr/lib/libSM.so.6.0.1
008b3000-008b4000 rw-p 00007000 08:02 393213     /usr/lib/libSM.so.6.0.1
008c4000-008d9000 r-xp 00000000 08:02 393296     /usr/lib/libaudio.so.2.4
008d9000-008da000 r--p 00015000 08:02 393296     /usr/lib/libaudio.so.2.4
008da000-008db000 rw-p 00016000 08:02 393296     /usr/lib/libaudio.so.2.4
008e1000-009ca000 r-xp 00000000 08:02 393876     /usr/lib/libstdc++.so.6.0.13
009ca000-009cb000 ---p 000e9000 08:02 393876     /usr/lib/libstdc++.so.6.0.13
009cb000-009cf000 r--p 000e9000 08:02 393876     /usr/lib/libstdc++.so.6.0.13
009cf000-009d0000 rw-p 000ed000 08:02 393876     /usr/lib/libstdc++.so.6.0.13
009d0000-009d7000 rw-p 00000000 00:00 0 
00a27000-00a2d000 r-xp 00000000 08:02 130981     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00a2d000-00a2e000 r--p 00006000 08:02 130981     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00a2e000-00a2f000 rw-p 00007000 08:02 130981     /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00a87000-00a89000 r-xp 00000000 08:02 394092     /usr/lib/ao/plugins-2/libpulse.so
00a89000-00a8a000 r--p 00001000 08:02 394092     /usr/lib/ao/plugins-2/libpulse.so
00a8a000-00a8b000 rw-p 00002000 08:02 394092     /usr/lib/ao/plugins-2/libpulse.so
00ab4000-00abc000 r-xp 00000000 08:02 393459     /usr/lib/libfusion-1.2.so.0.8.0
00abc000-00abd000 r--p 00007000 08:02 393459     /usr/lib/libfusion-1.2.so.0.8.0
00abd000-00abe000 rw-p 00008000 08:02 393459     /usr/lib/libfusion-1.2.so.0.8.0
00aea000-00aed000 r-xp 00000000 08:02 393810     /usr/lib/libpulse-simple.so.0.0.3
00aed000-00aee000 r--p 00002000 08:02 393810     /usr/lib/libpulse-simple.so.0.0.3
00aee000-00aef000 rw-p 00003000 08:02 393810     /usr/lib/libpulse-simple.so.0.0.3
00b10000-00b12000 r-xp 00000000 08:02 393219     /usr/lib/libXau.so.6.0.0
00b12000-00b13000 r--p 00001000 08:02 393219     /usr/lib/libXau.so.6.0.0
00b13000-00b14000 rw-p 00002000 08:02 393219     /usr/lib/libXau.so.6.0.0
00b91000-00bb5000 r-xp 00000000 08:02 130968     /lib/tls/i686/cmov/libm-2.11.1.so
00bb5000-00bb6000 r--p 00023000 08:02 130968     /lib/tls/i686/cmov/libm-2.11.1.so
00bb6000-00bb7000 rw-p 00024000 08:02 130968     /lib/tls/i686/cmov/libm-2.11.1.so
00c0c000-00c13000 r-xp 00000000 08:02 131036     /lib/tls/i686/cmov/librt-2.11.1.so
00c13000-00c14000 r--p 00006000 08:02 131036     /lib/tls/i686/cmov/librt-2.11.1.so
00c14000-00c15000 rw-p 00007000 08:02 131036     /lib/tls/i686/cmov/librt-2.11.1.so
00c2a000-00c2e000 r-xp 00000000 08:02 393258     /usr/lib/libXtst.so.6.1.0
00c2e000-00c2f000 r--p 00003000 08:02 393258     /usr/lib/libXtst.so.6.1.0
00c2f000-00c30000 rw-p 00004000 08:02 393258     /usr/lib/libXtst.so.6.1.0
00c77000-00cdb000 r-xp 00000000 08:02 403439     /usr/lib/libSDL-1.2.so.0.11.3
00cdb000-00cdc000 r--p 00063000 08:02 403439     /usr/lib/libSDL-1.2.so.0.11.3
00cdc000-00cdd000 rw-p 00064000 08:02 403439     /usr/lib/libSDL-1.2.so.0.11.3
00cdd000-00d05000 rw-p 00000000 00:00 0 
00d31000-00d3f000 r-xp 00000000 08:02 393232     /usr/lib/libXext.so.6.4.0
00d3f000-00d40000 r--p 0000d000 08:02 393232     /usr/lib/libXext.so.6.4.0
00d40000-00d41000 rw-p 0000e000 08:02 393232     /usr/lib/libXext.so.6.4.0
00d43000-00d4b000 r-xp 00000000 08:02 393252     /usr/lib/libXrender.so.1.3.0
00d4b000-00d4c000 r--p 00007000 08:02 393252     /usr/lib/libXrender.so.1.3.0
00d4c000-00d4d000 rw-p 00008000 08:02 393252     /usr/lib/libXrender.so.1.3.0
00d71000-00d84000 r-xp 00000000 08:02 131060     /lib/libz.so.1.2.3.3
00d84000-00d85000 r--p 00012000 08:02 131060     /lib/libz.so.1.2.3.3
00d85000-00d86000 rw-p 00013000 08:02 131060     /lib/libz.so.1.2.3.3
00dbc000-00dbe000 r-xp 00000000 08:02 393228     /usr/lib/libXdamage.so.1.1.0
00dbe000-00dbf000 r--p 00001000 08:02 393228     /usr/lib/libXdamage.so.1.1.0
00dbf000-00dc0000 rw-p 00002000 08:02 393228     /usr/lib/libXdamage.so.1.1.0
00dde000-00df9000 r-xp 00000000 08:02 130892     /lib/ld-2.11.1.soAborted

```Is there a file I can edit to make this work again?

Video card: Intel Mobile 945GME Express Integrated Graphics Controller

---

### Post by dfreer on 2010-06-24
~/.zsnes/ contains all of the configuration files (and I think saved games as well). It's weird that zsnes would suddenly start crashing just because you changed a video setting.

In particular, I think ~/.zsnes/zsnesl.cfg is the file but I can't remember for sure.

---

