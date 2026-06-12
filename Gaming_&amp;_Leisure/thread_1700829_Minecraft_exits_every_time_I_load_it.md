---
title: "Minecraft exits every time I load it"
date: 2011-03-05
forum: Gaming &amp; Leisure
---

### Post by Arachan on 2011-03-05
Hello,

I've been playing Minecraft 1.3 Beta on Windows, and so I tried it on Linux.

I installed a bunch of java packages that other sites told me I needed, and tried to run the game. It loads fine, I select singleplayer, select my world, it loads my world, but then straight away the game exits. 

I'm at a bit of a loss about how to read this error, and I figured someone else could probably understand it better. Here is the error message:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x0089b416, pid=24131, tid=1789197168
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.7
# Distribution: Ubuntu 10.10, package 6b20-1.9.7-0ubuntu1
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x00005e43

Registers:
EAX=0x00000000, EBX=0x00005e43, ECX=0x00005ebf, EDX=0x0000000b
ESP=0x6aa4f288, EBP=0x6aa4f294, ESI=0x00000020, EDI=0x008f5ff4
EIP=0x0089b416, CR2=0x00000000, EFLAGS=0x00000202

Register to memory mapping:

EAX=0x00000000
0x00000000 is pointing to unknown location

EBX=0x00005e43
0x00005e43 is pointing to unknown location

ECX=0x00005ebf
0x00005ebf is pointing to unknown location

EDX=0x0000000b
0x0000000b is pointing to unknown location

ESP=0x6aa4f288
0x6aa4f288 is pointing to unknown location

EBP=0x6aa4f294
0x6aa4f294 is pointing to unknown location

ESI=0x00000020
0x00000020 is pointing to unknown location

EDI=0x008f5ff4
0x008f5ff4: <offset 0x16ff4> in /lib/libpthread.so.0 at 0x008df000


Top of Stack: (sp=0x6aa4f288)
0x6aa4f288:   008ed990 008f5ff4 070f6880 6aa4f398
0x6aa4f298:   06c128a3 0000000b 00000000 00000000
0x6aa4f2a8:   00000000 00001000 00000000 00000000
0x6aa4f2b8:   00000000 00000000 00000000 7fffffff
0x6aa4f2c8:   fffffffe ffffffff ffffffff ffffffff
0x6aa4f2d8:   ffffffff ffffffff ffffffff ffffffff
0x6aa4f2e8:   ffffffff ffffffff ffffffff ffffffff
0x6aa4f2f8:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0x0089b416)
0x0089b406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0x0089b416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73 

Stack: [0x6aa3f000,0x6aa50000],  sp=0x6aa4f288,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [fglrx_dri.so+0x167e8a3]
C  [libpthread.so.0+0x5cc9]


---------------  P R O C E S S  ---------------

VM state:synchronizing (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x08143eb0] Safepoint_lock - owner thread: 0x081cbc00
[0x08143f18] Threads_lock - owner thread: 0x081cbc00

Heap
 PSYoungGen      total 152896K, used 5639K [0x9f250000, 0xa9cf0000, 0xb47a0000)
  eden space 131072K, 4% used [0x9f250000,0x9f7d1f30,0xa7250000)
  from space 21824K, 0% used [0xa87a0000,0xa87a0000,0xa9cf0000)
  to   space 21824K, 0% used [0xa7250000,0xa7250000,0xa87a0000)
 PSOldGen        total 349568K, used 12251K [0x747a0000, 0x89d00000, 0x9f250000)
  object space 349568K, 3% used [0x747a0000,0x75396c80,0x89d00000)
 PSPermGen       total 39552K, used 17507K [0x6c7a0000, 0x6ee40000, 0x747a0000)
  object space 39552K, 44% used [0x6c7a0000,0x6d8b8c88,0x6ee40000)

Dynamic libraries:
00110000-00132000 r-xp 00000000 08:11 1442221    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00132000-00133000 r--p 00021000 08:11 1442221    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00133000-00135000 rw-p 00022000 08:11 1442221    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00135000-0013e000 r-xp 00000000 08:11 1308663    /lib/libnss_nis-2.12.1.so
0013e000-0013f000 r--p 00008000 08:11 1308663    /lib/libnss_nis-2.12.1.so
0013f000-00140000 rw-p 00009000 08:11 1308663    /lib/libnss_nis-2.12.1.so
00140000-0014a000 r-xp 00000000 08:11 1308661    /lib/libnss_files-2.12.1.so
0014a000-0014b000 r--p 00009000 08:11 1308661    /lib/libnss_files-2.12.1.so
0014b000-0014c000 rw-p 0000a000 08:11 1308661    /lib/libnss_files-2.12.1.so
0014c000-00152000 r-xp 00000000 08:11 1442226    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00152000-00153000 r--p 00005000 08:11 1442226    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00153000-00154000 rw-p 00006000 08:11 1442226    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00154000-001d6000 r-xp 00000000 08:11 1442224    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001d6000-001d7000 r--p 00081000 08:11 1442224    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001d7000-001dd000 rw-p 00082000 08:11 1442224    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
001dd000-00202000 rw-p 00000000 00:00 0 
00202000-0031b000 r-xp 00000000 08:11 1442798    /usr/lib/libX11.so.6.3.0
0031b000-0031c000 r--p 00118000 08:11 1442798    /usr/lib/libX11.so.6.3.0
0031c000-0031e000 rw-p 00119000 08:11 1442798    /usr/lib/libX11.so.6.3.0
0031e000-0031f000 rw-p 00000000 00:00 0 
0031f000-00323000 r-xp 00000000 08:11 1442843    /usr/lib/libXtst.so.6.1.0
00323000-00324000 r--p 00003000 08:11 1442843    /usr/lib/libXtst.so.6.1.0
00324000-00325000 rw-p 00004000 08:11 1442843    /usr/lib/libXtst.so.6.1.0
00325000-00331000 r-xp 00000000 08:11 1442823    /usr/lib/libXi.so.6.1.0
00331000-00332000 r--p 0000b000 08:11 1442823    /usr/lib/libXi.so.6.1.0
00332000-00333000 rw-p 0000c000 08:11 1442823    /usr/lib/libXi.so.6.1.0
00333000-0034b000 r-xp 00000000 08:11 1443764    /usr/lib/libxcb.so.1.1.0
0034b000-0034c000 r--p 00017000 08:11 1443764    /usr/lib/libxcb.so.1.1.0
0034c000-0034d000 rw-p 00018000 08:11 1443764    /usr/lib/libxcb.so.1.1.0
0034d000-0034f000 r-xp 00000000 08:11 1442802    /usr/lib/libXau.so.6.0.0
0034f000-00350000 r--p 00001000 08:11 1442802    /usr/lib/libXau.so.6.0.0
00350000-00351000 rw-p 00002000 08:11 1442802    /usr/lib/libXau.so.6.0.0
00351000-003c3000 r-xp 00000000 08:11 1444720    /usr/lib/libfreetype.so.6.6.0
003c3000-003c7000 r--p 00071000 08:11 1444720    /usr/lib/libfreetype.so.6.6.0
003c7000-003c8000 rw-p 00075000 08:11 1444720    /usr/lib/libfreetype.so.6.6.0
003c8000-003e2000 r-xp 00000000 08:11 1308240    /lib/libgcc_s.so.1
003e2000-003e3000 r--p 00019000 08:11 1308240    /lib/libgcc_s.so.1
003e3000-003e4000 rw-p 0001a000 08:11 1308240    /lib/libgcc_s.so.1
003e4000-003ec000 r-xp 00000000 08:11 1442809    /usr/lib/libXcursor.so.1.0.2
003ec000-003ed000 r--p 00007000 08:11 1442809    /usr/lib/libXcursor.so.1.0.2
003ed000-003ee000 rw-p 00008000 08:11 1442809    /usr/lib/libXcursor.so.1.0.2
003ee000-003f2000 r-xp 00000000 08:11 1442817    /usr/lib/libXfixes.so.3.1.0
003f2000-003f3000 r--p 00003000 08:11 1442817    /usr/lib/libXfixes.so.3.1.0
003f3000-003f4000 rw-p 00004000 08:11 1442817    /usr/lib/libXfixes.so.3.1.0
003f5000-0054c000 r-xp 00000000 08:11 1308652    /lib/libc-2.12.1.so
0054c000-0054e000 r--p 00157000 08:11 1308652    /lib/libc-2.12.1.so
0054e000-0054f000 rw-p 00159000 08:11 1308652    /lib/libc-2.12.1.so
0054f000-00552000 rw-p 00000000 00:00 0 
00552000-0056a000 r-xp 00000000 08:11 1442878    /usr/lib/libatk-1.0.so.0.3209.1
0056a000-0056b000 ---p 00018000 08:11 1442878    /usr/lib/libatk-1.0.so.0.3209.1
0056b000-0056c000 r--p 00018000 08:11 1442878    /usr/lib/libatk-1.0.so.0.3209.1
0056c000-0056d000 rw-p 00019000 08:11 1442878    /usr/lib/libatk-1.0.so.0.3209.1
0056d000-00591000 r-xp 00000000 08:11 1451709    /usr/lib/libpangoft2-1.0.so.0.2800.2
00591000-00592000 r--p 00023000 08:11 1451709    /usr/lib/libpangoft2-1.0.so.0.2800.2
00592000-00593000 rw-p 00024000 08:11 1451709    /usr/lib/libpangoft2-1.0.so.0.2800.2
00593000-0059d000 r-xp 00000000 08:11 1449045    /usr/lib/libpangocairo-1.0.so.0.2800.2
0059d000-0059e000 r--p 00009000 08:11 1449045    /usr/lib/libpangocairo-1.0.so.0.2800.2
0059e000-0059f000 rw-p 0000a000 08:11 1449045    /usr/lib/libpangocairo-1.0.so.0.2800.2
0059f000-005a2000 r-xp 00000000 08:11 1451704    /usr/lib/libgthread-2.0.so.0.2600.1
005a2000-005a3000 r--p 00003000 08:11 1451704    /usr/lib/libgthread-2.0.so.0.2600.1
005a3000-005a4000 rw-p 00004000 08:11 1451704    /usr/lib/libgthread-2.0.so.0.2600.1
005a4000-005a5000 r-xp 00000000 08:11 1442796    /usr/lib/libX11-xcb.so.1.0.0
005a5000-005a6000 r--p 00000000 08:11 1442796    /usr/lib/libX11-xcb.so.1.0.0
005a6000-005a7000 rw-p 00001000 08:11 1442796    /usr/lib/libX11-xcb.so.1.0.0
005a7000-005ad000 r-xp 00000000 08:11 1459862    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
005ad000-005ae000 r--p 00005000 08:11 1459862    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
005ae000-005af000 rw-p 00006000 08:11 1459862    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
005af000-00643000 r-xp 00000000 08:11 1443118    /usr/lib/libgdk-x11-2.0.so.0.2200.0
00643000-00645000 r--p 00094000 08:11 1443118    /usr/lib/libgdk-x11-2.0.so.0.2200.0
00645000-00646000 rw-p 00096000 08:11 1443118    /usr/lib/libgdk-x11-2.0.so.0.2200.0
00646000-00685000 r-xp 00000000 08:11 1446510    /usr/lib/libpango-1.0.so.0.2800.2
00685000-00686000 ---p 0003f000 08:11 1446510    /usr/lib/libpango-1.0.so.0.2800.2
00686000-00687000 r--p 0003f000 08:11 1446510    /usr/lib/libpango-1.0.so.0.2800.2
00687000-00688000 rw-p 00040000 08:11 1446510    /usr/lib/libpango-1.0.so.0.2800.2
00688000-006b6000 r-xp 00000000 08:11 1443077    /usr/lib/libfontconfig.so.1.4.4
006b6000-006b7000 r--p 0002d000 08:11 1443077    /usr/lib/libfontconfig.so.1.4.4
006b7000-006b8000 rw-p 0002e000 08:11 1443077    /usr/lib/libfontconfig.so.1.4.4
006b8000-006ba000 r-xp 00000000 08:11 1442825    /usr/lib/libXinerama.so.1.0.0
006ba000-006bb000 r--p 00001000 08:11 1442825    /usr/lib/libXinerama.so.1.0.0
006bb000-006bc000 rw-p 00002000 08:11 1442825    /usr/lib/libXinerama.so.1.0.0
006bc000-006be000 r-xp 00000000 08:11 1442807    /usr/lib/libXcomposite.so.1.0.0
006be000-006bf000 r--p 00001000 08:11 1442807    /usr/lib/libXcomposite.so.1.0.0
006bf000-006c0000 rw-p 00002000 08:11 1442807    /usr/lib/libXcomposite.so.1.0.0
006c2000-006cd000 r-xp 00000000 08:11 1459869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
006cd000-006ce000 ---p 0000b000 08:11 1459869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
006ce000-006cf000 r--p 0000b000 08:11 1459869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
006cf000-006d0000 rw-p 0000c000 08:11 1459869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
006d1000-006f5000 r-xp 00000000 08:11 1308656    /lib/libm-2.12.1.so
006f5000-006f6000 r--p 00023000 08:11 1308656    /lib/libm-2.12.1.so
006f6000-006f7000 rw-p 00024000 08:11 1308656    /lib/libm-2.12.1.so
006f7000-007a5000 r-xp 00000000 08:11 1453842    /usr/lib/libcairo.so.2.11000.0
007a5000-007a6000 ---p 000ae000 08:11 1453842    /usr/lib/libcairo.so.2.11000.0
007a6000-007a7000 r--p 000ae000 08:11 1453842    /usr/lib/libcairo.so.2.11000.0
007a7000-007a8000 rw-p 000af000 08:11 1453842    /usr/lib/libcairo.so.2.11000.0
007a8000-007aa000 rw-p 00000000 00:00 0 
007aa000-007b0000 r-xp 00000000 08:11 1442835    /usr/lib/libXrandr.so.2.2.0
007b0000-007b1000 r--p 00005000 08:11 1442835    /usr/lib/libXrandr.so.2.2.0
007b1000-007b2000 rw-p 00006000 08:11 1442835    /usr/lib/libXrandr.so.2.2.0
007b2000-007b4000 r-xp 00000000 08:11 1442811    /usr/lib/libXdamage.so.1.1.0
007b4000-007b5000 r--p 00001000 08:11 1442811    /usr/lib/libXdamage.so.1.1.0
007b5000-007b6000 rw-p 00002000 08:11 1442811    /usr/lib/libXdamage.so.1.1.0
007b6000-007f9000 r-xp 00000000 08:11 1442288    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
007f9000-007fa000 r--p 00042000 08:11 1442288    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
007fa000-007fc000 rw-p 00043000 08:11 1442288    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
007fc000-007fd000 rw-p 00000000 00:00 0 
007fd000-0083e000 r-xp 00000000 08:11 1451702    /usr/lib/libgobject-2.0.so.0.2600.1
0083e000-0083f000 r--p 00040000 08:11 1451702    /usr/lib/libgobject-2.0.so.0.2600.1
0083f000-00840000 rw-p 00041000 08:11 1451702    /usr/lib/libgobject-2.0.so.0.2600.1
00840000-00863000 r-xp 00000000 08:11 1308310    /lib/libpng12.so.0.44.0
00863000-00864000 r--p 00022000 08:11 1308310    /lib/libpng12.so.0.44.0
00864000-00865000 rw-p 00023000 08:11 1308310    /lib/libpng12.so.0.44.0
00865000-00875000 r-xp 00000000 08:11 1320050    /lib/libresolv-2.12.1.so
00875000-00876000 r--p 00010000 08:11 1320050    /lib/libresolv-2.12.1.so
00876000-00877000 rw-p 00011000 08:11 1320050    /lib/libresolv-2.12.1.so
00877000-00879000 rw-p 00000000 00:00 0 
00879000-00893000 r-xp 00000000 08:11 1308322    /lib/libselinux.so.1
00893000-00894000 r--p 00019000 08:11 1308322    /lib/libselinux.so.1
00894000-00895000 rw-p 0001a000 08:11 1308322    /lib/libselinux.so.1
00895000-00897000 r-xp 00000000 08:11 1308278    /lib/libnss_mdns4_minimal.so.2
00897000-00898000 r--p 00001000 08:11 1308278    /lib/libnss_mdns4_minimal.so.2
00898000-00899000 rw-p 00002000 08:11 1308278    /lib/libnss_mdns4_minimal.so.2
0089b000-0089c000 r-xp 00000000 00:00 0          [vdso]
0089c000-008a2000 r-xp 00000000 08:11 1443760    /usr/lib/libxcb-render.so.0.0.0
008a2000-008a3000 r--p 00005000 08:11 1443760    /usr/lib/libxcb-render.so.0.0.0
008a3000-008a4000 rw-p 00006000 08:11 1443760    /usr/lib/libxcb-render.so.0.0.0
008a4000-008ad000 r-xp 00000000 08:11 1459855    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
008ad000-008ae000 r--p 00008000 08:11 1459855    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
008ae000-008af000 rw-p 00009000 08:11 1459855    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
008b1000-008b9000 r-xp 00000000 08:11 1442837    /usr/lib/libXrender.so.1.3.0
008b9000-008ba000 r--p 00007000 08:11 1442837    /usr/lib/libXrender.so.1.3.0
008ba000-008bb000 rw-p 00008000 08:11 1442837    /usr/lib/libXrender.so.1.3.0
008bb000-008cf000 r-xp 00000000 08:11 1459877    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
008cf000-008d0000 r--p 00013000 08:11 1459877    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
008d0000-008d1000 rw-p 00014000 08:11 1459877    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
008d1000-008d8000 r-xp 00000000 08:11 1442225    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008d8000-008d9000 r--p 00006000 08:11 1442225    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008d9000-008da000 rw-p 00007000 08:11 1442225    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
008da000-008dd000 r-xp 00000000 08:15 405532     /home/arachan/.minecraft/bin/natives/libjinput-linux.so
008dd000-008de000 rw-p 00002000 08:15 405532     /home/arachan/.minecraft/bin/natives/libjinput-linux.so
008df000-008f4000 r-xp 00000000 08:11 1308669    /lib/libpthread-2.12.1.so
008f4000-008f5000 ---p 00015000 08:11 1308669    /lib/libpthread-2.12.1.so
008f5000-008f6000 r--p 00015000 08:11 1308669    /lib/libpthread-2.12.1.so
008f6000-008f7000 rw-p 00016000 08:11 1308669    /lib/libpthread-2.12.1.so
008f7000-008f9000 rw-p 00000000 00:00 0 
008f9000-009e1000 r-xp 00000000 08:11 1451705    /usr/lib/libgio-2.0.so.0.2600.1
009e1000-009e3000 r--p 000e7000 08:11 1451705    /usr/lib/libgio-2.0.so.0.2600.1
009e3000-009e4000 rw-p 000e9000 08:11 1451705    /usr/lib/libgio-2.0.so.0.2600.1
009e4000-009e5000 rw-p 00000000 00:00 0 
009e5000-00a09000 r-xp 00000000 08:11 1308233    /lib/libexpat.so.1.5.2
00a09000-00a0b000 r--p 00024000 08:11 1308233    /lib/libexpat.so.1.5.2
00a0b000-00a0c000 rw-p 00026000 08:11 1308233    /lib/libexpat.so.1.5.2
00a0c000-00a10000 r-xp 00000000 08:11 1308660    /lib/libnss_dns-2.12.1.so
00a10000-00a11000 r--p 00004000 08:11 1308660    /lib/libnss_dns-2.12.1.so
00a11000-00a12000 rw-p 00005000 08:11 1308660    /lib/libnss_dns-2.12.1.so
00a12000-00a15000 r-xp 00000000 08:11 1443752    /usr/lib/libxcb-atom.so.1.0.0
00a15000-00a16000 r--p 00002000 08:11 1443752    /usr/lib/libxcb-atom.so.1.0.0
00a16000-00a17000 rw-p 00003000 08:11 1443752    /usr/lib/libxcb-atom.so.1.0.0
00a1a000-00a1b000 r-xp 00000000 08:11 1442249    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00a1b000-00a1c000 r--p 00000000 08:11 1442249    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00a1c000-00a1d000 rw-p 00001000 08:11 1442249    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00a21000-00a34000 r-xp 00000000 08:11 1308658    /lib/libnsl-2.12.1.so
00a34000-00a35000 r--p 00012000 08:11 1308658    /lib/libnsl-2.12.1.so
00a35000-00a36000 rw-p 00013000 08:11 1308658    /lib/libnsl-2.12.1.so
00a36000-00a38000 rw-p 00000000 00:00 0 
00a38000-00a94000 r-xp 00000000 08:11 1443528    /usr/lib/libpixman-1.so.0.18.4
00a94000-00a97000 r--p 0005c000 08:11 1443528    /usr/lib/libpixman-1.so.0.18.4
00a97000-00a98000 rw-p 0005f000 08:11 1443528    /usr/lib/libpixman-1.so.0.18.4
00a98000-00aad000 r-xp 00000000 08:11 1442773    /usr/lib/libICE.so.6.3.0
00aad000-00aae000 r--p 00014000 08:11 1442773    /usr/lib/libICE.so.6.3.0
00aae000-00aaf000 rw-p 00015000 08:11 1442773    /usr/lib/libICE.so.6.3.0
00aaf000-00ab1000 rw-p 00000000 00:00 0 
00ab1000-00ab4000 r-xp 00000000 08:11 1323223    /lib/libuuid.so.1.3.0
00ab4000-00ab5000 r--p 00002000 08:11 1323223    /lib/libuuid.so.1.3.0
00ab5000-00ab6000 rw-p 00003000 08:11 1323223    /lib/libuuid.so.1.3.0
00ab9000-00aba000 r-xp 00000000 08:11 1456799    /usr/lib/jni/libjava-access-bridge-jni.so.0.0.0
00aba000-00abb000 r--p 00000000 08:11 1456799    /usr/lib/jni/libjava-access-bridge-jni.so.0.0.0
00abb000-00abc000 rw-p 00001000 08:11 1456799    /usr/lib/jni/libjava-access-bridge-jni.so.0.0.0
00abc000-00ae9000 r-xp 00000000 08:11 1459863    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
00ae9000-00aea000 r--p 0002c000 08:11 1459863    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
00aea000-00aeb000 rw-p 0002d000 08:11 1459863    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
00aeb000-00aed000 rw-p 00000000 00:00 0 
00aed000-00af4000 r-xp 00000000 08:11 1442794    /usr/lib/libSM.so.6.0.1
00af4000-00af5000 r--p 00006000 08:11 1442794    /usr/lib/libSM.so.6.0.1
00af5000-00af6000 rw-p 00007000 08:11 1442794    /usr/lib/libSM.so.6.0.1
00af6000-00afb000 r-xp 00000000 08:11 1443485    /usr/lib/libogg.so.0.7.0
00afb000-00afc000 r--p 00004000 08:11 1443485    /usr/lib/libogg.so.0.7.0
00afc000-00afd000 rw-p 00005000 08:11 1443485    /usr/lib/libogg.so.0.7.0
00afd000-00b01000 r-xp 00000000 08:11 1444091    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b01000-00b02000 r--p 00003000 08:11 1444091    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b02000-00b03000 rw-p 00004000 08:11 1444091    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
00b08000-00b0e000 r-xp 00000000 08:11 1308659    /lib/libnss_compat-2.12.1.so
00b0e000-00b0f000 r--p 00006000 08:11 1308659    /lib/libnss_compat-2.12.1.so
00b0f000-00b10000 rw-p 00007000 08:11 1308659    /lib/libnss_compat-2.12.1.so
00b10000-00b41000 r-xp 00000000 08:11 1450911    /usr/lib/fglrx/libatiadlxx.so
00b41000-00b42000 rw-p 00030000 08:11 1450911    /usr/lib/fglrx/libatiadlxx.so
00b42000-00b68000 r-xp 00000000 08:11 1443721    /usr/lib/libvorbis.so.0.4.4
00b68000-00b69000 r--p 00025000 08:11 1443721    /usr/lib/libvorbis.so.0.4.4
00b69000-00b6a000 rw-p 00026000 08:11 1443721    /usr/lib/libvorbis.so.0.4.4
00b73000-00b8a000 r-xp 00000000 08:11 1443120    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
00b8a000-00b8b000 r--p 00017000 08:11 1443120    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
00b8b000-00b8c000 rw-p 00018000 08:11 1443120    /usr/lib/libgdk_pixbuf-2.0.so.0.2200.0
00b99000-00b9c000 r-xp 00000000 08:11 1442253    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00b9c000-00b9d000 r--p 00002000 08:11 1442253    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00b9d000-00b9e000 rw-p 00003000 08:11 1442253    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00b9e000-00bac000 r-xp 00000000 08:11 1442815    /usr/lib/libXext.so.6.4.0
00bac000-00bad000 r--p 0000d000 08:11 1442815    /usr/lib/libXext.so.6.4.0
00bad000-00bae000 rw-p 0000e000 08:11 1442815    /usr/lib/libXext.so.6.4.0
00be1000-00be8000 r-xp 00000000 08:11 1320051    /lib/librt-2.12.1.so
00be8000-00be9000 r--p 00006000 08:11 1320051    /lib/librt-2.12.1.so
00be9000-00bea000 rw-p 00007000 08:11 1320051    /lib/librt-2.12.1.so
00bea000-00cb7000 r-xp 00000000 08:11 1308321    /lib/libglib-2.0.so.0.2600.1
00cb7000-00cb8000 r--p 000cc000 08:11 1308321    /lib/libglib-2.0.so.0.2600.1
00cb8000-00cb9000 rw-p 000cd000 08:11 1308321    /lib/libglib-2.0.so.0.2600.1
00cde000-00ce0000 r-xp 00000000 08:11 1443762    /usr/lib/libxcb-shm.so.0.0.0
00ce0000-00ce1000 r--p 00001000 08:11 1443762    /usr/lib/libxcb-shm.so.0.0.0
00ce1000-00ce2000 rw-p 00002000 08:11 1443762    /usr/lib/libxcb-shm.so.0.0.0
00ce2000-00d2a000 r-xp 00000000 08:11 1439380    /usr/lib/libpulsecommon-0.9.21.so
00d2a000-00d2b000 r--p 00047000 08:11 1439380    /usr/lib/libpulsecommon-0.9.21.so
00d2b000-00d2c000 rw-p 00048000 08:11 1439380    /usr/lib/libpulsecommon-0.9.21.so
00d33000-00d74000 r-xp 00000000 08:15 405534     /home/arachan/.minecraft/bin/natives/liblwjgl.so
00d74000-00d75000 rw-p 00041000 08:15 405534     /home/arachan/.minecraft/bin/natives/liblwjgl.so
00d75000-00daf000 r-xp 00000000 08:11 1308197    /lib/libdbus-1.so.3.5.2
00daf000-00db0000 r--p 00039000 08:11 1308197    /lib/libdbus-1.so.3.5.2
00db0000-00db1000 rw-p 0003a000 08:11 1308197    /lib/libdbus-1.so.3.5.2
00db8000-00dba000 r-xp 00000000 08:11 1451703    /usr/lib/libgmodule-2.0.so.0.2600.1
00dba000-00dbb000 r--p 00002000 08:11 1451703    /usr/lib/libgmodule-2.0.so.0.2600.1
00dbb000-00dbc000 rw-p 00003000 08:11 1451703    /usr/lib/libgmodule-2.0.so.0.2600.1
00dcb000-00e0f000 r-xp 00000000 08:11 1459879    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00e0f000-00e11000 r--p 00043000 08:11 1459879    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00e11000-00e12000 rw-p 00045000 08:11 1459879    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
00e12000-00e17000 rw-p 00000000 00:00 0 
00e24000-00e28000 r-xp 00000000 08:11 1442813    /usr/lib/libXdmcp.so.6.0.0
00e28000-00e29000 r--p 00003000 08:11 1442813    /usr/lib/libXdmcp.so.6.0.0
00e29000-00e2a000 rw-p 00004000 08:11 1442813    /usr/lib/libXdmcp.so.6.0.0
00e38000-00e3f000 r-xp 00000000 08:11 1450881    /usr/lib/fglrx/libatiuki.so.1.0
00e3f000-00e40000 rw-p 00006000 08:11 1450881    /usr/lib/fglrx/libatiuki.so.1.0
00e42000-00e49000 r-xp 00000000 08:11 1308350    /lib/libwrap.so.0.7.6
00e49000-00e4a000 r--p 00006000 08:11 1308350    /lib/libwrap.so.0.7.6
00e4a000-00e4b000 rw-p 00007000 08:11 1308350    /lib/libwrap.so.0.7.6
00e59000-00e8c000 r-xp 00000000 08:11 1308298    /lib/libpcre.so.3.12.1
00e8c000-00e8d000 r--p 00032000 08:11 1308298    /lib/libpcre.so.3.12.1
00e8d000-00e8e000 rw-p 00033000 08:11 1308298    /lib/libpcre.so.3.12.1
00eb9000-00ed5000 r-xp 00000000 08:11 1308590    /lib/ld-2.12.1.so
00ed5000-00ed6000 r--p 0001b000 08:11 1308590    /lib/ld-2.12.1.so
00ed6000-00ed7000 rw-p 0001c000 08:11 1308590    /lib/ld-2.12.1.so
00f22000-00f61000 r-xp 00000000 08:11 1439378    /usr/lib/libpulse.so.0.12.2
00f61000-00f62000 ---p 0003f000 08:11 1439378    /usr/lib/libpulse.so.0.12.2
00f62000-00f63000 r--p 0003f000 08:11 1439378    /usr/lib/libpulse.so.0.12.2
00f63000-00f64000 rw-p 00040000 08:11 1439378    /usr/lib/libpulse.so.0.12.2
00f66000-00f79000 r-xp 00000000 08:11 1308355    /lib/libz.so.1.2.3.4
00f79000-00f7a000 r--p 00012000 08:11 1308355    /lib/libz.so.1.2.3.4
00f7a000-00f7b000 rw-p 00013000 08:11 1308355    /lib/libz.so.1.2.3.4
00fc0000-00fc2000 r-xp 00000000 08:11 1308655    /lib/libdl-2.12.1.so
00fc2000-00fc3000 r--p 00001000 08:11 1308655    /lib/libdl-2.12.1.so
00fc3000-00fc4000 rw-p 00002000 08:11 1308655    /lib/libdl-2.12.1.so
00fc4000-01688000 r-xp 00000000 08:11 1459861    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
01688000-016cd000 r--p 006c4000 08:11 1459861    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
016cd000-016dc000 rw-p 00709000 08:11 1459861    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
016dc000-01afb000 rw-p 00000000 00:00 0 
01afb000-01baf000 r-xp 00000000 08:11 1450885    /usr/lib/fglrx/libGL.so.1.2
01baf000-01bba000 rwxp 000b3000 08:11 1450885    /usr/lib/fglrx/libGL.so.1.2
01bba000-01bbf000 rwxp 00000000 00:00 0 
01bbf000-01c7f000 r-xp 00000000 08:11 1439219    /usr/lib/libasound.so.2.0.0
01c7f000-01c80000 ---p 000c0000 08:11 1439219    /usr/lib/libasound.so.2.0.0
01c80000-01c84000 r--p 000c0000 08:11 1439219    /usr/lib/libasound.so.2.0.0
01c84000-01c85000 rw-p 000c4000 08:11 1439219    /usr/lib/libasound.so.2.0.0
01c85000-01ccf000 r-xp 00000000 08:11 1442760    /usr/lib/libFLAC.so.8.2.0
01ccf000-01cd0000 r--p 00049000 08:11 1442760    /usr/lib/libFLAC.so.8.2.0
01cd0000-01cd1000 rw-p 0004a000 08:11 1442760    /usr/lib/libFLAC.so.8.2.0
02f5a000-02fbb000 r-xp 00000000 08:11 1443629    /usr/lib/libsndfile.so.1.0.21
02fbb000-02fbc000 ---p 00061000 08:11 1443629    /usr/lib/libsndfile.so.1.0.21
02fbc000-02fbd000 r--p 00061000 08:11 1443629    /usr/lib/libsndfile.so.1.0.21
02fbd000-02fbe000 rw-p 00062000 08:11 1443629    /usr/lib/libsndfile.so.1.0.21
02fbe000-02fc2000 rw-p 00000000 00:00 0 
04298000-042bd000 r-xp 00000000 08:15 405536     /home/arachan/.minecraft/bin/natives/libopenal.so
042bd000-042be000 rw-p 00025000 08:15 405536     /home/arachan/.minecraft/bin/natives/libopenal.so
042be000-043ab000 rw-p 00000000 00:00 0 
04560000-04928000 r-xp 00000000 08:11 1443266    /usr/lib/libgtk-x11-2.0.so.0.2200.0
04928000-0492c000 r--p 003c8000 08:11 1443266    /usr/lib/libgtk-x11-2.0.so.0.2200.0
0492c000-0492e000 rw-p 003cc000 08:11 1443266    /usr/lib/libgtk-x11-2.0.so.0.2200.0
0492e000-04930000 rw-p 00000000 00:00 0 
04aaa000-04c0f000 r-xp 00000000 08:11 1443723    /usr/lib/libvorbisenc.so.2.0.7
04c0f000-04c10000 ---p 00165000 08:11 1443723    /usr/lib/libvorbisenc.so.2.0.7
04c10000-04c21000 r--p 00165000 08:11 1443723    /usr/lib/libvorbisenc.so.2.0.7
04c21000-04c22000 rw-p 00176000 08:11 1443723    /usr/lib/libvorbisenc.so.2.0.7
05594000-06fa9000 r-xp 00000000 08:11 1450883    /usr/lib/fglrx/dri/fglrx_dri.so
06fa9000-0706d000 rw-p 01a15000 08:11 1450883    /usr/lib/fglrx/dri/fglrx_dri.so
0706d000-070f8000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:11 1441170    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:11 1441170    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:11 1441170    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08140000-08a61000 rw-p 00000000 00:00 0          [heap]
5a0ff000-5a1ff000 rw-s 0985b000 00:05 8865       /dev/ati/card0
5a1ff000-5a200000 ---p 00000000 00:00 0 
5a200000-5a400000 rw-p 00000000 00:00 0 
5a400000-5a4e9000 rw-p 00000000 00:00 0 
5a4e9000-5a500000 ---p 00000000 00:00 0 
5a5af000-5a5b2000 ---p 00000000 00:00 0 
5a5b2000-5a600000 rw-p 00000000 00:00 0 
5a600000-5a6fd000 rw-p 00000000 00:00 0 
5a6fd000-5a700000 ---p 00000000 00:00 0 
5a700000-5a800000 rw-p 00000000 00:00 0 
5a800000-5a8fd000 rw-p 00000000 00:00 0 
5a8fd000-5a900000 ---p 00000000 00:00 0 
5a900000-5a9fd000 rw-p 00000000 00:00 0 
5a9fd000-5aa00000 ---p 00000000 00:00 0 
5aa00000-5ab00000 rw-p 00000000 00:00 0 
5ab17000-64b57000 rw-p 00000000 00:00 0 
64b57000-64b58000 ---p 00000000 00:00 0 
64b58000-65358000 rw-p 00000000 00:00 0 
65358000-65359000 ---p 00000000 00:00 0 
65359000-65b59000 rw-p 00000000 00:00 0 
65b59000-69b5a000 rw-s 00000000 00:10 351532     /dev/shm/pulse-shm-4230955227
69b5a000-69b5d000 ---p 00000000 00:00 0 
69b5d000-69bab000 rw-p 00000000 00:00 0 
69bab000-69bae000 ---p 00000000 00:00 0 
69bae000-69bfc000 rw-p 00000000 00:00 0 
69bfc000-69dfc000 rw-s 0980b000 00:05 8865       /dev/ati/card0
69dfc000-6a700000 rw-p 00000000 00:00 0 
6a700000-6a7e1000 rw-p 00000000 00:00 0 
6a7e1000-6a800000 ---p 00000000 00:00 0 
6a800000-6a900000 rw-s 09807000 00:05 8865       /dev/ati/card0
6a900000-6aa00000 rw-p 00000000 00:00 0 
6aa3f000-6aa40000 ---p 00000000 00:00 0 
6aa40000-6aa50000 rw-p 00000000 00:00 0 
6aa50000-6aa90000 rw-s 00013000 00:05 8865       /dev/ati/card0
6aa90000-6ab10000 rw-p 00000000 00:00 0 
6ab10000-6b210000 rw-s 00006000 00:05 8865       /dev/ati/card0
6b210000-6b213000 ---p 00000000 00:00 0 
6b213000-6b261000 rw-p 00000000 00:00 0 
6b261000-6b2c6000 rw-s 00000000 00:04 9535516    /SYSV00000000 (deleted)
6b2c6000-6b2c9000 ---p 00000000 00:00 0 
6b2c9000-6b317000 rw-p 00000000 00:00 0 
6b317000-6b31a000 ---p 00000000 00:00 0 
6b31a000-6b368000 rw-p 00000000 00:00 0 
6b368000-6b36b000 ---p 00000000 00:00 0 
6b36b000-6b3b9000 rw-p 00000000 00:00 0 
6b3b9000-6b3bc000 ---p 00000000 00:00 0 
6b3bc000-6b40a000 rw-p 00000000 00:00 0 
6b40a000-6b59b000 rw-s 00000000 00:04 9502747    /SYSV00000000 (deleted)
6b59b000-6b600000 rw-s 00000000 00:04 9469978    /SYSV00000000 (deleted)
6b600000-6b700000 rw-p 00000000 00:00 0 
6b70d000-6b710000 ---p 00000000 00:00 0 
6b710000-6b75e000 rw-p 00000000 00:00 0 
6b75e000-6b761000 ---p 00000000 00:00 0 
6b761000-6b7af000 rw-p 00000000 00:00 0 
6b7af000-6b7b2000 ---p 00000000 00:00 0 
6b7b2000-6b800000 rw-p 00000000 00:00 0 
6b800000-6b8ff000 rw-p 00000000 00:00 0 
6b8ff000-6b900000 ---p 00000000 00:00 0 
6b907000-6b90e000 r--s 00000000 08:11 1455925    /usr/lib/gconv/gconv-modules.cache
6b90e000-6b90f000 rw-s 00005000 00:05 8865       /dev/ati/card0
6b90f000-6b92f000 rw-s fe9c0000 00:05 8865       /dev/ati/card0
6b92f000-6b931000 rw-s 00002000 00:05 8865       /dev/ati/card0
6b931000-6b93c000 r--s 00127000 08:15 405464     /home/arachan/.minecraft/bin/minecraft.jar
6b93c000-6b93f000 r--s 00011000 08:15 405531     /home/arachan/.minecraft/bin/lwjgl_util.jar
6b93f000-6b944000 r--s 0002f000 08:15 405529     /home/arachan/.minecraft/bin/jinput.jar
6b944000-6b94b000 r--s 00083000 08:15 405530     /home/arachan/.minecraft/bin/lwjgl.jar
6b94b000-6b94e000 r--s 00031000 08:11 1446945    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
6b94e000-6b954000 r--s 000fc000 08:11 1458048    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
6b954000-6b955000 r--s 00000000 08:11 916182     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
6b955000-6b956000 r--s 00000000 08:11 916381     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b956000-6b95c000 r--s 00000000 08:11 916380     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b95c000-6b95e000 r--s 00000000 08:11 916377     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b95e000-6b961000 r--s 00000000 08:11 916376     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b961000-6b967000 r--s 00000000 08:11 918571     /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
6b967000-6b96a000 r--s 00000000 08:11 935923     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b96a000-6b96b000 r--s 00000000 08:11 933416     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-le32d4.cache-3
6b96b000-6b96d000 r--s 00000000 08:11 933415     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-le32d4.cache-3
6b96d000-6b96e000 r--s 00000000 08:11 933414     /var/cache/fontconfig/fc14e3aff40829fbb7132d5e06a8168b-le32d4.cache-3
6b96e000-6b96f000 r--s 00000000 08:11 933413     /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-le32d4.cache-3
6b96f000-6b970000 r--s 00000000 08:11 916372     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6b970000-6b971000 r--s 00000000 08:11 933412     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-le32d4.cache-3
6b971000-6b974000 r--s 00000000 08:11 916371     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6b974000-6b975000 r--s 00000000 08:11 916369     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6b975000-6b976000 r--s 00000000 08:11 916368     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6b976000-6b978000 r--s 00000000 08:11 933411     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-le32d4.cache-3
6b978000-6b979000 r--s 00000000 08:11 916367     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6b979000-6b97d000 r--s 00000000 08:11 916365     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b97d000-6b97f000 r--s 00000000 08:11 933410     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-le32d4.cache-3
6b97f000-6b982000 r--s 00000000 08:11 933409     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-le32d4.cache-3
6b982000-6b989000 r--s 00000000 08:11 916087     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6b989000-6b98b000 r--s 00000000 08:11 933408     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-le32d4.cache-3
6b98b000-6b996000 r--s 00000000 08:11 916048     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6b996000-6b999000 r--s 00000000 08:11 916046     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6b999000-6b99a000 r--s 00000000 08:11 933396     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
6b99a000-6b9bc000 r--s 00000000 08:11 923335     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6b9bc000-6b9c4000 r--s 00000000 08:11 916043     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6b9c4000-6b9cc000 r--s 00000000 08:11 915967     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6b9cc000-6b9cf000 r--s 00000000 08:11 933407     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
6b9cf000-6b9d5000 r--s 00000000 08:15 5041       /home/arachan/.fontconfig/1832c906f2ff15b8b91145fa4e8a135a-le32d4.cache-3
6b9d5000-6b9d6000 r--s 00000000 08:11 916182     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
6b9d6000-6b9d7000 r--s 00000000 08:11 916381     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
6b9d7000-6b9dd000 r--s 00000000 08:11 916380     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
6b9dd000-6b9df000 r--s 00000000 08:11 916377     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
6b9df000-6b9e2000 r--s 00000000 08:11 916376     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
6b9e2000-6b9e8000 r--s 00000000 08:11 918571     /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
6b9e8000-6b9eb000 r--s 00000000 08:11 935923     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
6b9eb000-6b9ec000 r--s 00000000 08:11 933416     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-le32d4.cache-3
6b9ec000-6b9ee000 r--s 00000000 08:11 933415     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-le32d4.cache-3
6b9ee000-6b9ef000 r--s 00000000 08:11 933414     /var/cache/fontconfig/fc14e3aff40829fbb7132d5e06a8168b-le32d4.cache-3
6b9ef000-6b9f0000 r--s 00000000 08:11 933413     /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-le32d4.cache-3
6b9f0000-6b9f1000 r--s 00000000 08:11 916372     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
6b9f1000-6b9f2000 r--s 00000000 08:11 933412     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-le32d4.cache-3
6b9f2000-6b9f5000 r--s 00000000 08:11 916371     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
6b9f5000-6b9f6000 r--s 00000000 08:11 916369     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
6b9f6000-6b9f7000 r--s 00000000 08:11 916368     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
6b9f7000-6b9f9000 r--s 00000000 08:11 933411     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-le32d4.cache-3
6b9f9000-6b9fa000 r--s 00000000 08:11 916367     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
6b9fa000-6b9fe000 r--s 00000000 08:11 916365     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
6b9fe000-6ba00000 r--s 00000000 08:11 933410     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-le32d4.cache-3
6ba00000-6ba03000 r--s 00000000 08:11 933409     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-le32d4.cache-3
6ba03000-6ba0a000 r--s 00000000 08:11 916087     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
6ba0a000-6ba0c000 r--s 00000000 08:11 933408     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-le32d4.cache-3
6ba0c000-6ba17000 r--s 00000000 08:11 916048     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
6ba17000-6ba39000 r--s 00000000 08:11 923335     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
6ba39000-6ba3c000 ---p 00000000 00:00 0 
6ba3c000-6ba8a000 rw-p 00000000 00:00 0 
6ba8a000-6ba8b000 ---p 00000000 00:00 0 
6ba8b000-6bb0b000 rw-p 00000000 00:00 0 
6bb0b000-6bb0e000 ---p 00000000 00:00 0 
6bb0e000-6bb5c000 rw-p 00000000 00:00 0 
6bb5c000-6bb5f000 ---p 00000000 00:00 0 
6bb5f000-6bbdd000 rw-p 00000000 00:00 0 
6bbdd000-6bbe0000 ---p 00000000 00:00 0 
6bbe0000-6bc5e000 rw-p 00000000 00:00 0 
6bc5e000-6bc61000 ---p 00000000 00:00 0 
6bc61000-6bcaf000 rw-p 00000000 00:00 0 
6bcaf000-6beaf000 r--p 00000000 08:11 1440743    /usr/lib/locale/locale-archive
6beaf000-6beb2000 ---p 00000000 00:00 0 
6beb2000-6bf00000 rw-p 00000000 00:00 0 
6bf00000-6bff8000 rw-p 00000000 00:00 0 
6bff8000-6c000000 ---p 00000000 00:00 0 
6c002000-6c004000 r--s 00013000 08:11 1440825    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
6c004000-6c007000 r--s 00077000 08:11 1446944    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
6c007000-6c009000 r--s 00001000 08:11 1448812    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/dnsns.jar
6c009000-6c00c000 r--s 00000000 08:11 916046     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
6c00c000-6c014000 r--s 00000000 08:11 916043     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
6c014000-6c01c000 r--s 00000000 08:11 915967     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
6c01c000-6c022000 r--s 00000000 08:15 5041       /home/arachan/.fontconfig/1832c906f2ff15b8b91145fa4e8a135a-le32d4.cache-3
6c022000-6c026000 r--s 0007c000 08:11 1440818    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
6c026000-6c02c000 r--s 0004e000 08:15 404504     /home/arachan/.minecraft/Minecraft.jar
6c02c000-6c02f000 ---p 00000000 00:00 0 
6c02f000-6c07d000 rw-p 00000000 00:00 0 
6c07d000-6c07e000 ---p 00000000 00:00 0 
6c07e000-6c0fe000 rw-p 00000000 00:00 0 
6c0fe000-6c100000 r--s 0001d000 08:11 1441173    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
6c100000-6c105000 r--s 00044000 08:11 1442388    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
6c105000-6c138000 rw-p 00000000 00:00 0 
6c138000-6c2c7000 r--s 038c2000 08:11 1459880    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
6c2c7000-6c2c8000 ---p 00000000 00:00 0 
6c2c8000-6c348000 rw-p 00000000 00:00 0 
6c348000-6c349000 ---p 00000000 00:00 0 
6c349000-6c3dd000 rw-p 00000000 00:00 0 
6c3dd000-6c409000 rw-p 00000000 00:00 0 
6c409000-6c4b4000 rw-p 00000000 00:00 0 
6c4b4000-6c55f000 rw-p 00000000 00:00 0 
6c55f000-6c573000 rw-p 00000000 00:00 0 
6c573000-6c59f000 rw-p 00000000 00:00 0 
6c59f000-6c64a000 rw-p 00000000 00:00 0 
6c64a000-6c6f4000 rw-p 00000000 00:00 0 
6c6f4000-6c74a000 rw-p 00000000 00:00 0 
6c74a000-6c79f000 rw-p 00000000 00:00 0 
6c79f000-6ee40000 rw-p 00000000 00:00 0 
6ee40000-747a0000 rw-p 00000000 00:00 0 
747a0000-89d00000 rw-p 00000000 00:00 0 
89d00000-9f250000 rw-p 00000000 00:00 0 
9f250000-a9cf0000 rw-p 00000000 00:00 0 
a9cf0000-b47a0000 rw-p 00000000 00:00 0 
b47a0000-b47a1000 r--p 00000000 00:00 0 
b47a1000-b47a2000 r--s 00000000 08:11 933396     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b47a2000-b47aa000 r--s 00066000 08:11 156119     /usr/share/java/gnome-java-bridge.jar
b47aa000-b47b3000 rw-p 00000000 00:00 0 
b47b3000-b486a000 rw-p 00000000 00:00 0 
b486a000-b4aaa000 rwxp 00000000 00:00 0 
b4aaa000-b786a000 rw-p 00000000 00:00 0 
b786a000-b786d000 ---p 00000000 00:00 0 
b786d000-b78be000 rw-p 00000000 00:00 0 
b78be000-b78c1000 r--s 00000000 08:11 933407     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b78c1000-b78c4000 r--s 0000f000 08:11 1448971    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b78c4000-b78c5000 r--p 0029e000 08:11 1440743    /usr/lib/locale/locale-archive
b78c5000-b78cd000 rw-s 00000000 08:11 1178085    /tmp/hsperfdata_arachan/24131
b78cd000-b78ce000 rw-p 00000000 00:00 0 
b78ce000-b78cf000 ---p 00000000 00:00 0 
b78cf000-b78d1000 rw-p 00000000 00:00 0 
bff01000-bff22000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1024M -Xms512M 
java_command: net.minecraft.LauncherFrame
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=arachan
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6497c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6497c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x51ba60], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x51b110], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x51dc80], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.10 (maverick)
uname:Linux 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.18 0.22 0.22

/proc/meminfo:
MemTotal:        2060368 kB
MemFree:           56740 kB
Buffers:           43028 kB
Cached:           942372 kB
SwapCached:            0 kB
Active:           993276 kB
Inactive:         798848 kB
Active(anon):     649796 kB
Inactive(anon):   191660 kB
Active(file):     343480 kB
Inactive(file):   607188 kB
Unevictable:         756 kB
Mlocked:              64 kB
HighTotal:       1187400 kB
HighFree:           3076 kB
LowTotal:         872968 kB
LowFree:           53664 kB
SwapTotal:       8193144 kB
SwapFree:        8193144 kB
Dirty:               308 kB
Writeback:             0 kB
AnonPages:        807480 kB
Mapped:           210280 kB
Shmem:             33988 kB
Slab:              49204 kB
SReclaimable:      32648 kB
SUnreclaim:        16556 kB
KernelStack:        3080 kB
PageTables:         9064 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9223328 kB
Committed_AS:    2548908 kB
VmallocTotal:     122880 kB
VmallocUsed:       61728 kB
VmallocChunk:      55516 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 23 stepping 6, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1

Memory: 4k page, physical 2060368k(56740k free), swap 8193144k(8193144k free)

vm_info: OpenJDK Server VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 23 2011 09:09:10 by "buildd" with gcc 4.4.5

time: Sun Mar  6 10:03:27 2011
elapsed time: 9 seconds

```

---

### Post by keltic dave on 2011-03-05
the only thing you need is the opensource java which you can get from the ubuntu software centre and the client. Which you right click and make executable. Shouldn't need to so anything other than that.

---

### Post by cisasteelersfan on 2011-03-11
Archan, do you by any chance have an ATI graphics card? There is some bug with the ATI drivers and java. I have not yet found a way around it. I'm kind of angry at ATI because I bought this card to play minecraft, and now I can't (in Ubuntu).

---

### Post by wog on 2011-03-12
Personally I'd uninstall OpenJDK and install Sun Java, since that's the version Minecraft wants and is expecting.

---

### Post by Arachan on 2011-03-13
Hello,

Cisastellersfan, I do have an ATI graphics card, it's the HD5770.

At first I just got a black screen in Minecraft which apparently is quite common. I followed the instructions here: [http://www.timashley.me/node/596](http://www.timashley.me/node/596) and this fixed the black screen problem, but as I said above I still can't play it.

Wog, I open Minecraft with "Sun Java 6 Runtime", so I figure having OpenJDK can't really hurt.

Thanks for your replies,
Arachan.

---

### Post by Arachan on 2011-06-07
I have done some more reading into this and it turns out that it is a bug with the propriety AMD drivers for ATI GPUs.

I have discovered a workaround, that is to remove these drivers. The only disadvantage I have noticed so far is that I can no longer monitor my GPU temperature and fan speed.

Once I had done that, I tried to play Minecraft again, which now seemed to work. The only problem was that there was a constant black flickering, which is caused by compiz desktop effects. Now when I run Minecraft I simply turn these off and it runs fine. For the record it seems to use a lot less RAM than in Windows 7 but has a lower framerate.

Thanks for everyone's help.
Arachan.

EDIT: As of Natty, I can play Minecraft (and other games) with the propriety AMD drivers very well.

---

