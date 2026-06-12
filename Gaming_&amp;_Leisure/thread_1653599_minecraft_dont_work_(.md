---
title: "minecraft dont work :("
date: 2010-12-27
forum: Gaming &amp; Leisure
---

### Post by ravergames on 2010-12-27
At first: I used the serach function (i used Goggle too);

Minecraft starts but when i generate a new level minecraft stops.

and i get a error lof file here:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb78dc424, pid=2059, tid=1510865776
#
# JRE version: 6.0_22-b04
# Java VM: Java HotSpot(TM) Server VM (17.1-b03 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x0000080b

Registers:
EAX=0x00000000, EBX=0x0000080b, ECX=0x0000082a, EDX=0x0000000b
ESP=0x5a0df27c, EBP=0x5a0df294, ESI=0x00000020, EDI=0xb78c7ff4
EIP=0xb78dc424, CR2=0x00000004, EFLAGS=0x00000202

Top of Stack: (sp=0x5a0df27c)
0x5a0df27c:   5a0df294 0000000b 0000082a b78bf990
0x5a0df28c:   b78c7ff4 6d5bc880 5a0df398 6d0d88a3
0x5a0df29c:   0000000b 00000000 00000000 00000000
0x5a0df2ac:   00001000 00000000 00000000 00000000
0x5a0df2bc:   00000000 00000000 7fffffff fffffffe
0x5a0df2cc:   ffffffff ffffffff ffffffff ffffffff
0x5a0df2dc:   ffffffff ffffffff ffffffff ffffffff
0x5a0df2ec:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb78dc424)
0xb78dc414:   51 52 55 89 e5 0f 34 90 90 90 90 90 90 90 eb f3
0xb78dc424:   5d 5a 59 c3 00 2e 73 68 73 74 72 74 61 62 00 2e 

Stack: [0x5a0cf000,0x5a0e0000],  sp=0x5a0df27c,  free space=405a0dec00k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x424]  __kernel_vsyscall+0x10
C  [fglrx_dri.so+0x167e8a3]
C  [libpthread.so.0+0x5cc9]


[error occurred during error reporting (printing target Java thread stack), id 0xb]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 229376K, used 37894K [0x9e480000, 0xae480000, 0xb39d0000)
  eden space 196608K, 19% used [0x9e480000,0xa0981bf0,0xaa480000)
  from space 32768K, 0% used [0xac480000,0xac480000,0xae480000)
  to   space 32768K, 0% used [0xaa480000,0xaa480000,0xac480000)
 PSOldGen        total 524288K, used 12288K [0x739d0000, 0x939d0000, 0x9e480000)
  object space 524288K, 2% used [0x739d0000,0x745d0368,0x939d0000)
 PSPermGen       total 32256K, used 14407K [0x6f9d0000, 0x71950000, 0x739d0000)
  object space 32256K, 44% used [0x6f9d0000,0x707e1c88,0x71950000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 17304679   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 17304679   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/bin/java
08912000-09b92000 rwxp 00000000 00:00 0          [heap]
59a7b000-59a7e000 ---p 00000000 00:00 0 
59a7e000-59acc000 rwxp 00000000 00:00 0 
59acc000-59acd000 ---p 00000000 00:00 0 
59acd000-59ccd000 rwxp 00000000 00:00 0 
59ccd000-59cce000 ---p 00000000 00:00 0 
59cce000-59ece000 rwxp 00000000 00:00 0 
59ece000-59ecf000 ---p 00000000 00:00 0 
59ecf000-5a0cf000 rwxp 00000000 00:00 0 
5a0cf000-5a0d0000 ---p 00000000 00:00 0 
5a0d0000-5a0e0000 rwxp 00000000 00:00 0 
5a0e0000-5a0e3000 ---p 00000000 00:00 0 
5a0e3000-64171000 rwxp 00000000 00:00 0 
64171000-64172000 ---p 00000000 00:00 0 
64172000-64972000 rwxp 00000000 00:00 0 
64972000-64973000 ---p 00000000 00:00 0 
64973000-65173000 rwxp 00000000 00:00 0 
65173000-69174000 rwxs 00000000 00:10 16150      /dev/shm/pulse-shm-4017809543
69174000-69179000 r-xp 00000000 08:01 15601068   /usr/lib/libogg.so.0.7.0
69179000-6917a000 r-xp 00004000 08:01 15601068   /usr/lib/libogg.so.0.7.0
6917a000-6917b000 rwxp 00005000 08:01 15601068   /usr/lib/libogg.so.0.7.0
6917b000-691a1000 r-xp 00000000 08:01 15601304   /usr/lib/libvorbis.so.0.4.4
691a1000-691a2000 r-xp 00025000 08:01 15601304   /usr/lib/libvorbis.so.0.4.4
691a2000-691a3000 rwxp 00026000 08:01 15601304   /usr/lib/libvorbis.so.0.4.4
691a3000-69308000 r-xp 00000000 08:01 15601306   /usr/lib/libvorbisenc.so.2.0.7
69308000-69309000 ---p 00165000 08:01 15601306   /usr/lib/libvorbisenc.so.2.0.7
69309000-6931a000 r-xp 00165000 08:01 15601306   /usr/lib/libvorbisenc.so.2.0.7
6931a000-6931b000 rwxp 00176000 08:01 15601306   /usr/lib/libvorbisenc.so.2.0.7
6931b000-69365000 r-xp 00000000 08:01 15600343   /usr/lib/libFLAC.so.8.2.0
69365000-69366000 r-xp 00049000 08:01 15600343   /usr/lib/libFLAC.so.8.2.0
69366000-69367000 rwxp 0004a000 08:01 15600343   /usr/lib/libFLAC.so.8.2.0
69367000-693a1000 r-xp 00000000 08:01 10092601   /lib/libdbus-1.so.3.5.2
693a1000-693a2000 r-xp 00039000 08:01 10092601   /lib/libdbus-1.so.3.5.2
693a2000-693a3000 rwxp 0003a000 08:01 10092601   /lib/libdbus-1.so.3.5.2
693a3000-69404000 r-xp 00000000 08:01 15601212   /usr/lib/libsndfile.so.1.0.21
69404000-69405000 ---p 00061000 08:01 15601212   /usr/lib/libsndfile.so.1.0.21
69405000-69406000 r-xp 00061000 08:01 15601212   /usr/lib/libsndfile.so.1.0.21
69406000-69407000 rwxp 00062000 08:01 15601212   /usr/lib/libsndfile.so.1.0.21
69407000-6940b000 rwxp 00000000 00:00 0 
6940b000-69412000 r-xp 00000000 08:01 10092733   /lib/libwrap.so.0.7.6
69412000-69413000 r-xp 00006000 08:01 10092733   /lib/libwrap.so.0.7.6
69413000-69414000 rwxp 00007000 08:01 10092733   /lib/libwrap.so.0.7.6
69414000-6945c000 r-xp 00000000 08:01 15601145   /usr/lib/libpulsecommon-0.9.21.so
6945c000-6945d000 r-xp 00047000 08:01 15601145   /usr/lib/libpulsecommon-0.9.21.so
6945d000-6945e000 rwxp 00048000 08:01 15601145   /usr/lib/libpulsecommon-0.9.21.so
6945e000-69473000 r-xp 00000000 08:01 15600356   /usr/lib/libICE.so.6.3.0
69473000-69474000 r-xp 00014000 08:01 15600356   /usr/lib/libICE.so.6.3.0
69474000-69475000 rwxp 00015000 08:01 15600356   /usr/lib/libICE.so.6.3.0
69475000-69477000 rwxp 00000000 00:00 0 
69477000-694b6000 r-xp 00000000 08:01 15598681   /usr/lib/libpulse.so.0.12.2
694b6000-694b7000 ---p 0003f000 08:01 15598681   /usr/lib/libpulse.so.0.12.2
694b7000-694b8000 r-xp 0003f000 08:01 15598681   /usr/lib/libpulse.so.0.12.2
694b8000-694b9000 rwxp 00040000 08:01 15598681   /usr/lib/libpulse.so.0.12.2
694b9000-69579000 r-xp 00000000 08:01 15597811   /usr/lib/libasound.so.2.0.0
69579000-6957a000 ---p 000c0000 08:01 15597811   /usr/lib/libasound.so.2.0.0
6957a000-6957e000 r-xp 000c0000 08:01 15597811   /usr/lib/libasound.so.2.0.0
6957e000-6957f000 rwxp 000c4000 08:01 15597811   /usr/lib/libasound.so.2.0.0
6957f000-695a4000 r-xp 00000000 08:01 1573356    /home/otto/.minecraft/bin/natives/libopenal.so
695a4000-695a5000 rwxp 00025000 08:01 1573356    /home/otto/.minecraft/bin/natives/libopenal.so
695a5000-69692000 rwxp 00000000 00:00 0 
69692000-69695000 ---p 00000000 00:00 0 
69695000-696e3000 rwxp 00000000 00:00 0 
696e3000-696e6000 ---p 00000000 00:00 0 
696e6000-69734000 rwxp 00000000 00:00 0 
69734000-69935000 rwxs d38ac000 00:05 8623       /dev/ati/card0
69935000-69a35000 rwxs 0480b000 00:05 8623       /dev/ati/card0
69a35000-69b35000 rwxs 0480a000 00:05 8623       /dev/ati/card0
69b35000-69c35000 rwxs 04809000 00:05 8623       /dev/ati/card0
69c35000-69d35000 rwxs 04808000 00:05 8623       /dev/ati/card0
69d35000-69e35000 rwxs 04807000 00:05 8623       /dev/ati/card0
69e35000-69f35000 rwxs 04806000 00:05 8623       /dev/ati/card0
69f35000-6a035000 rwxs 04805000 00:05 8623       /dev/ati/card0
6a035000-6a135000 rwxs 04804000 00:05 8623       /dev/ati/card0
6a135000-6a235000 rwxs 04803000 00:05 8623       /dev/ati/card0
6a235000-6a335000 rwxs 04802000 00:05 8623       /dev/ati/card0
6a335000-6a435000 rwxs 04801000 00:05 8623       /dev/ati/card0
6a435000-6a535000 rwxs 04800000 00:05 8623       /dev/ati/card0
6a535000-6a635000 rwxs 047ff000 00:05 8623       /dev/ati/card0
6a635000-6a735000 rwxs 047fe000 00:05 8623       /dev/ati/card0
6a735000-6a835000 rwxs 047fd000 00:05 8623       /dev/ati/card0
6a835000-6a935000 rwxs 047fc000 00:05 8623       /dev/ati/card0
6a935000-6b239000 rwxp 00000000 00:00 0 
6b239000-6b279000 rwxs 00013000 00:05 8623       /dev/ati/card0
6b279000-6b2f9000 rwxp 00000000 00:00 0 
6b2f9000-6b32a000 r-xp 00000000 08:01 17304034   /usr/lib/fglrx/libatiadlxx.so
6b32a000-6b32b000 rwxp 00030000 08:01 17304034   /usr/lib/fglrx/libatiadlxx.so
6b32d000-6b331000 r-xp 00000000 08:01 15601674   /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6b331000-6b332000 r-xp 00003000 08:01 15601674   /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6b332000-6b333000 rwxp 00004000 08:01 15601674   /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6b333000-6b33a000 r-xs 00000000 08:01 15599348   /usr/lib/gconv/gconv-modules.cache
6b33a000-6ba3a000 rwxs 00006000 00:05 8623       /dev/ati/card0
6ba3a000-6ba5a000 rwxs fdec0000 00:05 8623       /dev/ati/card0
6ba5a000-6d46f000 r-xp 00000000 08:01 17304010   /usr/lib/fglrx/dri/fglrx_dri.so
6d46f000-6d533000 rwxp 01a15000 08:01 17304010   /usr/lib/fglrx/dri/fglrx_dri.so
6d533000-6d5be000 rwxp 00000000 00:00 0 
6d5be000-6d672000 r-xp 00000000 08:01 17304012   /usr/lib/fglrx/libGL.so.1.2
6d672000-6d67d000 rwxp 000b3000 08:01 17304012   /usr/lib/fglrx/libGL.so.1.2
6d67d000-6d682000 rwxp 00000000 00:00 0 
6d682000-6d6d9000 r-xp 00000000 08:01 1573354    /home/otto/.minecraft/bin/natives/liblwjgl.so
6d6d9000-6d6da000 r-xp 00056000 08:01 1573354    /home/otto/.minecraft/bin/natives/liblwjgl.so
6d6da000-6d6db000 rwxp 00057000 08:01 1573354    /home/otto/.minecraft/bin/natives/liblwjgl.so
6d6db000-6d6de000 ---p 00000000 00:00 0 
6d6de000-6d72c000 rwxp 00000000 00:00 0 
6d72c000-6d791000 rwxs 00000000 00:04 1343510    /SYSV00000000 (deleted)
6d791000-6d922000 rwxs 00000000 00:04 1310744    /SYSV00000000 (deleted)
6d924000-6d927000 r-xp 00000000 08:01 10092731   /lib/libuuid.so.1.3.0
6d927000-6d928000 r-xp 00002000 08:01 10092731   /lib/libuuid.so.1.3.0
6d928000-6d929000 rwxp 00003000 08:01 10092731   /lib/libuuid.so.1.3.0
6d929000-6d92c000 r-xp 00000000 08:01 15601335   /usr/lib/libxcb-atom.so.1.0.0
6d92c000-6d92d000 r-xp 00002000 08:01 15601335   /usr/lib/libxcb-atom.so.1.0.0
6d92d000-6d92e000 rwxp 00003000 08:01 15601335   /usr/lib/libxcb-atom.so.1.0.0
6d92e000-6d948000 r-xp 00000000 08:01 10092623   /lib/libgcc_s.so.1
6d948000-6d949000 r-xp 00019000 08:01 10092623   /lib/libgcc_s.so.1
6d949000-6d94a000 rwxp 0001a000 08:01 10092623   /lib/libgcc_s.so.1
6d94a000-6d94d000 ---p 00000000 00:00 0 
6d94d000-6d99b000 rwxp 00000000 00:00 0 
6d99b000-6da00000 rwxs 00000000 00:04 1212437    /SYSV00000000 (deleted)
6da00000-6da8d000 rwxp 00000000 00:00 0 
6da8d000-6db00000 ---p 00000000 00:00 0 
6db01000-6db08000 r-xp 00000000 08:01 15600377   /usr/lib/libSM.so.6.0.1
6db08000-6db09000 r-xp 00006000 08:01 15600377   /usr/lib/libSM.so.6.0.1
6db09000-6db0a000 rwxp 00007000 08:01 15600377   /usr/lib/libSM.so.6.0.1
6db0a000-6db0b000 r-xp 00000000 08:01 15600379   /usr/lib/libX11-xcb.so.1.0.0
6db0b000-6db0c000 r-xp 00000000 08:01 15600379   /usr/lib/libX11-xcb.so.1.0.0
6db0c000-6db0d000 rwxp 00001000 08:01 15600379   /usr/lib/libX11-xcb.so.1.0.0
6db0d000-6db10000 ---p 00000000 00:00 0 
6db10000-6db5e000 rwxp 00000000 00:00 0 
6db5e000-6db61000 ---p 00000000 00:00 0 
6db61000-6dbaf000 rwxp 00000000 00:00 0 
6dbaf000-6dbb2000 ---p 00000000 00:00 0 
6dbb2000-6dc00000 rwxp 00000000 00:00 0 
6dc00000-6dcfa000 rwxp 00000000 00:00 0 
6dcfa000-6dd00000 ---p 00000000 00:00 0 
6dd00000-6ddf1000 rwxp 00000000 00:00 0 
6ddf1000-6de00000 ---p 00000000 00:00 0 
6de00000-6defb000 rwxp 00000000 00:00 0 
6defb000-6df00000 ---p 00000000 00:00 0 
6df00000-6dfeb000 rwxp 00000000 00:00 0 
6dfeb000-6e000000 ---p 00000000 00:00 0 
6e000000-6e0ef000 rwxp 00000000 00:00 0 
6e0ef000-6e100000 ---p 00000000 00:00 0 
6e100000-6e1f9000 rwxp 00000000 00:00 0 
6e1f9000-6e200000 ---p 00000000 00:00 0 
6e200000-6e2fe000 rwxp 00000000 00:00 0 
6e2fe000-6e300000 ---p 00000000 00:00 0 
6e300000-6e3f8000 rwxp 00000000 00:00 0 
6e3f8000-6e400000 ---p 00000000 00:00 0 
6e400000-6e4f3000 rwxp 00000000 00:00 0 
6e4f3000-6e500000 ---p 00000000 00:00 0 
6e500000-6e507000 r-xp 00000000 08:01 17304008   /usr/lib/fglrx/libatiuki.so.1.0
6e507000-6e508000 rwxp 00006000 08:01 17304008   /usr/lib/fglrx/libatiuki.so.1.0
6e508000-6e509000 r-xp 00000000 08:01 17304742   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libjawt.so
6e509000-6e50a000 rwxp 00000000 08:01 17304742   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libjawt.so
6e50a000-6e510000 r-xp 00000000 08:01 15600418   /usr/lib/libXrandr.so.2.2.0
6e510000-6e511000 r-xp 00005000 08:01 15600418   /usr/lib/libXrandr.so.2.2.0
6e511000-6e512000 rwxp 00006000 08:01 15600418   /usr/lib/libXrandr.so.2.2.0
6e512000-6e515000 ---p 00000000 00:00 0 
6e515000-6e563000 rwxp 00000000 00:00 0 
6e563000-6e564000 r-xs 00000000 08:01 4988699    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
6e564000-6e565000 r-xs 00000000 08:01 4980800    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6e565000-6e56b000 r-xs 00000000 08:01 4980797    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6e56b000-6e56d000 r-xs 00000000 08:01 4980798    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6e56d000-6e570000 r-xs 00000000 08:01 4980807    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6e570000-6e572000 r-xs 00000000 08:01 4980786    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6e572000-6e573000 r-xs 00000000 08:01 4980808    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6e573000-6e595000 r-xs 00000000 08:01 4988713    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6e599000-6e59c000 r-xp 00000000 08:01 1573352    /home/otto/.minecraft/bin/natives/libjinput-linux.so
6e59c000-6e59d000 r-xp 00002000 08:01 1573352    /home/otto/.minecraft/bin/natives/libjinput-linux.so
6e59d000-6e59e000 rwxp 00003000 08:01 1573352    /home/otto/.minecraft/bin/natives/libjinput-linux.so
6e59e000-6e5a0000 r-xp 00000000 08:01 15600408   /usr/lib/libXinerama.so.1.0.0
6e5a0000-6e5a1000 r-xp 00001000 08:01 15600408   /usr/lib/libXinerama.so.1.0.0
6e5a1000-6e5a2000 rwxp 00002000 08:01 15600408   /usr/lib/libXinerama.so.1.0.0
6e5a2000-6e5a4000 rwxs 00002000 00:05 8623       /dev/ati/card0
6e5a4000-6e5ad000 r-xs 0010b000 08:01 1573349    /home/otto/.minecraft/bin/minecraft.jar
6e5ad000-6e5b0000 r-xs 0001f000 08:01 1573348    /home/otto/.minecraft/bin/lwjgl_util.jar
6e5b0000-6e5c0000 r-xp 00000000 08:01 10092985   /lib/libresolv-2.12.1.so
6e5c0000-6e5c1000 r-xp 00010000 08:01 10092985   /lib/libresolv-2.12.1.so
6e5c1000-6e5c2000 rwxp 00011000 08:01 10092985   /lib/libresolv-2.12.1.so
6e5c2000-6e5c4000 rwxp 00000000 00:00 0 
6e5c4000-6e5c8000 r-xp 00000000 08:01 10092980   /lib/libnss_dns-2.12.1.so
6e5c8000-6e5c9000 r-xp 00004000 08:01 10092980   /lib/libnss_dns-2.12.1.so
6e5c9000-6e5ca000 rwxp 00005000 08:01 10092980   /lib/libnss_dns-2.12.1.so
6e5ca000-6e5cc000 r-xp 00000000 08:01 10092661   /lib/libnss_mdns4_minimal.so.2
6e5cc000-6e5cd000 r-xp 00001000 08:01 10092661   /lib/libnss_mdns4_minimal.so.2
6e5cd000-6e5ce000 rwxp 00002000 08:01 10092661   /lib/libnss_mdns4_minimal.so.2
6e5cf000-6e5d4000 r-xs 00033000 08:01 1573347    /home/otto/.minecraft/bin/jinput.jar
6e5d4000-6e5dd000 r-xs 000ac000 08:01 1573346    /home/otto/.minecraft/bin/lwjgl.jar
6e5dd000-6e5e0000 ---p 00000000 00:00 0 
6e5e0000-6e62e000 rwxp 00000000 00:00 0 
6e62e000-6e632000 r-xp 00000000 08:01 15600400   /usr/lib/libXfixes.so.3.1.0
6e632000-6e633000 r-xp 00003000 08:01 15600400   /usr/lib/libXfixes.so.3.1.0
6e633000-6e634000 rwxp 00004000 08:01 15600400   /usr/lib/libXfixes.so.3.1.0
6e634000-6e63c000 r-xp 00000000 08:01 15600420   /usr/lib/libXrender.so.1.3.0
6e63c000-6e63d000 r-xp 00007000 08:01 15600420   /usr/lib/libXrender.so.1.3.0
6e63d000-6e63e000 rwxp 00008000 08:01 15600420   /usr/lib/libXrender.so.1.3.0
6e63e000-6e646000 r-xp 00000000 08:01 15600392   /usr/lib/libXcursor.so.1.0.2
6e646000-6e647000 r-xp 00007000 08:01 15600392   /usr/lib/libXcursor.so.1.0.2
6e647000-6e648000 rwxp 00008000 08:01 15600392   /usr/lib/libXcursor.so.1.0.2
6e648000-6e649000 rwxs 00005000 00:05 8623       /dev/ati/card0
6e649000-6e64f000 rwxs 00000000 00:04 1277975    /SYSV00000000 (deleted)
6e64f000-6e656000 r-xp 00000000 08:01 17304718   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libnio.so
6e656000-6e657000 rwxp 00006000 08:01 17304718   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libnio.so
6e657000-6e66a000 r-xp 00000000 08:01 17304717   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libnet.so
6e66a000-6e66b000 rwxp 00013000 08:01 17304717   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libnet.so
6e66b000-6e66e000 r-xs 00027000 08:01 17304631   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/ext/sunjce_provider.jar
6e66e000-6e675000 r-xs 00094000 08:01 16256685   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/jsse.jar
6e675000-6e678000 r-xs 00013000 08:01 16256686   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/jce.jar
6e678000-6e6f1000 r-xp 00000000 08:01 17304736   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libfontmanager.so
6e6f1000-6e6fb000 rwxp 00078000 08:01 17304736   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libfontmanager.so
6e6fb000-6e700000 rwxp 00000000 00:00 0 
6e700000-6e7ff000 rwxp 00000000 00:00 0 
6e7ff000-6e800000 ---p 00000000 00:00 0 
6e800000-6e803000 r-xs 00000000 08:01 4980794    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6e803000-6e804000 r-xs 00000000 08:01 4980790    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6e804000-6e805000 r-xs 00000000 08:01 4980783    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6e805000-6e806000 r-xs 00000000 08:01 4980792    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6e806000-6e811000 r-xs 00000000 08:01 4980784    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6e811000-6e814000 ---p 00000000 00:00 0 
6e814000-6e862000 rwxp 00000000 00:00 0 
6e862000-6e87a000 r-xp 00000000 08:01 15601347   /usr/lib/libxcb.so.1.1.0
6e87a000-6e87b000 r-xp 00017000 08:01 15601347   /usr/lib/libxcb.so.1.1.0
6e87b000-6e87c000 rwxp 00018000 08:01 15601347   /usr/lib/libxcb.so.1.1.0
6e87c000-6e888000 r-xp 00000000 08:01 15600406   /usr/lib/libXi.so.6.1.0
6e888000-6e889000 r-xp 0000b000 08:01 15600406   /usr/lib/libXi.so.6.1.0
6e889000-6e88a000 rwxp 0000c000 08:01 15600406   /usr/lib/libXi.so.6.1.0
6e88a000-6e9a3000 r-xp 00000000 08:01 15600381   /usr/lib/libX11.so.6.3.0
6e9a3000-6e9a4000 r-xp 00118000 08:01 15600381   /usr/lib/libX11.so.6.3.0
6e9a4000-6e9a6000 rwxp 00119000 08:01 15600381   /usr/lib/libX11.so.6.3.0
6e9a6000-6e9a7000 rwxp 00000000 00:00 0 
6e9a7000-6e9b5000 r-xp 00000000 08:01 15600398   /usr/lib/libXext.so.6.4.0
6e9b5000-6e9b6000 r-xp 0000d000 08:01 15600398   /usr/lib/libXext.so.6.4.0
6e9b6000-6e9b7000 rwxp 0000e000 08:01 15600398   /usr/lib/libXext.so.6.4.0
6e9b7000-6e9be000 r-xs 00000000 08:01 4980802    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6e9be000-6e9c6000 r-xs 00000000 08:01 4980803    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6e9c6000-6ea09000 r-xp 00000000 08:01 17304731   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/xawt/libmawt.so
6ea09000-6ea0b000 rwxp 00043000 08:01 17304731   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/xawt/libmawt.so
6ea0b000-6ea0c000 rwxp 00000000 00:00 0 
6ea0c000-6ea90000 r-xp 00000000 08:01 17304728   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libawt.so
6ea90000-6ea97000 rwxp 00084000 08:01 17304728   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libawt.so
6ea97000-6eabb000 rwxp 00000000 00:00 0 
6eabb000-6eabc000 ---p 00000000 00:00 0 
6eabc000-6eb3c000 rwxp 00000000 00:00 0 
6eb3c000-6eb3f000 ---p 00000000 00:00 0 
6eb3f000-6eb8d000 rwxp 00000000 00:00 0 
6eb8d000-6eb90000 ---p 00000000 00:00 0 
6eb90000-6ec0e000 rwxp 00000000 00:00 0 
6ec0e000-6ec11000 ---p 00000000 00:00 0 
6ec11000-6ec8f000 rwxp 00000000 00:00 0 
6ec8f000-6ec92000 ---p 00000000 00:00 0 
6ec92000-6ece0000 rwxp 00000000 00:00 0 
6ece0000-6ee00000 r-xp 00326000 08:01 15604847   /usr/lib/locale/locale-archive
6ee00000-6f000000 r-xp 00000000 08:01 15604847   /usr/lib/locale/locale-archive
6f000000-6f0ff000 rwxp 00000000 00:00 0 
6f0ff000-6f100000 ---p 00000000 00:00 0 
6f100000-6f108000 r-xs 00000000 08:01 4987190    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6f108000-6f147000 r-xp 002e5000 08:01 15604847   /usr/lib/locale/locale-archive
6f147000-6f14a000 ---p 00000000 00:00 0 
6f14a000-6f198000 rwxp 00000000 00:00 0 
6f198000-6f19b000 ---p 00000000 00:00 0 
6f19b000-6f1e9000 rwxp 00000000 00:00 0 
6f1e9000-6f1ea000 ---p 00000000 00:00 0 
6f1ea000-6f29d000 rwxp 00000000 00:00 0 
6f29d000-6f435000 r-xs 03013000 08:01 16256719   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/rt.jar
6f435000-6f436000 ---p 00000000 00:00 0 
6f436000-6f4b6000 rwxp 00000000 00:00 0 
6f4b6000-6f4b7000 ---p 00000000 00:00 0 
6f4b7000-6f537000 rwxp 00000000 00:00 0 
6f537000-6f538000 ---p 00000000 00:00 0 
6f538000-6f5b8000 rwxp 00000000 00:00 0 
6f5b8000-6f5b9000 ---p 00000000 00:00 0 
6f5b9000-6f649000 rwxp 00000000 00:00 0 
6f649000-6f659000 rwxp 00000000 00:00 0 
6f659000-6f759000 rwxp 00000000 00:00 0 
6f759000-6f7af000 rwxp 00000000 00:00 0 
6f7af000-6f7bf000 rwxp 00000000 00:00 0 
6f7bf000-6f7cf000 rwxp 00000000 00:00 0 
6f7cf000-6f8cf000 rwxp 00000000 00:00 0 
6f8cf000-6f924000 rwxp 00000000 00:00 0 
6f924000-6f9a5000 rwxp 00000000 00:00 0 
6f9a5000-6f9cf000 rwxp 00000000 00:00 0 
6f9cf000-71950000 rwxp 00000000 00:00 0 
71950000-739d0000 rwxp 00000000 00:00 0 
739d0000-939d0000 rwxp 00000000 00:00 0 
939d0000-9e480000 rwxp 00000000 00:00 0 
9e480000-ae480000 rwxp 00000000 00:00 0 
ae480000-b39d0000 rwxp 00000000 00:00 0 
b39d0000-b39d4000 r-xs 00000000 08:01 4980799    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b39d4000-b39d7000 r-xs 00000000 08:01 4980804    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b39d7000-b39db000 r-xp 00000000 08:01 15600396   /usr/lib/libXdmcp.so.6.0.0
b39db000-b39dc000 r-xp 00003000 08:01 15600396   /usr/lib/libXdmcp.so.6.0.0
b39dc000-b39dd000 rwxp 00004000 08:01 15600396   /usr/lib/libXdmcp.so.6.0.0
b39dd000-b39e6000 rwxp 00000000 00:00 0 
b39e6000-b3a9d000 rwxp 00000000 00:00 0 
b3a9d000-b3cdd000 rwxp 00000000 00:00 0 
b3cdd000-b6a9d000 rwxp 00000000 00:00 0 
b6a9d000-b6aac000 r-xp 00000000 08:01 17304713   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libzip.so
b6aac000-b6aae000 rwxp 0000e000 08:01 17304713   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libzip.so
b6aae000-b6ab8000 r-xp 00000000 08:01 10092982   /lib/libnss_files-2.12.1.so
b6ab8000-b6ab9000 r-xp 00009000 08:01 10092982   /lib/libnss_files-2.12.1.so
b6ab9000-b6aba000 rwxp 0000a000 08:01 10092982   /lib/libnss_files-2.12.1.so
b6aba000-b6ac3000 r-xp 00000000 08:01 10092988   /lib/libnss_nis-2.12.1.so
b6ac3000-b6ac4000 r-xp 00008000 08:01 10092988   /lib/libnss_nis-2.12.1.so
b6ac4000-b6ac5000 rwxp 00009000 08:01 10092988   /lib/libnss_nis-2.12.1.so
b6ac5000-b6acb000 r-xp 00000000 08:01 10092994   /lib/libnss_compat-2.12.1.so
b6acb000-b6acc000 r-xp 00006000 08:01 10092994   /lib/libnss_compat-2.12.1.so
b6acc000-b6acd000 rwxp 00007000 08:01 10092994   /lib/libnss_compat-2.12.1.so
b6acd000-b6ad0000 r-xs 00000000 08:01 4988696    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b6ad0000-b6ad2000 r-xp 00000000 08:01 15600385   /usr/lib/libXau.so.6.0.0
b6ad2000-b6ad3000 r-xp 00001000 08:01 15600385   /usr/lib/libXau.so.6.0.0
b6ad3000-b6ad4000 rwxp 00002000 08:01 15600385   /usr/lib/libXau.so.6.0.0
b6ad4000-b6adc000 rwxs 00000000 08:01 15996075   /tmp/hsperfdata_otto/2059
b6adc000-b6aef000 r-xp 00000000 08:01 10092990   /lib/libnsl-2.12.1.so
b6aef000-b6af0000 r-xp 00012000 08:01 10092990   /lib/libnsl-2.12.1.so
b6af0000-b6af1000 rwxp 00013000 08:01 10092990   /lib/libnsl-2.12.1.so
b6af1000-b6af3000 rwxp 00000000 00:00 0 
b6af3000-b6af7000 r-xp 00000000 08:01 15600426   /usr/lib/libXtst.so.6.1.0
b6af7000-b6af8000 r-xp 00003000 08:01 15600426   /usr/lib/libXtst.so.6.1.0
b6af8000-b6af9000 rwxp 00004000 08:01 15600426   /usr/lib/libXtst.so.6.1.0
b6af9000-b6aff000 r-xp 00000000 08:01 17304698   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/native_threads/libhpi.so
b6aff000-b6b00000 rwxp 00006000 08:01 17304698   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/native_threads/libhpi.so
b6b00000-b6b01000 rwxp 00000000 00:00 0 
b6b01000-b6b02000 r-xp 00000000 00:00 0 
b6b02000-b6b25000 r-xp 00000000 08:01 17304710   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libjava.so
b6b25000-b6b27000 rwxp 00023000 08:01 17304710   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libjava.so
b6b27000-b6b2e000 r-xp 00000000 08:01 10092986   /lib/librt-2.12.1.so
b6b2e000-b6b2f000 r-xp 00006000 08:01 10092986   /lib/librt-2.12.1.so
b6b2f000-b6b30000 rwxp 00007000 08:01 10092986   /lib/librt-2.12.1.so
b6b30000-b6b33000 ---p 00000000 00:00 0 
b6b33000-b6b81000 rwxp 00000000 00:00 0 
b6b81000-b6ba5000 r-xp 00000000 08:01 10092993   /lib/libm-2.12.1.so
b6ba5000-b6ba6000 r-xp 00023000 08:01 10092993   /lib/libm-2.12.1.so
b6ba6000-b6ba7000 rwxp 00024000 08:01 10092993   /lib/libm-2.12.1.so
b6ba7000-b72d3000 r-xp 00000000 08:01 17304700   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/server/libjvm.so
b72d3000-b7326000 rwxp 0072c000 08:01 17304700   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/server/libjvm.so
b7326000-b7746000 rwxp 00000000 00:00 0 
b7746000-b789d000 r-xp 00000000 08:01 10092995   /lib/libc-2.12.1.so
b789d000-b789f000 r-xp 00157000 08:01 10092995   /lib/libc-2.12.1.so
b789f000-b78a0000 rwxp 00159000 08:01 10092995   /lib/libc-2.12.1.so
b78a0000-b78a3000 rwxp 00000000 00:00 0 
b78a3000-b78a5000 r-xp 00000000 08:01 10092984   /lib/libdl-2.12.1.so
b78a5000-b78a6000 r-xp 00001000 08:01 10092984   /lib/libdl-2.12.1.so
b78a6000-b78a7000 rwxp 00002000 08:01 10092984   /lib/libdl-2.12.1.so
b78a7000-b78ae000 r-xp 00000000 08:01 17304712   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/jli/libjli.so
b78ae000-b78b0000 rwxp 00006000 08:01 17304712   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/jli/libjli.so
b78b0000-b78b1000 rwxp 00000000 00:00 0 
b78b1000-b78c6000 r-xp 00000000 08:01 10092996   /lib/libpthread-2.12.1.so
b78c6000-b78c7000 ---p 00015000 08:01 10092996   /lib/libpthread-2.12.1.so
b78c7000-b78c8000 r-xp 00015000 08:01 10092996   /lib/libpthread-2.12.1.so
b78c8000-b78c9000 rwxp 00016000 08:01 10092996   /lib/libpthread-2.12.1.so
b78c9000-b78cb000 rwxp 00000000 00:00 0 
b78cb000-b78cc000 r-xs 00000000 08:01 4980788    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b78cc000-b78ce000 r-xs 0000b000 08:01 15861093   /home/otto/Desktop/Minecraft.jar
b78ce000-b78d9000 r-xp 00000000 08:01 17304709   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libverify.so
b78d9000-b78da000 rwxp 0000b000 08:01 17304709   /usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/libverify.so
b78da000-b78dc000 rwxp 00000000 00:00 0 
b78dc000-b78dd000 r-xp 00000000 00:00 0          [vdso]
b78dd000-b78f9000 r-xp 00000000 08:01 10092979   /lib/ld-2.12.1.so
b78f9000-b78fa000 r-xp 0001b000 08:01 10092979   /lib/ld-2.12.1.so
b78fa000-b78fb000 rwxp 0001c000 08:01 10092979   /lib/ld-2.12.1.so
bf883000-bf8a4000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms768M 
java_command: net.minecraft.LauncherFrame
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=otto
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.22/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.22/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6a9f20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6a9f20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5781e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x5781e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x5781e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5781e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x57ae20], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x57ab50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x57ab50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x57ab50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x57ab50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.35-24-generic-pae #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.57 0.57 0.41

CPU:total 4 (4 cores per cpu, 1 threads per core) family 16 model 5 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 4119816k(2577708k free), swap 11909116k(11909116k free)

vm_info: Java HotSpot(TM) Server VM (17.1-b03) for linux-x86 JRE (1.6.0_22-b04), built on Sep 15 2010 01:02:09 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Mon Dec 27 10:33:56 2010
elapsed time: 13 seconds

```PS: I installed Java, Minecraft did a Update, here is the code i use:

```
java -Xmx1024M -Xms768M -cp /home/otto/Desktop/Minecraft.jar net.minecraft.LauncherFrame
```Thanks RaverGames

---

### Post by Cousjava on 2010-12-27
Which Java and Minecraft are you using? Please could you say the full version number, and for Java exactly which packages you've got.

---

### Post by perfecti0n on 2011-01-24
I have the same problem :( any ideas?

I'm using 1.2.2 minecraft and i'm not sure how to check which packages i got... I just installed java runtime through software center.

---

### Post by proteusmoteus on 2011-01-24
Recommend using Sun's java to launch minecraft. Check to see if it is installed via "/usr/lib/jvm/java-6-sun/jre/bin/java -version"

If it isnt then enable the "partner" repository. Here is a [guide]("http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository") which shows how to do this either via the GUI or command line (dont do both as they accomplish the same thing).

Install sun's java via "sudo aptituide install sun-java6-jre"

Launch minecraft via "/usr/lib/jvm/java-6-sun/jre/bin/java -Xmx1024M -Xms512M -cp /whereever/you/downloaded/the/file/to/Minecraft.jar net.minecraft.LauncherFrame"

---

### Post by perfecti0n on 2011-01-25
Well that didn't work either, but thank you anyway.

After some googling I discovered that the problem are ATI drivers on Linux and apparently there's no fix for it.
There seems to be a conflict with lwjgl library and the FGLRX drivers...
(someone mentioned 3rd party drivers but I don't wanna mess with that since other stuff might stop working :D)

*Source: [http://www.minecraftforum.net/viewtopic.php?f=17&t=105618&view=unread]("http://www.minecraftforum.net/viewtopic.php?f=17&t=105618&view=unread")*

If anyone thinks of a solution please help? :)

---

### Post by perfecti0n on 2011-01-29
I'm using the latest (installed from software center). I have just recently replaced my OS with ubuntu so I probably have all the latest software...

---

