---
title: "Minecraft Quits after Loading World"
date: 2012-04-25
forum: Gaming &amp; Leisure
---

### Post by UnknownFearNG on 2012-04-25
Hello all. I recently installed proprietary drivers for my ATI video card on my Acer laptop and now, whenever I go to run Minecraft, it loads and then quits the game. I tried it twice; once using switches and the other just as is and it still quits. Here is the output from the Terminal:

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7735416, pid=3169, tid=1837316976
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# An error report file with more information is saved as:
# /home/djmillier/.minecraft/hs_err_pid3169.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted
```

For the Java version, I have both OpenJDK and Sun Java 6 installed as a few people recommend using Sun for gaming. I have Sun set as the default. Can anyone help me out with this?

Here is also the output of the hs_err_pid3169.log file it outputted:

```


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7735416, pid=3169, tid=1837316976
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x00000c61

Registers:
EAX=0x00000000, EBX=0x00000c61, ECX=0x00000c95, EDX=0x0000000b
ESP=0x6d83328c, EBP=0x6d833398, ESI=0x00000020, EDI=0xb771eff4
EIP=0xb7735416, EFLAGS=0x00200202, CR2=0xb7726000

Top of Stack: (sp=0x6d83328c)
0x6d83328c:   b7715e6e b771eff4 6b32d880 6ad0d743
0x6d83329c:   0000000b 00000000 00000000 00000000
0x6d8332ac:   00001000 00000000 00000000 00000000
0x6d8332bc:   00000000 00000000 7fffffff fffffffe
0x6d8332cc:   ffffffff ffffffff ffffffff ffffffff
0x6d8332dc:   ffffffff ffffffff ffffffff ffffffff
0x6d8332ec:   ffffffff ffffffff ffffffff ffffffff
0x6d8332fc:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb7735416)
0xb77353f6:   00 00 00 00 00 00 00 00 00 00 58 b8 77 00 00 00
0xb7735406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0xb7735416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73
0xb7735426:   68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 6e 73 74 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x00000c61 is an unknown value
ECX=0x00000c95 is an unknown value
EDX=0x0000000b is an unknown value
ESP=0x6d83328c is an unknown value
EBP=0x6d833398 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb771eff4: <offset 0x17ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb7707000


Stack: [0x6d823000,0x6d834000],  sp=0x6d83328c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [libpthread.so.0+0x6d31]  short+0xd1


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 152896K, used 1599K [0x9e230000, 0xa8cd0000, 0xb3780000)
  eden space 131072K, 1% used [0x9e230000,0x9e3bfd00,0xa6230000)
  from space 21824K, 0% used [0xa6230000,0xa6230000,0xa7780000)
  to   space 21824K, 0% used [0xa7780000,0xa7780000,0xa8cd0000)
 PSOldGen        total 349568K, used 30376K [0x73780000, 0x88ce0000, 0x9e230000)
  object space 349568K, 8% used [0x73780000,0x7552a108,0x88ce0000)
 PSPermGen       total 42880K, used 19157K [0x6f780000, 0x72160000, 0x73780000)
  object space 42880K, 44% used [0x6f780000,0x70a357c8,0x72160000)

Code Cache  [0xb384e000, 0xb3a8e000, 0xb684e000)
 total_blobs=749 nmethods=411 adapters=292 free_code_cache=49022592 largest_free_block=7936

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 18350548   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 18350548   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java
0995d000-0a524000 rwxp 00000000 00:00 0          [heap]
572ff000-57300000 ---p 00000000 00:00 0 
57300000-57500000 rwxp 00000000 00:00 0 
57500000-575e7000 rwxp 00000000 00:00 0 
575e7000-57600000 ---p 00000000 00:00 0 
5766b000-5766e000 ---p 00000000 00:00 0 
5766e000-616fc000 rwxp 00000000 00:00 0 
616fc000-616fd000 ---p 00000000 00:00 0 
616fd000-61efd000 rwxp 00000000 00:00 0 
61efd000-61efe000 ---p 00000000 00:00 0 
61efe000-626fe000 rwxp 00000000 00:00 0 
626fe000-666ff000 rwxs 00000000 00:12 22637      /run/shm/pulse-shm-2644309348
666ff000-66865000 r-xp 00000000 08:01 14682259   /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
66865000-66876000 r-xp 00165000 08:01 14682259   /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
66876000-66877000 rwxp 00176000 08:01 14682259   /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
66877000-668c3000 r-xp 00000000 08:01 14685251   /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
668c3000-668c4000 r-xp 0004b000 08:01 14685251   /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
668c4000-668c5000 rwxp 0004c000 08:01 14685251   /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
668c5000-66930000 r-xp 00000000 08:01 14685552   /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
66930000-66931000 r-xp 0006b000 08:01 14685552   /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
66931000-66932000 rwxp 0006c000 08:01 14685552   /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
66932000-66936000 rwxp 00000000 00:00 0 
66936000-66999000 r-xp 00000000 08:01 14682183   /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
66999000-6699a000 r-xp 00062000 08:01 14682183   /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
6699a000-6699b000 rwxp 00063000 08:01 14682183   /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
6699b000-669e7000 r-xp 00000000 08:01 14682181   /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
669e7000-669e8000 r-xp 0004b000 08:01 14682181   /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
669e8000-669e9000 rwxp 0004c000 08:01 14682181   /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
669e9000-66a0e000 r-xp 00000000 08:01 28574035   /home/djmillier/.minecraft/bin/natives/libopenal.so
66a0e000-66a0f000 rwxp 00025000 08:01 28574035   /home/djmillier/.minecraft/bin/natives/libopenal.so
66a0f000-66afc000 rwxp 00000000 00:00 0 
66afc000-66bfc000 rwxs 007f8000 00:05 8388       /dev/ati/card0
66bfc000-66dfc000 rwxs 007f7000 00:05 8388       /dev/ati/card0
66dfc000-68600000 rwxp 00000000 00:00 0 
68600000-68800000 rwxp 00000000 00:00 0 
68800000-688fe000 rwxp 00000000 00:00 0 
688fe000-68900000 ---p 00000000 00:00 0 
6890f000-689fb000 r-xp 00000000 08:01 14685332   /usr/lib/i386-linux-gnu/libasound.so.2.0.0
689fb000-689ff000 r-xp 000eb000 08:01 14685332   /usr/lib/i386-linux-gnu/libasound.so.2.0.0
689ff000-68a00000 rwxp 000ef000 08:01 14685332   /usr/lib/i386-linux-gnu/libasound.so.2.0.0
68a00000-68b00000 rwxp 00000000 00:00 0 
68b0d000-68b10000 ---p 00000000 00:00 0 
68b10000-68b5e000 rwxp 00000000 00:00 0 
68b5e000-68b61000 ---p 00000000 00:00 0 
68b61000-68baf000 rwxp 00000000 00:00 0 
68baf000-68bef000 rwxs 00012000 00:05 8388       /dev/ati/card0
68bef000-692ef000 rwxs 00006000 00:05 8388       /dev/ati/card0
692ef000-6936f000 rwxp 00000000 00:00 0 
6936f000-693a8000 r-xp 00000000 08:01 18351404   /usr/lib/fglrx/libatiadlxx.so
693a8000-693aa000 rwxp 00038000 08:01 18351404   /usr/lib/fglrx/libatiadlxx.so
693aa000-693ea000 rwxs f0400000 00:05 8388       /dev/ati/card0
693ea000-6b1a4000 r-xp 00000000 08:01 18351378   /usr/lib/fglrx/dri/fglrx_dri.so
6b1a4000-6b26f000 rwxp 01db9000 08:01 18351378   /usr/lib/fglrx/dri/fglrx_dri.so
6b26f000-6b32f000 rwxp 00000000 00:00 0 
6b32f000-6b3f8000 r-xp 00000000 08:01 18351380   /usr/lib/fglrx/libGL.so.1.2
6b3f8000-6b404000 rwxp 000c8000 08:01 18351380   /usr/lib/fglrx/libGL.so.1.2
6b404000-6b419000 rwxp 00000000 00:00 0 
6b419000-6b470000 r-xp 00000000 08:01 28574033   /home/djmillier/.minecraft/bin/natives/liblwjgl.so
6b470000-6b471000 r-xp 00056000 08:01 28574033   /home/djmillier/.minecraft/bin/natives/liblwjgl.so
6b471000-6b472000 rwxp 00057000 08:01 28574033   /home/djmillier/.minecraft/bin/natives/liblwjgl.so
6b472000-6b603000 rwxs 00000000 00:04 4849670    /SYSV00000000 (deleted)
6b603000-6b794000 rwxs 00000000 00:04 3473410    /SYSV00000000 (deleted)
6b794000-6ba00000 rwxp 00000000 00:00 0 
6ba00000-6bacc000 rwxp 00000000 00:00 0 
6bacc000-6bb00000 ---p 00000000 00:00 0 
6bb18000-6bb1d000 r-xp 00000000 08:01 14685334   /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
6bb1d000-6bb1e000 r-xp 00004000 08:01 14685334   /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
6bb1e000-6bb1f000 rwxp 00005000 08:01 14685334   /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
6bb1f000-6bb27000 r-xp 00000000 08:01 9962486    /lib/i386-linux-gnu/libwrap.so.0.7.6
6bb27000-6bb28000 r-xp 00007000 08:01 9962486    /lib/i386-linux-gnu/libwrap.so.0.7.6
6bb28000-6bb29000 rwxp 00008000 08:01 9962486    /lib/i386-linux-gnu/libwrap.so.0.7.6
6bb29000-6bb2f000 r-xp 00000000 08:01 14685457   /usr/lib/i386-linux-gnu/libjson.so.0.0.1
6bb2f000-6bb30000 r-xp 00005000 08:01 14685457   /usr/lib/i386-linux-gnu/libjson.so.0.0.1
6bb30000-6bb31000 rwxp 00006000 08:01 14685457   /usr/lib/i386-linux-gnu/libjson.so.0.0.1
6bb31000-6bb4d000 r-xp 00000000 08:01 9962426    /lib/i386-linux-gnu/libgcc_s.so.1
6bb4d000-6bb4e000 r-xp 0001b000 08:01 9962426    /lib/i386-linux-gnu/libgcc_s.so.1
6bb4e000-6bb4f000 rwxp 0001c000 08:01 9962426    /lib/i386-linux-gnu/libgcc_s.so.1
6bb4f000-6bb52000 ---p 00000000 00:00 0 
6bb52000-6bba0000 rwxp 00000000 00:00 0 
6bba0000-6bc00000 rwxs 00000000 00:04 3342339    /SYSV00000000 (deleted)
6bc00000-6bcec000 rwxp 00000000 00:00 0 
6bcec000-6bd00000 ---p 00000000 00:00 0 
6bd01000-6bd08000 r-xp 00000000 08:01 18351376   /usr/lib/fglrx/libatiuki.so.1.0
6bd08000-6bd09000 rwxp 00006000 08:01 18351376   /usr/lib/fglrx/libatiuki.so.1.0
6bd13000-6bd18000 r-xp 00000000 08:01 14682373   /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
6bd18000-6bd19000 r-xp 00004000 08:01 14682373   /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
6bd19000-6bd1a000 rwxp 00005000 08:01 14682373   /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
6bd1a000-6bd31000 r-xs 003c2000 08:01 28574028   /home/djmillier/.minecraft/bin/minecraft.jar
6bd31000-6bd96000 rwxs 00000000 00:04 4816900    /SYSV00000000 (deleted)
6bd9c000-6bd9f000 r-xp 00000000 08:01 28574031   /home/djmillier/.minecraft/bin/natives/libjinput-linux.so
6bd9f000-6bda0000 r-xp 00002000 08:01 28574031   /home/djmillier/.minecraft/bin/natives/libjinput-linux.so
6bda0000-6bda1000 rwxp 00003000 08:01 28574031   /home/djmillier/.minecraft/bin/natives/libjinput-linux.so
6bda1000-6bda6000 r-xs 00033000 08:01 28574026   /home/djmillier/.minecraft/bin/jinput.jar
6bda6000-6bdaf000 r-xs 000ac000 08:01 28574025   /home/djmillier/.minecraft/bin/lwjgl.jar
6bdaf000-6bdb2000 ---p 00000000 00:00 0 
6bdb2000-6be00000 rwxp 00000000 00:00 0 
6be00000-6bef9000 rwxp 00000000 00:00 0 
6bef9000-6bf00000 ---p 00000000 00:00 0 
6bf02000-6bf05000 ---p 00000000 00:00 0 
6bf05000-6bf53000 rwxp 00000000 00:00 0 
6bf53000-6bf56000 ---p 00000000 00:00 0 
6bf56000-6bfa4000 rwxp 00000000 00:00 0 
6bfa4000-6bfa9000 r-xp 00000000 08:01 9961629    /lib/i386-linux-gnu/libnss_dns-2.13.so
6bfa9000-6bfaa000 r-xp 00004000 08:01 9961629    /lib/i386-linux-gnu/libnss_dns-2.13.so
6bfaa000-6bfab000 rwxp 00005000 08:01 9961629    /lib/i386-linux-gnu/libnss_dns-2.13.so
6bfab000-6bfad000 r-xp 00000000 08:01 9961538    /lib/libnss_mdns4_minimal.so.2
6bfad000-6bfae000 r-xp 00001000 08:01 9961538    /lib/libnss_mdns4_minimal.so.2
6bfae000-6bfaf000 rwxp 00002000 08:01 9961538    /lib/libnss_mdns4_minimal.so.2
6bfaf000-6bfb2000 ---p 00000000 00:00 0 
6bfb2000-6c000000 rwxp 00000000 00:00 0 
6c000000-6c0fe000 rwxp 00000000 00:00 0 
6c0fe000-6c100000 ---p 00000000 00:00 0 
6c100000-6c103000 ---p 00000000 00:00 0 
6c103000-6c151000 rwxp 00000000 00:00 0 
6c151000-6c154000 ---p 00000000 00:00 0 
6c154000-6c1a2000 rwxp 00000000 00:00 0 
6c1a2000-6c1a3000 ---p 00000000 00:00 0 
6c1a3000-6c9a3000 rwxp 00000000 00:00 0 
6c9a3000-6c9a4000 ---p 00000000 00:00 0 
6c9a4000-6d1a4000 rwxp 00000000 00:00 0 
6d1a4000-6d1bc000 r-xp 00000000 08:01 14682955   /usr/lib/libdbusmenu-glib.so.4.0.5
6d1bc000-6d1bd000 r-xp 00017000 08:01 14682955   /usr/lib/libdbusmenu-glib.so.4.0.5
6d1bd000-6d1be000 rwxp 00018000 08:01 14682955   /usr/lib/libdbusmenu-glib.so.4.0.5
6d1be000-6d1ce000 r-xp 00000000 08:01 14682957   /usr/lib/libdbusmenu-gtk.so.4.0.5
6d1ce000-6d1cf000 ---p 00010000 08:01 14682957   /usr/lib/libdbusmenu-gtk.so.4.0.5
6d1cf000-6d1d0000 r-xp 00010000 08:01 14682957   /usr/lib/libdbusmenu-gtk.so.4.0.5
6d1d0000-6d1d1000 rwxp 00011000 08:01 14682957   /usr/lib/libdbusmenu-gtk.so.4.0.5
6d1d2000-6d1d4000 rwxs 00002000 00:05 8388       /dev/ati/card0
6d1d4000-6d1d8000 r-xs 000cb000 08:01 15728647   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/localedata.jar
6d1d8000-6d1db000 r-xs 00027000 08:01 15728646   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/sunjce_provider.jar
6d1db000-6d1e2000 r-xs 00094000 08:01 15732378   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/jsse.jar
6d1e2000-6d1f2000 r-xp 00000000 08:01 9961494    /lib/i386-linux-gnu/libudev.so.0.12.0
6d1f2000-6d1f3000 r-xp 0000f000 08:01 9961494    /lib/i386-linux-gnu/libudev.so.0.12.0
6d1f3000-6d1f4000 rwxp 00010000 08:01 9961494    /lib/i386-linux-gnu/libudev.so.0.12.0
6d1f4000-6d23b000 r-xp 00000000 08:01 9962415    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
6d23b000-6d23c000 r-xp 00046000 08:01 9962415    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
6d23c000-6d23d000 rwxp 00047000 08:01 9962415    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
6d23d000-6d252000 r-xp 00000000 08:01 14685216   /usr/lib/gvfs/libgvfscommon.so
6d252000-6d253000 r-xp 00015000 08:01 14685216   /usr/lib/gvfs/libgvfscommon.so
6d253000-6d254000 rwxp 00016000 08:01 14685216   /usr/lib/gvfs/libgvfscommon.so
6d254000-6d27e000 r-xp 00000000 08:01 14684661   /usr/lib/gio/modules/libgvfsdbus.so
6d27e000-6d27f000 r-xp 00029000 08:01 14684661   /usr/lib/gio/modules/libgvfsdbus.so
6d27f000-6d280000 rwxp 0002a000 08:01 14684661   /usr/lib/gio/modules/libgvfsdbus.so
6d280000-6d2bf000 r-xp 00000000 08:01 14683227   /usr/lib/libibus-1.0.so.0.0.0
6d2bf000-6d2c0000 r-xp 0003f000 08:01 14683227   /usr/lib/libibus-1.0.so.0.0.0
6d2c0000-6d2c1000 rwxp 00040000 08:01 14683227   /usr/lib/libibus-1.0.so.0.0.0
6d2c1000-6d2c4000 r-xs 00013000 08:01 15728653   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/jce.jar
6d2c4000-6d2cc000 r-xs 00115000 08:01 15733082   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/resources.jar
6d2cc000-6d2d0000 r-xp 00000000 08:01 14685153   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6d2d0000-6d2d1000 r-xp 00004000 08:01 14685153   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6d2d1000-6d2d2000 rwxp 00005000 08:01 14685153   /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
6d2d2000-6d2d7000 r-xp 00000000 08:01 14685934   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
6d2d7000-6d2d8000 ---p 00005000 08:01 14685934   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
6d2d8000-6d2d9000 r-xp 00005000 08:01 14685934   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
6d2d9000-6d2da000 rwxp 00006000 08:01 14685934   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
6d2da000-6d32c000 r-xp 00000000 08:01 15729787   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
6d32c000-6d383000 r-xp 00000000 08:01 15729834   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
6d383000-6d385000 r-xp 00000000 08:01 14684136   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6d385000-6d386000 r-xp 00001000 08:01 14684136   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6d386000-6d387000 rwxp 00002000 08:01 14684136   /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
6d387000-6d388000 r-xs 00000000 08:01 8126544    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6d388000-6d38e000 r-xs 00000000 08:01 8126541    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6d38e000-6d390000 r-xs 00000000 08:01 8126542    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6d390000-6d393000 r-xs 00000000 08:01 8126552    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6d393000-6d396000 r-xs 00000000 08:01 8126529    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6d396000-6d397000 r-xs 00000000 08:01 8126553    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6d397000-6d39b000 r-xs 00000000 08:01 8126538    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6d39b000-6d39c000 r-xs 00000000 08:01 8126533    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6d39c000-6d39d000 r-xs 00000000 08:01 8126526    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6d39d000-6d39e000 r-xs 00000000 08:01 8126536    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6d39e000-6d3a2000 r-xs 00000000 08:01 8126543    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6d3a2000-6d3a9000 r-xs 00000000 08:01 8134208    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6d3a9000-6d3b4000 r-xs 00000000 08:01 8126527    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6d3b4000-6d3d6000 r-xs 00000000 08:01 8134699    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6d3d6000-6d3e3000 r-xs 00000000 08:01 8126548    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6d3e3000-6d3f7000 r-xp 00000000 08:01 16389584   /usr/share/locale/en_CA/LC_MESSAGES/glib20.mo
6d500000-6d5fc000 rwxp 00000000 00:00 0 
6d5fc000-6d600000 ---p 00000000 00:00 0 
6d700000-6d7fd000 rwxp 00000000 00:00 0 
6d7fd000-6d800000 ---p 00000000 00:00 0 
6d800000-6d801000 r-xp 00000000 08:01 16393931   /usr/share/locale-langpack/en_CA/LC_MESSAGES/pulseaudio.mo
6d801000-6d809000 r-xs 00000000 08:01 8126967    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6d823000-6d824000 ---p 00000000 00:00 0 
6d824000-6d834000 rwxp 00000000 00:00 0 
6d834000-6d848000 r-xp 00000000 08:01 15732660   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnet.so
6d848000-6d849000 rwxp 00013000 08:01 15732660   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnet.so
6d849000-6d876000 r-xp 00000000 08:01 14685150   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d876000-6d877000 r-xp 0002c000 08:01 14685150   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d877000-6d878000 rwxp 0002d000 08:01 14685150   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
6d878000-6d87e000 r-xp 00000000 08:01 14685500   /usr/lib/i386-linux-gnu/libogg.so.0.7.1
6d87e000-6d87f000 r-xp 00005000 08:01 14685500   /usr/lib/i386-linux-gnu/libogg.so.0.7.1
6d87f000-6d880000 rwxp 00006000 08:01 14685500   /usr/lib/i386-linux-gnu/libogg.so.0.7.1
6d880000-6d8a9000 r-xp 00000000 08:01 14682261   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
6d8a9000-6d8aa000 r-xp 00028000 08:01 14682261   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
6d8aa000-6d8ab000 rwxp 00029000 08:01 14682261   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
6d8ab000-6d8b3000 r-xp 00000000 08:01 14683295   /usr/lib/libltdl.so.7.3.0
6d8b3000-6d8b4000 r-xp 00008000 08:01 14683295   /usr/lib/libltdl.so.7.3.0
6d8b4000-6d8b5000 rwxp 00009000 08:01 14683295   /usr/lib/libltdl.so.7.3.0
6d8b5000-6d8c6000 r-xp 00000000 08:01 14685569   /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
6d8c6000-6d8c7000 r-xp 00010000 08:01 14685569   /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
6d8c7000-6d8c8000 rwxp 00011000 08:01 14685569   /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
6d8c8000-6d8d0000 r-xp 00000000 08:01 14682257   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
6d8d0000-6d8d1000 r-xp 00007000 08:01 14682257   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
6d8d1000-6d8d2000 rwxp 00008000 08:01 14682257   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
6d8d2000-6d8e1000 r-xp 00000000 08:01 14680863   /usr/lib/libcanberra.so.0.2.5
6d8e1000-6d8e2000 r-xp 0000e000 08:01 14680863   /usr/lib/libcanberra.so.0.2.5
6d8e2000-6d8e3000 rwxp 0000f000 08:01 14680863   /usr/lib/libcanberra.so.0.2.5
6d8e3000-6d8e7000 r-xp 00000000 08:01 14680869   /usr/lib/libcanberra-gtk.so.0.1.8
6d8e7000-6d8e8000 r-xp 00003000 08:01 14680869   /usr/lib/libcanberra-gtk.so.0.1.8
6d8e8000-6d8e9000 rwxp 00004000 08:01 14680869   /usr/lib/libcanberra-gtk.so.0.1.8
6d8e9000-6d8ec000 r-xs 0001f000 08:01 28574027   /home/djmillier/.minecraft/bin/lwjgl_util.jar
6d8ec000-6d8ef000 r-xs 00000000 08:01 8126549    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6d8ef000-6d8f2000 r-xs 00000000 08:01 8134700    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6d8f2000-6d8f9000 r-xp 00000000 08:01 15732654   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnio.so
6d8f9000-6d8fa000 rwxp 00006000 08:01 15732654   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnio.so
6d8fa000-6d8ff000 r-xp 00000000 08:01 14683218   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6d8ff000-6d900000 r-xp 00004000 08:01 14683218   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6d900000-6d901000 rwxp 00005000 08:01 14683218   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
6d901000-6d922000 r-xp 00000000 08:01 16394420   /usr/share/locale/en_CA/LC_MESSAGES/gtk20-properties.mo
6d922000-6d930000 r-xp 00000000 08:01 14683387   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
6d930000-6d931000 r-xp 0000d000 08:01 14683387   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
6d931000-6d932000 rwxp 0000e000 08:01 14683387   /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
6d932000-6d939000 r-xs 00000000 08:01 14681692   /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
6d939000-6d976000 r-xp 00000000 08:01 9962462    /lib/i386-linux-gnu/libpcre.so.3.12.1
6d976000-6d977000 r-xp 0003c000 08:01 9962462    /lib/i386-linux-gnu/libpcre.so.3.12.1
6d977000-6d978000 rwxp 0003d000 08:01 9962462    /lib/i386-linux-gnu/libpcre.so.3.12.1
6d978000-6d97d000 r-xp 00000000 08:01 14685394   /usr/lib/i386-linux-gnu/libffi.so.6.0.0
6d97d000-6d97e000 r-xp 00004000 08:01 14685394   /usr/lib/i386-linux-gnu/libffi.so.6.0.0
6d97e000-6d97f000 rwxp 00005000 08:01 14685394   /usr/lib/i386-linux-gnu/libffi.so.6.0.0
6d97f000-6d9a5000 r-xp 00000000 08:01 9962421    /lib/i386-linux-gnu/libexpat.so.1.5.2
6d9a5000-6d9a6000 ---p 00026000 08:01 9962421    /lib/i386-linux-gnu/libexpat.so.1.5.2
6d9a6000-6d9a8000 r-xp 00026000 08:01 9962421    /lib/i386-linux-gnu/libexpat.so.1.5.2
6d9a8000-6d9a9000 rwxp 00028000 08:01 9962421    /lib/i386-linux-gnu/libexpat.so.1.5.2
6d9a9000-6d9bc000 r-xp 00000000 08:01 9962536    /lib/i386-linux-gnu/libresolv-2.13.so
6d9bc000-6d9bd000 r-xp 00012000 08:01 9962536    /lib/i386-linux-gnu/libresolv-2.13.so
6d9bd000-6d9be000 rwxp 00013000 08:01 9962536    /lib/i386-linux-gnu/libresolv-2.13.so
6d9be000-6d9c0000 rwxp 00000000 00:00 0 
6d9c0000-6d9dc000 r-xp 00000000 08:01 9962471    /lib/i386-linux-gnu/libselinux.so.1
6d9dc000-6d9dd000 r-xp 0001b000 08:01 9962471    /lib/i386-linux-gnu/libselinux.so.1
6d9dd000-6d9de000 rwxp 0001c000 08:01 9962471    /lib/i386-linux-gnu/libselinux.so.1
6d9de000-6d9f1000 r-xp 00000000 08:01 9962488    /lib/i386-linux-gnu/libz.so.1.2.3.4
6d9f1000-6d9f2000 r-xp 00012000 08:01 9962488    /lib/i386-linux-gnu/libz.so.1.2.3.4
6d9f2000-6d9f3000 rwxp 00013000 08:01 9962488    /lib/i386-linux-gnu/libz.so.1.2.3.4
6d9f3000-6d9fb000 r-xp 00000000 08:01 14685595   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6d9fb000-6d9fc000 r-xp 00008000 08:01 14685595   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6d9fc000-6d9fd000 rwxp 00009000 08:01 14685595   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
6d9fd000-6d9ff000 r-xp 00000000 08:01 14685589   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6d9ff000-6da00000 r-xp 00001000 08:01 14685589   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6da00000-6da01000 rwxp 00002000 08:01 14685589   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
6da01000-6da29000 r-xp 00000000 08:01 9961506    /lib/i386-linux-gnu/libpng12.so.0.46.0
6da29000-6da2a000 r-xp 00027000 08:01 9961506    /lib/i386-linux-gnu/libpng12.so.0.46.0
6da2a000-6da2b000 rwxp 00028000 08:01 9961506    /lib/i386-linux-gnu/libpng12.so.0.46.0
6da2b000-6dac0000 r-xp 00000000 08:01 14686623   /usr/lib/i386-linux-gnu/libpixman-1.so.0.25.2
6dac0000-6dac4000 r-xp 00094000 08:01 14686623   /usr/lib/i386-linux-gnu/libpixman-1.so.0.25.2
6dac4000-6dac5000 rwxp 00098000 08:01 14686623   /usr/lib/i386-linux-gnu/libpixman-1.so.0.25.2
6dac5000-6db57000 r-xp 00000000 08:01 14682178   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6db57000-6db5b000 r-xp 00091000 08:01 14682178   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6db5b000-6db5c000 rwxp 00095000 08:01 14682178   /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
6db5c000-6db5e000 r-xp 00000000 08:01 14685306   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6db5e000-6db5f000 r-xp 00001000 08:01 14685306   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6db5f000-6db60000 rwxp 00002000 08:01 14685306   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
6db60000-6dc57000 r-xp 00000000 08:01 9961497    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.0
6dc57000-6dc58000 r-xp 000f6000 08:01 9961497    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.0
6dc58000-6dc59000 rwxp 000f7000 08:01 9961497    /lib/i386-linux-gnu/libglib-2.0.so.0.3200.0
6dc59000-6dca6000 r-xp 00000000 08:01 14680446   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.0
6dca6000-6dca7000 r-xp 0004c000 08:01 14680446   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.0
6dca7000-6dca8000 rwxp 0004d000 08:01 14680446   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3200.0
6dca8000-6dcda000 r-xp 00000000 08:01 14685401   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6dcda000-6dcdb000 ---p 00032000 08:01 14685401   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6dcdb000-6dcdc000 r-xp 00032000 08:01 14685401   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6dcdc000-6dcdd000 rwxp 00033000 08:01 14685401   /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
6dcdd000-6dd24000 r-xp 00000000 08:01 14684086   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
6dd24000-6dd25000 ---p 00047000 08:01 14684086   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
6dd25000-6dd26000 r-xp 00047000 08:01 14684086   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
6dd26000-6dd27000 rwxp 00048000 08:01 14684086   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3000.0
6dd27000-6de7a000 r-xp 00000000 08:01 14683882   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.0
6de7a000-6de7c000 r-xp 00153000 08:01 14683882   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.0
6de7c000-6de7d000 rwxp 00155000 08:01 14683882   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3200.0
6de7d000-6de7e000 rwxp 00000000 00:00 0 
6de7e000-6df84000 r-xp 00000000 08:01 14685593   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.1
6df84000-6df86000 r-xp 00105000 08:01 14685593   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.1
6df86000-6df87000 rwxp 00107000 08:01 14685593   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.1
6df87000-6df88000 rwxp 00000000 00:00 0 
6df88000-6e033000 r-xp 00000000 08:01 14685420   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
6e033000-6e034000 ---p 000ab000 08:01 14685420   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
6e034000-6e036000 r-xp 000ab000 08:01 14685420   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
6e036000-6e037000 rwxp 000ad000 08:01 14685420   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.10
6e037000-6e497000 r-xp 00000000 08:01 14684755   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
6e497000-6e49b000 r-xp 00460000 08:01 14684755   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
6e49b000-6e49d000 rwxp 00464000 08:01 14684755   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.10
6e49d000-6e49f000 rwxp 00000000 00:00 0 
6e49f000-6e4a0000 r-xs 00000000 08:01 8126544    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6e4a0000-6e4a6000 r-xs 00000000 08:01 8126541    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6e4a6000-6e4a8000 r-xs 00000000 08:01 8126542    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6e4a8000-6e4ab000 r-xs 00000000 08:01 8126552    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6e4ab000-6e4ae000 r-xs 00000000 08:01 8126529    /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6e4ae000-6e4af000 r-xs 00000000 08:01 8126553    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6e4af000-6e4b3000 r-xs 00000000 08:01 8126538    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6e4b3000-6e4b4000 r-xs 00000000 08:01 8126533    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6e4b4000-6e4b5000 r-xs 00000000 08:01 8126526    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6e4b5000-6e4b6000 r-xs 00000000 08:01 8126536    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6e4b6000-6e4ba000 r-xs 00000000 08:01 8126543    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6e4ba000-6e4c1000 r-xs 00000000 08:01 8134208    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6e4c1000-6e4cc000 r-xs 00000000 08:01 8126527    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6e4cc000-6e4ee000 r-xs 00000000 08:01 8134699    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6e4ee000-6e4fb000 r-xs 00000000 08:01 8126548    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6e4fb000-6e4fc000 r-xp 00000000 08:01 14680451   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.0
6e4fc000-6e4fd000 r-xp 00000000 08:01 14680451   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.0
6e4fd000-6e4fe000 rwxp 00001000 08:01 14680451   /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3200.0
6e4fe000-6e528000 r-xp 00000000 08:01 14683923   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
6e528000-6e529000 r-xp 00029000 08:01 14683923   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
6e529000-6e52a000 rwxp 0002a000 08:01 14683923   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3000.0
6e52a000-6e548000 r-xp 00000000 08:01 14685414   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
6e548000-6e549000 r-xp 0001d000 08:01 14685414   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
6e549000-6e54a000 rwxp 0001e000 08:01 14685414   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
6e54a000-6e567000 r-xp 00000000 08:01 14685336   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
6e567000-6e569000 r-xp 0001c000 08:01 14685336   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
6e569000-6e56a000 rwxp 0001e000 08:01 14685336   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
6e56a000-6e56d000 ---p 00000000 00:00 0 
6e56d000-6e5bb000 rwxp 00000000 00:00 0 
6e5bb000-6e5c4000 r-xp 00000000 08:01 14685322   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6e5c4000-6e5c5000 r-xp 00008000 08:01 14685322   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6e5c5000-6e5c6000 rwxp 00009000 08:01 14685322   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
6e5c6000-6e5cf000 r-xp 00000000 08:01 14685304   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6e5cf000-6e5d0000 r-xp 00008000 08:01 14685304   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6e5d0000-6e5d1000 rwxp 00009000 08:01 14685304   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
6e5d1000-6e5d2000 rwxs 00005000 00:05 8388       /dev/ati/card0
6e5d2000-6e5d4000 r-xp 00000000 08:01 14685302   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6e5d4000-6e5d5000 r-xp 00001000 08:01 14685302   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6e5d5000-6e5d6000 rwxp 00002000 08:01 14685302   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
6e5d6000-6e5dd000 r-xp 00000000 08:01 14685320   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6e5dd000-6e5de000 r-xp 00006000 08:01 14685320   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6e5de000-6e5df000 rwxp 00007000 08:01 14685320   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
6e5df000-6e5e1000 r-xp 00000000 08:01 14685318   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6e5e1000-6e5e2000 r-xp 00001000 08:01 14685318   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6e5e2000-6e5e3000 rwxp 00002000 08:01 14685318   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
6e5e3000-6e5e6000 r-xp 00000000 08:01 14680427   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.0
6e5e6000-6e5e7000 r-xp 00002000 08:01 14680427   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.0
6e5e7000-6e5e8000 rwxp 00003000 08:01 14680427   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3200.0
6e5e8000-6e5f3000 r-xp 00000000 08:01 14684710   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
6e5f3000-6e5f4000 r-xp 0000a000 08:01 14684710   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
6e5f4000-6e5f5000 rwxp 0000b000 08:01 14684710   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3000.0
6e5f5000-6e5f6000 r-xp 00000000 08:01 15732652   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjawt.so
6e5f6000-6e5f7000 rwxp 00000000 08:01 15732652   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjawt.so
6e5f7000-6e5fa000 r-xp 00000000 08:01 16388354   /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
6e5fa000-6e606000 r-xp 00000000 08:01 16394419   /usr/share/locale/en_CA/LC_MESSAGES/gtk20.mo
6e606000-6e609000 ---p 00000000 00:00 0 
6e609000-6e657000 rwxp 00000000 00:00 0 
6e657000-6e6d0000 r-xp 00000000 08:01 15732670   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libfontmanager.so
6e6d0000-6e6da000 rwxp 00078000 08:01 15732670   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libfontmanager.so
6e6da000-6e6df000 rwxp 00000000 00:00 0 
6e6df000-6e6fe000 r-xp 00000000 08:01 14685519   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6e6fe000-6e6ff000 r-xp 0001e000 08:01 14685519   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6e6ff000-6e700000 rwxp 0001f000 08:01 14685519   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
6e700000-6e831000 r-xp 00000000 08:01 14685298   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6e831000-6e832000 ---p 00131000 08:01 14685298   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6e832000-6e833000 r-xp 00131000 08:01 14685298   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6e833000-6e835000 rwxp 00132000 08:01 14685298   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
6e835000-6e836000 rwxp 00000000 00:00 0 
6e836000-6e879000 r-xp 00000000 08:01 18350438   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/xawt/libmawt.so
6e879000-6e87b000 rwxp 00043000 08:01 18350438   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/xawt/libmawt.so
6e87b000-6e87c000 rwxp 00000000 00:00 0 
6e87c000-6e901000 r-xp 00000000 08:01 15732686   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libawt.so
6e901000-6e908000 rwxp 00085000 08:01 15732686   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libawt.so
6e908000-6e92c000 rwxp 00000000 00:00 0 
6e92c000-6e92d000 ---p 00000000 00:00 0 
6e92d000-6e9ad000 rwxp 00000000 00:00 0 
6e9ad000-6e9b0000 ---p 00000000 00:00 0 
6e9b0000-6e9fe000 rwxp 00000000 00:00 0 
6e9fe000-6ea01000 ---p 00000000 00:00 0 
6ea01000-6ea7f000 rwxp 00000000 00:00 0 
6ea7f000-6ea82000 ---p 00000000 00:00 0 
6ea82000-6eb00000 rwxp 00000000 00:00 0 
6eb00000-6ebff000 rwxp 00000000 00:00 0 
6ebff000-6ec00000 ---p 00000000 00:00 0 
6ec00000-6ec01000 r-xp 00000000 08:01 16388428   /usr/share/locale-langpack/en_CA/LC_MESSAGES/gdk-pixbuf.mo
6ec01000-6ec0f000 r-xp 00000000 08:01 14685316   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6ec0f000-6ec10000 r-xp 0000d000 08:01 14685316   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6ec10000-6ec11000 rwxp 0000e000 08:01 14685316   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
6ec11000-6ec22000 r-xp 00000000 08:01 14685310   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6ec22000-6ec23000 r-xp 00010000 08:01 14685310   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6ec23000-6ec24000 rwxp 00011000 08:01 14685310   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
6ec24000-6ec28000 r-xp 00000000 08:01 14685312   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6ec28000-6ec29000 r-xp 00003000 08:01 14685312   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6ec29000-6ec2a000 rwxp 00004000 08:01 14685312   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
6ec2a000-6ec32000 r-xs 00000000 08:01 8126967    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6ec32000-6ec35000 r-xs 00000000 08:01 8134700    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6ec35000-6ec38000 ---p 00000000 00:00 0 
6ec38000-6ec86000 rwxp 00000000 00:00 0 
6ec86000-6edb8000 r-xp 002ff000 08:01 14686938   /usr/lib/locale/locale-archive
6edb8000-6edf8000 r-xp 002bd000 08:01 14686938   /usr/lib/locale/locale-archive
6edf8000-6eff8000 r-xp 00000000 08:01 14686938   /usr/lib/locale/locale-archive
6eff8000-6effb000 ---p 00000000 00:00 0 
6effb000-6f049000 rwxp 00000000 00:00 0 
6f049000-6f04c000 ---p 00000000 00:00 0 
6f04c000-6f09a000 rwxp 00000000 00:00 0 
6f09a000-6f09b000 ---p 00000000 00:00 0 
6f09b000-6f14f000 rwxp 00000000 00:00 0 
6f14f000-6f2e7000 r-xs 03029000 08:01 15733170   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/rt.jar
6f2e7000-6f2e8000 ---p 00000000 00:00 0 
6f2e8000-6f368000 rwxp 00000000 00:00 0 
6f368000-6f369000 ---p 00000000 00:00 0 
6f369000-6f3fe000 rwxp 00000000 00:00 0 
6f3fe000-6f409000 rwxp 00000000 00:00 0 
6f409000-6f4b4000 rwxp 00000000 00:00 0 
6f4b4000-6f55f000 rwxp 00000000 00:00 0 
6f55f000-6f574000 rwxp 00000000 00:00 0 
6f574000-6f57f000 rwxp 00000000 00:00 0 
6f57f000-6f62a000 rwxp 00000000 00:00 0 
6f62a000-6f6d4000 rwxp 00000000 00:00 0 
6f6d4000-6f72a000 rwxp 00000000 00:00 0 
6f72a000-6f77f000 rwxp 00000000 00:00 0 
6f77f000-72160000 rwxp 00000000 00:00 0 
72160000-73780000 rwxp 00000000 00:00 0 
73780000-88ce0000 rwxp 00000000 00:00 0 
88ce0000-9e230000 rwxp 00000000 00:00 0 
9e230000-a8cd0000 rwxp 00000000 00:00 0 
a8cd0000-b3780000 rwxp 00000000 00:00 0 
b3780000-b3783000 r-xs 00000000 08:01 8126549    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b3783000-b3788000 r-xp 00000000 08:01 14685308   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3788000-b3789000 r-xp 00004000 08:01 14685308   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3789000-b378a000 rwxp 00005000 08:01 14685308   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b378a000-b378c000 r-xp 00000000 08:01 14685300   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b378c000-b378d000 r-xp 00001000 08:01 14685300   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b378d000-b378e000 rwxp 00002000 08:01 14685300   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b378e000-b3797000 rwxp 00000000 00:00 0 
b3797000-b384e000 rwxp 00000000 00:00 0 
b384e000-b3a8e000 rwxp 00000000 00:00 0 
b3a8e000-b684e000 rwxp 00000000 00:00 0 
b684e000-b685d000 r-xp 00000000 08:01 15732668   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libzip.so
b685d000-b685f000 rwxp 0000e000 08:01 15732668   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libzip.so
b685f000-b686a000 r-xp 00000000 08:01 9961630    /lib/i386-linux-gnu/libnss_files-2.13.so
b686a000-b686b000 r-xp 0000a000 08:01 9961630    /lib/i386-linux-gnu/libnss_files-2.13.so
b686b000-b686c000 rwxp 0000b000 08:01 9961630    /lib/i386-linux-gnu/libnss_files-2.13.so
b686c000-b6876000 r-xp 00000000 08:01 9962477    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6876000-b6877000 r-xp 00009000 08:01 9962477    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6877000-b6878000 rwxp 0000a000 08:01 9962477    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6878000-b6880000 r-xp 00000000 08:01 9961628    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6880000-b6881000 r-xp 00007000 08:01 9961628    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6881000-b6882000 rwxp 00008000 08:01 9961628    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6882000-b6897000 r-xp 00000000 08:01 9961627    /lib/i386-linux-gnu/libnsl-2.13.so
b6897000-b6898000 r-xp 00015000 08:01 9961627    /lib/i386-linux-gnu/libnsl-2.13.so
b6898000-b6899000 rwxp 00016000 08:01 9961627    /lib/i386-linux-gnu/libnsl-2.13.so
b6899000-b689b000 rwxp 00000000 00:00 0 
b689b000-b689c000 r-xp 00000000 08:01 16388321   /usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo
b689c000-b689d000 r-xs 00000000 08:01 8132398    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b689d000-b68a2000 r-xp 00000000 08:01 14682860   /usr/lib/libXtst.so.6.1.0
b68a2000-b68a3000 r-xp 00004000 08:01 14682860   /usr/lib/libXtst.so.6.1.0
b68a3000-b68a4000 rwxp 00005000 08:01 14682860   /usr/lib/libXtst.so.6.1.0
b68a4000-b68ac000 rwxs 00000000 08:01 24117267   /tmp/hsperfdata_djmillier/3169
b68ac000-b68cf000 r-xp 00000000 08:01 15732640   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjava.so
b68cf000-b68d1000 rwxp 00023000 08:01 15732640   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjava.so
b68d1000-b68d8000 r-xp 00000000 08:01 9965422    /lib/i386-linux-gnu/librt-2.13.so
b68d8000-b68d9000 r-xp 00006000 08:01 9965422    /lib/i386-linux-gnu/librt-2.13.so
b68d9000-b68da000 rwxp 00007000 08:01 9965422    /lib/i386-linux-gnu/librt-2.13.so
b68da000-b68dd000 ---p 00000000 00:00 0 
b68dd000-b692b000 rwxp 00000000 00:00 0 
b692b000-b6953000 r-xp 00000000 08:01 9961625    /lib/i386-linux-gnu/libm-2.13.so
b6953000-b6954000 r-xp 00028000 08:01 9961625    /lib/i386-linux-gnu/libm-2.13.so
b6954000-b6955000 rwxp 00029000 08:01 9961625    /lib/i386-linux-gnu/libm-2.13.so
b6955000-b7107000 r-xp 00000000 08:01 18350435   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server/libjvm.so
b7107000-b715b000 rwxp 007b1000 08:01 18350435   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server/libjvm.so
b715b000-b757a000 rwxp 00000000 00:00 0 
b757a000-b76f2000 r-xp 00000000 08:01 9961621    /lib/i386-linux-gnu/libc-2.13.so
b76f2000-b76f4000 r-xp 00178000 08:01 9961621    /lib/i386-linux-gnu/libc-2.13.so
b76f4000-b76f5000 rwxp 0017a000 08:01 9961621    /lib/i386-linux-gnu/libc-2.13.so
b76f5000-b76f8000 rwxp 00000000 00:00 0 
b76f8000-b76fb000 r-xp 00000000 08:01 9961624    /lib/i386-linux-gnu/libdl-2.13.so
b76fb000-b76fc000 r-xp 00002000 08:01 9961624    /lib/i386-linux-gnu/libdl-2.13.so
b76fc000-b76fd000 rwxp 00003000 08:01 9961624    /lib/i386-linux-gnu/libdl-2.13.so
b76fd000-b7704000 r-xp 00000000 08:01 18350440   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/jli/libjli.so
b7704000-b7706000 rwxp 00006000 08:01 18350440   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/jli/libjli.so
b7706000-b7707000 rwxp 00000000 00:00 0 
b7707000-b771e000 r-xp 00000000 08:01 9962535    /lib/i386-linux-gnu/libpthread-2.13.so
b771e000-b771f000 r-xp 00016000 08:01 9962535    /lib/i386-linux-gnu/libpthread-2.13.so
b771f000-b7720000 rwxp 00017000 08:01 9962535    /lib/i386-linux-gnu/libpthread-2.13.so
b7720000-b7722000 rwxp 00000000 00:00 0 
b7722000-b7723000 r-xs 00000000 08:01 8132398    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b7723000-b7725000 r-xs 00016000 08:01 28574406   /home/djmillier/.minecraft/minecraft.jar
b7725000-b7726000 rwxp 00000000 00:00 0 
b7726000-b7727000 r-xp 00000000 00:00 0 
b7727000-b7732000 r-xp 00000000 08:01 15732673   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libverify.so
b7732000-b7733000 rwxp 0000b000 08:01 15732673   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libverify.so
b7733000-b7735000 rwxp 00000000 00:00 0 
b7735000-b7736000 r-xp 00000000 00:00 0          [vdso]
b7736000-b7754000 r-xp 00000000 08:01 9961618    /lib/i386-linux-gnu/ld-2.13.so
b7754000-b7755000 r-xp 0001d000 08:01 9961618    /lib/i386-linux-gnu/ld-2.13.so
b7755000-b7756000 rwxp 0001e000 08:01 9961618    /lib/i386-linux-gnu/ld-2.13.so
bfb38000-bfb59000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms512M 
java_command: net.minecraft.LauncherFrame
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=djmillier
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0

Signal Handlers:
SIGSEGV: [libjvm.so+0x725510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x725510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5e3160], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC 28107, NOFILE 4096, AS infinity
load average:1.05 1.02 0.61

/proc/meminfo:
MemTotal:        3611808 kB
MemFree:         1828856 kB
Buffers:           37304 kB
Cached:           646728 kB
SwapCached:            0 kB
Active:          1223196 kB
Inactive:         398860 kB
Active(anon):     938748 kB
Inactive(anon):     6004 kB
Active(file):     284448 kB
Inactive(file):   392856 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2755884 kB
HighFree:        1074320 kB
LowTotal:         855924 kB
LowFree:          754536 kB
SwapTotal:       3908604 kB
SwapFree:        3908604 kB
Dirty:               200 kB
Writeback:             0 kB
AnonPages:        937948 kB
Mapped:           158948 kB
Shmem:              6732 kB
Slab:              38148 kB
SReclaimable:      22512 kB
SUnreclaim:        15636 kB
KernelStack:        2968 kB
PageTables:         7200 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5714508 kB
Committed_AS:    3340868 kB
VmallocTotal:     122880 kB
VmallocUsed:       39268 kB
VmallocChunk:      78544 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 20 model 1 stepping 0, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, popcnt, mmxext, lzcnt, sse4a

/proc/cpuinfo:
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 20
model		: 1
model name	: AMD C-50 Processor
stepping	: 0
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter
bogomips	: 1995.16
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 20
model		: 1
model name	: AMD C-50 Processor
stepping	: 0
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter
bogomips	: 1994.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



Memory: 4k page, physical 3611808k(1828856k free), swap 3908604k(3908604k free)

vm_info: Java HotSpot(TM) Server VM (20.1-b02) for linux-x86 JRE (1.6.0_26-b03), built on May  4 2011 01:04:10 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Wed Apr 25 08:36:40 2012
elapsed time: 23 seconds

```

---

### Post by UnknownFearNG on 2012-04-25
Seemed to have fixed the issue by simply removing the ATi drivers and using the standard ones. Solved :)

---

