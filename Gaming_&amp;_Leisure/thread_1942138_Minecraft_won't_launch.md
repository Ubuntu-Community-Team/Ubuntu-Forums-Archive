---
title: "Minecraft won't launch"
date: 2012-03-16
forum: Gaming &amp; Leisure
---

### Post by manij on 2012-03-16
Hi,

Minecraft will not launch. I get the log in screen and and it simply crashes when I type in my password.

Help please!

Here is the error log

```
 #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00a30ef6, pid=8095, tid=3033033584
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.13
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.13-0ubuntu1~10.04.1
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0xb4ac1400):  JavaThread "Minecraft main thread" daemon [_thread_in_native, id=8138, stack(0xb4c36000,0xb4c87000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000004

Registers:
EAX=0x00000041, EBX=0x083a8468, ECX=0x083ea318, EDX=0x00a7dd60
ESP=0xb4c838c4, EBP=0x083a9bf0, ESI=0x00000000, EDI=0x00000001
EIP=0x00a30ef6, CR2=0x00000004, EFLAGS=0x00010202

Register to memory mapping:

EAX=0x00000041
0x00000041 is pointing to unknown location

EBX=0x083a8468
0x083a8468 is pointing to unknown location

ECX=0x083ea318
0x083ea318 is pointing to unknown location

EDX=0x00a7dd60
0x00a7dd60: <offset 0xb2d60> in /usr/lib/fglrx/libGL.so.1 at 0x009cb000

ESP=0xb4c838c4
0xb4c838c4 is pointing into the stack for thread: 0xb4ac1400
"Minecraft main thread" daemon prio=10 tid=0xb4ac1400 nid=0x1fca runnable [0xb4c85000]
   java.lang.Thread.State: RUNNABLE

EBP=0x083a9bf0
0x083a9bf0 is pointing to unknown location

ESI=0x00000000
0x00000000 is pointing to unknown location

EDI=0x00000001
0x00000001 is pointing to unknown location


Top of Stack: (sp=0xb4c838c4)
0xb4c838c4:   0025657e 00258a9d 00000000 00000000
0xb4c838d4:   0000000d 00000078 b4c838fc 0000000d
0xb4c838e4:   00000064 00000001 083a9bf0 00002000
0xb4c838f4:   083a7b94 00a2e5d0 083a9bf0 b4c83940
0xb4c83904:   b4c83944 0033f3c0 00000090 0033f3f0
0xb4c83914:   0033dff4 0033f3c0 b4c8596c bfbc5250
0xb4c83924:   bfbc6c97 b4c83958 00217932 bfbc6c99
0xb4c83934:   00a5c0de 00000013 00a5c0de 00000013 

Instructions: (pc=0x00a30ef6)
0x00a30ee6:   00 66 89 79 02 83 45 6c 04 83 45 60 01 8b 76 08
0x00a30ef6:   0f b6 56 04 88 11 88 41 01 33 c9 8d 04 24 51 51 

Stack: [0xb4c36000,0xb4c87000],  sp=0xb4c838c4,  free space=310k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(JILjava/nio/ByteBuffer;Lorg/lwjgl/opengl/PixelFormat;)V+0
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(Lorg/lwjgl/opengl/PixelFormat;)V+24
j  org.lwjgl.opengl.LinuxDisplay.createPeerInfo(Lorg/lwjgl/opengl/PixelFormat;)Lorg/lwjgl/opengl/PeerInfo;+6
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;Lorg/lwjgl/opengl/Drawable;Lorg/lwjgl/opengl/ContextAttribs;)V+55
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;)V+9
j  net.minecraft.client.Minecraft.a()V+151
j  net.minecraft.client.Minecraft.run()V+6
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0xb4ac1400 JavaThread "Minecraft main thread" daemon [_thread_in_native, id=8138, stack(0xb4c36000,0xb4c87000)]
  0xb4abe000 JavaThread "Timer hack thread" daemon [_thread_blocked, id=8137, stack(0xb43ba000,0xb440b000)]
  0x08566400 JavaThread "Keep-Alive-Timer" daemon [_thread_blocked, id=8134, stack(0xb4951000,0xb49a2000)]
  0xb4a1bc00 JavaThread "TimerQueue" daemon [_thread_blocked, id=8118, stack(0xb49a2000,0xb49f3000)]
  0xb4aadc00 JavaThread "DestroyJavaVM" [_thread_blocked, id=8096, stack(0xb769a000,0xb76eb000)]
  0xb4fb4000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=8114, stack(0xb4b07000,0xb4b58000)]
  0xb4fa7400 JavaThread "AWT-Shutdown" [_thread_blocked, id=8113, stack(0xb4b58000,0xb4ba9000)]
  0xb4f9f000 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=8107, stack(0xb4c87000,0xb4cd8000)]
  0xb4f5c000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=8106, stack(0xb4ddd000,0xb4e2e000)]
  0xb4f02800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=8102, stack(0xb4eaf000,0xb4f00000)]
  0xb4f00800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=8101, stack(0xb501d000,0xb509e000)]
  0x0838ec00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=8100, stack(0xb509e000,0xb50ef000)]
  0x08386800 JavaThread "Finalizer" daemon [_thread_blocked, id=8099, stack(0xb5135000,0xb5186000)]
  0x08385000 JavaThread "Reference Handler" daemon [_thread_blocked, id=8098, stack(0xb5186000,0xb51d7000)]

Other Threads:
  0x08383400 VMThread [stack: 0xb51d7000,0xb5258000] [id=8097]
  0xb4f05000 WatcherThread [stack: 0xb4e2e000,0xb4eaf000] [id=8103]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 8640K, used 2286K [0x6f880000, 0x701e0000, 0x7a320000)
  eden space 7680K,  17% used [0x6f880000, 0x6f9cb880, 0x70000000)
  from space 960K,  99% used [0x70000000, 0x700efff8, 0x700f0000)
  to   space 960K,   0% used [0x700f0000, 0x700f0000, 0x701e0000)
 tenured generation   total 19140K, used 18015K [0x7a320000, 0x7b5d1000, 0x8f880000)
   the space 19140K,  94% used [0x7a320000, 0x7b4b7f20, 0x7b4b8000, 0x7b5d1000)
 compacting perm gen  total 12288K, used 6378K [0x8f880000, 0x90480000, 0x93880000)
   the space 12288K,  51% used [0x8f880000, 0x8febabd8, 0x8febac00, 0x90480000)
    ro space 10240K,  73% used [0x93880000, 0x93fd9098, 0x93fd9200, 0x94280000)
    rw space 12288K,  60% used [0x94280000, 0x949c1388, 0x949c1400, 0x94e80000)

Dynamic libraries:
00110000-00134000 r-xp 00000000 08:01 5424097    /lib/tls/i686/cmov/libm-2.11.1.so
00134000-00135000 r--p 00023000 08:01 5424097    /lib/tls/i686/cmov/libm-2.11.1.so
00135000-00136000 rw-p 00024000 08:01 5424097    /lib/tls/i686/cmov/libm-2.11.1.so
00136000-00149000 r-xp 00000000 08:01 5423408    /lib/tls/i686/cmov/libnsl-2.11.1.so
00149000-0014a000 r--p 00012000 08:01 5423408    /lib/tls/i686/cmov/libnsl-2.11.1.so
0014a000-0014b000 rw-p 00013000 08:01 5423408    /lib/tls/i686/cmov/libnsl-2.11.1.so
0014b000-0014d000 rw-p 00000000 00:00 0 
0014d000-00157000 r-xp 00000000 08:01 5424003    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00157000-00158000 r--p 00009000 08:01 5424003    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00158000-00159000 rw-p 0000a000 08:01 5424003    /lib/tls/i686/cmov/libnss_files-2.11.1.so
00159000-0019e000 r-xp 00000000 08:01 1311338    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0019e000-0019f000 r--p 00044000 08:01 1311338    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
0019f000-001a1000 rw-p 00045000 08:01 1311338    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
001a1000-001a2000 rw-p 00000000 00:00 0 
001a2000-001b0000 r-xp 00000000 08:01 5391941    /usr/lib/libXext.so.6.4.0
001b0000-001b1000 r--p 0000d000 08:01 5391941    /usr/lib/libXext.so.6.4.0
001b1000-001b2000 rw-p 0000e000 08:01 5391941    /usr/lib/libXext.so.6.4.0
001b2000-001be000 r-xp 00000000 08:01 5391949    /usr/lib/libXi.so.6.1.0
001be000-001bf000 r--p 0000c000 08:01 5391949    /usr/lib/libXi.so.6.1.0
001bf000-001c0000 rw-p 0000d000 08:01 5391949    /usr/lib/libXi.so.6.1.0
001c0000-001c4000 r-xp 00000000 08:01 5391939    /usr/lib/libXdmcp.so.6.0.0
001c4000-001c5000 r--p 00003000 08:01 5391939    /usr/lib/libXdmcp.so.6.0.0
001c5000-001c6000 rw-p 00004000 08:01 5391939    /usr/lib/libXdmcp.so.6.0.0
001c6000-001c9000 r-xp 00000000 08:01 5390595    /usr/lib/libplc4.so
001c9000-001ca000 r--p 00002000 08:01 5390595    /usr/lib/libplc4.so
001ca000-001cb000 rw-p 00003000 08:01 5390595    /usr/lib/libplc4.so
001cc000-001e7000 r-xp 00000000 08:01 5400614    /lib/ld-2.11.1.so
001e7000-001e8000 r--p 0001a000 08:01 5400614    /lib/ld-2.11.1.so
001e8000-001e9000 rw-p 0001b000 08:01 5400614    /lib/ld-2.11.1.so
001e9000-0033c000 r-xp 00000000 08:01 5424024    /lib/tls/i686/cmov/libc-2.11.1.so
0033c000-0033e000 r--p 00153000 08:01 5424024    /lib/tls/i686/cmov/libc-2.11.1.so
0033e000-0033f000 rw-p 00155000 08:01 5424024    /lib/tls/i686/cmov/libc-2.11.1.so
0033f000-00342000 rw-p 00000000 00:00 0 
00342000-0035f000 r-xp 00000000 08:01 5398577    /lib/libgcc_s.so.1
0035f000-00360000 r--p 0001c000 08:01 5398577    /lib/libgcc_s.so.1
00360000-00361000 rw-p 0001d000 08:01 5398577    /lib/libgcc_s.so.1
00361000-00369000 r-xp 00000000 08:01 5391935    /usr/lib/libXcursor.so.1.0.2
00369000-0036a000 r--p 00007000 08:01 5391935    /usr/lib/libXcursor.so.1.0.2
0036a000-0036b000 rw-p 00008000 08:01 5391935    /usr/lib/libXcursor.so.1.0.2
0036b000-00372000 r-xp 00000000 08:01 1296897    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00372000-00373000 r--p 00006000 08:01 1296897    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00373000-00374000 rw-p 00007000 08:01 1296897    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00374000-00375000 r-xp 00000000 08:01 1296580    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00375000-00376000 r--p 00000000 08:01 1296580    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
00376000-00377000 rw-p 00001000 08:01 1296580    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjawt.so
0037a000-0037b000 r-xp 00000000 00:00 0          [vdso]
0037b000-00400000 r-xp 00000000 08:01 1296500    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00400000-00401000 r--p 00085000 08:01 1296500    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00401000-00407000 rw-p 00086000 08:01 1296500    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
00407000-0042c000 rw-p 00000000 00:00 0 
0042c000-0045a000 r-xp 00000000 08:01 1296585    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
0045a000-0045b000 r--p 0002d000 08:01 1296585    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
0045b000-0045c000 rw-p 0002e000 08:01 1296585    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/liblcms.so
0045c000-0045e000 rw-p 00000000 00:00 0 
0045e000-0046e000 r-xp 00000000 08:01 5424009    /lib/tls/i686/cmov/libresolv-2.11.1.so
0046e000-0046f000 r--p 00010000 08:01 5424009    /lib/tls/i686/cmov/libresolv-2.11.1.so
0046f000-00470000 rw-p 00011000 08:01 5424009    /lib/tls/i686/cmov/libresolv-2.11.1.so
00470000-00472000 rw-p 00000000 00:00 0 
00472000-00476000 r-xp 00000000 08:01 5391969    /usr/lib/libXtst.so.6.1.0
00476000-00477000 r--p 00003000 08:01 5391969    /usr/lib/libXtst.so.6.1.0
00477000-00478000 rw-p 00004000 08:01 5391969    /usr/lib/libXtst.so.6.1.0
00478000-0047e000 r-xp 00000000 08:01 5391961    /usr/lib/libXrandr.so.2.2.0
0047e000-0047f000 r--p 00005000 08:01 5391961    /usr/lib/libXrandr.so.2.2.0
0047f000-00480000 rw-p 00006000 08:01 5391961    /usr/lib/libXrandr.so.2.2.0
00487000-004ab000 r-xp 00000000 08:01 1296578    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
004ab000-004ac000 r--p 00023000 08:01 1296578    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
004ac000-004ae000 rw-p 00024000 08:01 1296578    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
004ae000-004f2000 r-xp 00000000 08:01 1296512    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
004f2000-004f4000 r--p 00043000 08:01 1296512    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
004f4000-004f5000 rw-p 00045000 08:01 1296512    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so
004f5000-004fa000 rw-p 00000000 00:00 0 
004fa000-0056b000 r-xp 00000000 08:01 5391805    /usr/lib/libfreetype.so.6.3.22
0056b000-0056f000 r--p 00070000 08:01 5391805    /usr/lib/libfreetype.so.6.3.22
0056f000-00570000 rw-p 00074000 08:01 5391805    /usr/lib/libfreetype.so.6.3.22
00570000-0057e000 r-xp 00000000 08:01 1296575    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0057e000-0057f000 r--p 0000d000 08:01 1296575    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0057f000-00580000 rw-p 0000e000 08:01 1296575    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
00580000-00595000 r-xp 00000000 08:01 5393973    /usr/lib/libnssutil3.so
00595000-00598000 r--p 00014000 08:01 5393973    /usr/lib/libnssutil3.so
00598000-00599000 rw-p 00017000 08:01 5393973    /usr/lib/libnssutil3.so
00599000-005ca000 r-xp 00000000 08:01 5390594    /usr/lib/libnspr4.so
005ca000-005cb000 r--p 00030000 08:01 5390594    /usr/lib/libnspr4.so
005cb000-005cc000 rw-p 00031000 08:01 5390594    /usr/lib/libnspr4.so
005cc000-005ce000 rw-p 00000000 00:00 0 
005ce000-005d5000 r-xp 00000000 08:01 3852815    /usr/lib/fglrx/libatiuki.so.1.0
005d5000-005d6000 rw-p 00006000 08:01 3852815    /usr/lib/fglrx/libatiuki.so.1.0
005da000-005ee000 r-xp 00000000 08:01 1296675    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
005ee000-005ef000 r--p 00013000 08:01 1296675    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
005ef000-005f0000 rw-p 00014000 08:01 1296675    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00607000-0060e000 r-xp 00000000 08:01 5424102    /lib/tls/i686/cmov/librt-2.11.1.so
0060e000-0060f000 r--p 00006000 08:01 5424102    /lib/tls/i686/cmov/librt-2.11.1.so
0060f000-00610000 rw-p 00007000 08:01 5424102    /lib/tls/i686/cmov/librt-2.11.1.so
00610000-00647000 r-xp 00000000 08:01 5423548    /usr/lib/nss/libsoftokn3.so
00647000-00648000 r--p 00037000 08:01 5423548    /usr/lib/nss/libsoftokn3.so
00648000-00649000 rw-p 00038000 08:01 5423548    /usr/lib/nss/libsoftokn3.so
00657000-00663000 r-xp 00000000 08:01 1296905    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00663000-00664000 r--p 0000b000 08:01 1296905    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00664000-00665000 rw-p 0000c000 08:01 1296905    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00665000-006b0000 r-xp 00000000 08:01 5423547    /usr/lib/nss/libfreebl3.so
006b0000-006b1000 r--p 0004a000 08:01 5423547    /usr/lib/nss/libfreebl3.so
006b1000-006b2000 rw-p 0004b000 08:01 5423547    /usr/lib/nss/libfreebl3.so
006b2000-006b6000 rw-p 00000000 00:00 0 
006d7000-006d9000 r-xp 00000000 08:01 5398649    /lib/libnss_mdns4_minimal.so.2
006d9000-006da000 r--p 00001000 08:01 5398649    /lib/libnss_mdns4_minimal.so.2
006da000-006db000 rw-p 00002000 08:01 5398649    /lib/libnss_mdns4_minimal.so.2
006f8000-006fa000 r-xp 00000000 08:01 5391928    /usr/lib/libXau.so.6.0.0
006fa000-006fb000 r--p 00001000 08:01 5391928    /usr/lib/libXau.so.6.0.0
006fb000-006fc000 rw-p 00002000 08:01 5391928    /usr/lib/libXau.so.6.0.0
0076a000-00772000 r-xp 00000000 08:01 5424812    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00772000-00773000 r--p 00007000 08:01 5424812    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00773000-00774000 rw-p 00008000 08:01 5424812    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
007c4000-007c8000 r-xp 00000000 08:01 5391943    /usr/lib/libXfixes.so.3.1.0
007c8000-007c9000 r--p 00003000 08:01 5391943    /usr/lib/libXfixes.so.3.1.0
007c9000-007ca000 rw-p 00004000 08:01 5391943    /usr/lib/libXfixes.so.3.1.0
007ca000-0084a000 r-xp 00000000 08:01 5392820    /usr/lib/libsqlite3.so.0.8.6
0084a000-0084b000 r--p 0007f000 08:01 5392820    /usr/lib/libsqlite3.so.0.8.6
0084b000-0084c000 rw-p 00080000 08:01 5392820    /usr/lib/libsqlite3.so.0.8.6
0084c000-0084d000 rw-p 00000000 00:00 0 
008b8000-008cb000 r-xp 00000000 08:01 5398726    /lib/libz.so.1.2.3.3
008cb000-008cc000 r--p 00012000 08:01 5398726    /lib/libz.so.1.2.3.3
008cc000-008cd000 rw-p 00013000 08:01 5398726    /lib/libz.so.1.2.3.3
008ec000-00901000 r-xp 00000000 08:01 5423613    /lib/tls/i686/cmov/libpthread-2.11.1.so
00901000-00902000 r--p 00014000 08:01 5423613    /lib/tls/i686/cmov/libpthread-2.11.1.so
00902000-00903000 rw-p 00015000 08:01 5423613    /lib/tls/i686/cmov/libpthread-2.11.1.so
00903000-00905000 rw-p 00000000 00:00 0 
00932000-00939000 r-xp 00000000 08:01 1296906    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00939000-0093a000 r--p 00006000 08:01 1296906    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
0093a000-0093b000 rw-p 00007000 08:01 1296906    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00944000-0099b000 r-xp 00000000 08:01 2885373    /home/manij/.minecraft/bin/natives/liblwjgl.so
0099b000-0099c000 r--p 00056000 08:01 2885373    /home/manij/.minecraft/bin/natives/liblwjgl.so
0099c000-0099d000 rw-p 00057000 08:01 2885373    /home/manij/.minecraft/bin/natives/liblwjgl.so
009af000-009b8000 r-xp 00000000 08:01 1296582    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
009b8000-009b9000 r--p 00008000 08:01 1296582    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
009b9000-009ba000 rw-p 00009000 08:01 1296582    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjpeg.so
009c7000-009c9000 r-xp 00000000 08:01 5390596    /usr/lib/libplds4.so
009c9000-009ca000 r--p 00001000 08:01 5390596    /usr/lib/libplds4.so
009ca000-009cb000 rw-p 00002000 08:01 5390596    /usr/lib/libplds4.so
009cb000-00a72000 r-xp 00000000 08:01 3852811    /usr/lib/fglrx/libGL.so.1.2
00a72000-00a7c000 rwxp 000a7000 08:01 3852811    /usr/lib/fglrx/libGL.so.1.2
00a7c000-00a81000 rwxp 00000000 00:00 0 
00a94000-00bad000 r-xp 00000000 08:01 5391924    /usr/lib/libX11.so.6.3.0
00bad000-00bae000 r--p 00118000 08:01 5391924    /usr/lib/libX11.so.6.3.0
00bae000-00bb0000 rw-p 00119000 08:01 5391924    /usr/lib/libX11.so.6.3.0
00bb0000-00bb1000 rw-p 00000000 00:00 0 
00c02000-00c08000 r-xp 00000000 08:01 5424811    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00c08000-00c09000 r--p 00006000 08:01 5424811    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00c09000-00c0a000 rw-p 00007000 08:01 5424811    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00c4f000-00c53000 r-xp 00000000 08:01 5424814    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00c53000-00c54000 r--p 00004000 08:01 5424814    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00c54000-00c55000 rw-p 00005000 08:01 5424814    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
00ce3000-00ceb000 r-xp 00000000 08:01 5391963    /usr/lib/libXrender.so.1.3.0
00ceb000-00cec000 r--p 00007000 08:01 5391963    /usr/lib/libXrender.so.1.3.0
00cec000-00ced000 rw-p 00008000 08:01 5391963    /usr/lib/libXrender.so.1.3.0
00d74000-00d7b000 r-xp 00000000 08:01 1304043    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00d7b000-00d7c000 r--p 00006000 08:01 1304043    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00d7c000-00d7d000 rw-p 00007000 08:01 1304043    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00d82000-00d85000 r-xp 00000000 08:01 1296497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00d85000-00d86000 r--p 00003000 08:01 1296497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00d86000-00d87000 rw-p 00004000 08:01 1296497    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00db4000-00dcc000 r-xp 00000000 08:01 5392929    /usr/lib/libxcb.so.1.1.0
00dcc000-00dcd000 r--p 00017000 08:01 5392929    /usr/lib/libxcb.so.1.1.0
00dcd000-00dce000 rw-p 00018000 08:01 5392929    /usr/lib/libxcb.so.1.1.0
00ed2000-00ed4000 r-xp 00000000 08:01 5423560    /lib/tls/i686/cmov/libdl-2.11.1.so
00ed4000-00ed5000 r--p 00001000 08:01 5423560    /lib/tls/i686/cmov/libdl-2.11.1.so
00ed5000-00ed6000 rw-p 00002000 08:01 5423560    /lib/tls/i686/cmov/libdl-2.11.1.so
00ed6000-01329000 r-xp 00000000 08:01 1296485    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01329000-0132a000 ---p 00453000 08:01 1296485    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0132a000-01341000 r--p 00453000 08:01 1296485    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01341000-0134e000 rw-p 0046a000 08:01 1296485    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0134e000-0176a000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:01 1311240    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 1311240    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 1311240    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08180000-0828f000 r-xp 00000000 08:01 5393974    /usr/lib/libnss3.so
0828f000-08292000 r--p 0010e000 08:01 5393974    /usr/lib/libnss3.so
08292000-08294000 rw-p 00111000 08:01 5393974    /usr/lib/libnss3.so
08350000-0869b000 rw-p 00000000 00:00 0          [heap]
6f880000-701e0000 rw-p 00000000 00:00 0 
701e0000-7a320000 rw-p 00000000 00:00 0 
7a320000-7b5d1000 rw-p 00000000 00:00 0 
7b5d1000-8f880000 rw-p 00000000 00:00 0 
8f880000-90480000 rw-p 00000000 00:00 0 
90480000-93880000 rw-p 00000000 00:00 0 
93880000-93fda000 r--s 00001000 08:01 1294374    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
93fda000-94280000 rw-p 00000000 00:00 0 
94280000-949c2000 rw-p 0075b000 08:01 1294374    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
949c2000-94e80000 rw-p 00000000 00:00 0 
94e80000-94f7b000 rw-p 00e9d000 08:01 1294374    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94f7b000-95280000 rw-p 00000000 00:00 0 
95280000-95288000 r-xs 00f98000 08:01 1294374    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95288000-95680000 rw-p 00000000 00:00 0 
b41c4000-b4355000 rw-s 00000000 00:04 99581964   /SYSV00000000 (deleted)
b4355000-b43ba000 rw-s 00000000 00:04 99549194   /SYSV00000000 (deleted)
b43ba000-b43bd000 ---p 00000000 00:00 0 
b43bd000-b440b000 rw-p 00000000 00:00 0 
b440b000-b440e000 ---p 00000000 00:00 0 
b440e000-b445c000 rw-p 00000000 00:00 0 
b445c000-b4499000 rw-s 00000000 00:04 99221511   /SYSV00000000 (deleted)
b4499000-b462a000 rw-s 00000000 00:04 98959368   /SYSV00000000 (deleted)
b4800000-b4838000 rw-p 00000000 00:00 0 
b4838000-b4900000 ---p 00000000 00:00 0 
b492f000-b4945000 r--s 003b8000 08:01 2885456    /home/manij/.minecraft/bin/minecraft.jar
b4945000-b4948000 r--s 0001f000 08:01 2885440    /home/manij/.minecraft/bin/lwjgl_util.jar
b4948000-b4951000 r--s 000ac000 08:01 2885395    /home/manij/.minecraft/bin/lwjgl.jar
b4951000-b4954000 ---p 00000000 00:00 0 
b4954000-b49a2000 rw-p 00000000 00:00 0 
b49a2000-b49a5000 ---p 00000000 00:00 0 
b49a5000-b49f3000 rw-p 00000000 00:00 0 
b49f5000-b49fa000 r--s 00033000 08:01 2885432    /home/manij/.minecraft/bin/jinput.jar
b49fa000-b49fd000 r--s 00038000 08:01 5644542    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b49fd000-b4a00000 r--s 00077000 08:01 5644548    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar
b4a00000-b4af8000 rw-p 00000000 00:00 0 
b4af8000-b4b00000 ---p 00000000 00:00 0 
b4b01000-b4b04000 r--s 00031000 08:01 5644558    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b4b04000-b4b07000 r--s 0007d000 08:01 5644654    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4b07000-b4b0a000 ---p 00000000 00:00 0 
b4b0a000-b4b58000 rw-p 00000000 00:00 0 
b4b58000-b4b5b000 ---p 00000000 00:00 0 
b4b5b000-b4ba9000 rw-p 00000000 00:00 0 
b4ba9000-b4bab000 r--s 00013000 08:01 5644653    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4bab000-b4bac000 r--s 00000000 08:01 3850974    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4bac000-b4bad000 r--s 00000000 08:01 3851806    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4bad000-b4bb3000 r--s 00000000 08:01 3850308    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4bb3000-b4bb5000 r--s 00000000 08:01 3851804    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4bb5000-b4bb7000 r--s 00000000 08:01 3851803    /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-le32d4.cache-3
b4bb7000-b4bba000 r--s 00000000 08:01 3851802    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4bba000-b4bc0000 r--s 00000000 08:01 3850975    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4bc0000-b4bc1000 r--s 00000000 08:01 3851800    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4bc1000-b4bc3000 r--s 00000000 08:01 3851799    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-le32d4.cache-3
b4bc3000-b4bc6000 r--s 00000000 08:01 3851798    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4bc6000-b4bc7000 r--s 00000000 08:01 3851797    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4bc7000-b4bc8000 r--s 00000000 08:01 3851796    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4bc8000-b4bc9000 r--s 00000000 08:01 3851795    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4bc9000-b4bcd000 r--s 00000000 08:01 3851794    /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-le32d4.cache-3
b4bcd000-b4bd1000 r--s 00000000 08:01 3851793    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4bd1000-b4bd5000 r--s 00000000 08:01 3851008    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4bd5000-b4bdc000 r--s 00000000 08:01 3851184    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4bdc000-b4bdf000 r--s 00000000 08:01 3851792    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-le32d4.cache-3
b4bdf000-b4be7000 r--s 00000000 08:01 3851791    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-le32d4.cache-3
b4be7000-b4bf2000 r--s 00000000 08:01 3851021    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4bf2000-b4bf5000 r--s 00000000 08:01 3851789    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4bf5000-b4bf7000 r--s 00000000 08:01 3851788    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b4bf7000-b4bf8000 r--s 00000000 08:01 3851395    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4bf8000-b4c1a000 r--s 00000000 08:01 3851786    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b4c1a000-b4c1d000 r--s 00000000 08:01 3851785    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b4c1d000-b4c25000 r--s 00000000 08:01 3851784    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4c25000-b4c2e000 r--s 00000000 08:01 3851783    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-le32d4.cache-3
b4c2e000-b4c30000 r--s 00000000 08:01 3850831    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4c30000-b4c35000 r--s 00000000 08:01 3850967    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4c35000-b4c36000 r--p 00000000 00:00 0 
b4c36000-b4c39000 ---p 00000000 00:00 0 
b4c39000-b4c87000 rw-p 00000000 00:00 0 
b4c87000-b4c8a000 ---p 00000000 00:00 0 
b4c8a000-b4cd8000 rw-p 00000000 00:00 0 
b4cd8000-b4cd9000 r--s 00000000 08:01 3850974    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4cd9000-b4cda000 r--s 00000000 08:01 3851806    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4cda000-b4ce0000 r--s 00000000 08:01 3850308    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4ce0000-b4ce2000 r--s 00000000 08:01 3851804    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4ce2000-b4ce4000 r--s 00000000 08:01 3851803    /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-le32d4.cache-3
b4ce4000-b4ce7000 r--s 00000000 08:01 3851802    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4ce7000-b4ced000 r--s 00000000 08:01 3850975    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4ced000-b4cee000 r--s 00000000 08:01 3851800    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4cee000-b4cf0000 r--s 00000000 08:01 3851799    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-le32d4.cache-3
b4cf0000-b4cf3000 r--s 00000000 08:01 3851798    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4cf3000-b4cf4000 r--s 00000000 08:01 3851797    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4cf4000-b4cf5000 r--s 00000000 08:01 3851796    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4cf5000-b4cf6000 r--s 00000000 08:01 3851795    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4cf6000-b4cfa000 r--s 00000000 08:01 3851794    /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-le32d4.cache-3
b4cfa000-b4cfe000 r--s 00000000 08:01 3851793    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4cfe000-b4d02000 r--s 00000000 08:01 3851008    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4d02000-b4d09000 r--s 00000000 08:01 3851184    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4d09000-b4d0c000 r--s 00000000 08:01 3851792    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-le32d4.cache-3
b4d0c000-b4d14000 r--s 00000000 08:01 3851791    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-le32d4.cache-3
b4d14000-b4d1f000 r--s 00000000 08:01 3851021    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4d1f000-b4d22000 r--s 00000000 08:01 3851789    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4d22000-b4d24000 r--s 00000000 08:01 3851788    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b4d24000-b4d25000 r--s 00000000 08:01 3851395    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4d25000-b4d47000 r--s 00000000 08:01 3851786    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b4d47000-b4d4a000 r--s 00000000 08:01 3851785    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b4d4a000-b4d52000 r--s 00000000 08:01 3851784    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4d52000-b4d5b000 r--s 00000000 08:01 3851783    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-le32d4.cache-3
b4d5b000-b4d5d000 r--s 00000000 08:01 3850831    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4d5d000-b4d62000 r--s 00000000 08:01 3850967    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4d62000-b4d63000 r--s 00000000 08:01 3850974    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b4d63000-b4d64000 r--s 00000000 08:01 3851806    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b4d64000-b4d6a000 r--s 00000000 08:01 3850308    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b4d6a000-b4d6c000 r--s 00000000 08:01 3851804    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b4d6c000-b4d6e000 r--s 00000000 08:01 3851803    /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-le32d4.cache-3
b4d6e000-b4d71000 r--s 00000000 08:01 3851802    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b4d71000-b4d77000 r--s 00000000 08:01 3850975    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b4d77000-b4d78000 r--s 00000000 08:01 3851800    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b4d78000-b4d7a000 r--s 00000000 08:01 3851799    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-le32d4.cache-3
b4d7a000-b4d7d000 r--s 00000000 08:01 3851798    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b4d7d000-b4d7e000 r--s 00000000 08:01 3851797    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4d7e000-b4d82000 r--s 00000000 08:01 3851794    /var/cache/fontconfig/062808c12e6e608270f93bb230aed730-le32d4.cache-3
b4d82000-b4d86000 r--s 00000000 08:01 3851793    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4d86000-b4d8a000 r--s 00000000 08:01 3851008    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4d8a000-b4d91000 r--s 00000000 08:01 3851184    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4d91000-b4d94000 r--s 00000000 08:01 3851792    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-le32d4.cache-3
b4d94000-b4d9c000 r--s 00000000 08:01 3851791    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-le32d4.cache-3
b4d9c000-b4da7000 r--s 00000000 08:01 3851021    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4da7000-b4daa000 r--s 00000000 08:01 3851789    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4daa000-b4dcc000 r--s 00000000 08:01 3851786    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b4dcc000-b4dd4000 r--s 00000000 08:01 3851784    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4dd4000-b4ddd000 r--s 00000000 08:01 3851783    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-le32d4.cache-3
b4ddd000-b4de0000 ---p 00000000 00:00 0 
b4de0000-b4e2e000 rw-p 00000000 00:00 0 
b4e2e000-b4e2f000 ---p 00000000 00:00 0 
b4e2f000-b4eaf000 rw-p 00000000 00:00 0 
b4eaf000-b4eb2000 ---p 00000000 00:00 0 
b4eb2000-b4f00000 rw-p 00000000 00:00 0 
b4f00000-b4fce000 rw-p 00000000 00:00 0 
b4fce000-b5000000 ---p 00000000 00:00 0 
b5000000-b5001000 r--s 00000000 08:01 3851796    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b5001000-b5002000 r--s 00000000 08:01 3851795    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b5002000-b5004000 r--s 00000000 08:01 3851788    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b5004000-b5007000 r--s 00000000 08:01 3851785    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b5007000-b5009000 r--s 00000000 08:01 3850831    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b5009000-b500e000 r--s 00000000 08:01 3850967    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b500e000-b5014000 r--s 000fc000 08:01 5644661    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b5014000-b501d000 r--s 00065000 08:01 1540114    /usr/share/java/gnome-java-bridge.jar
b501d000-b5020000 ---p 00000000 00:00 0 
b5020000-b509e000 rw-p 00000000 00:00 0 
b509e000-b50a1000 ---p 00000000 00:00 0 
b50a1000-b50ef000 rw-p 00000000 00:00 0 
b50ef000-b50f6000 r--s 00000000 08:01 2580970    /usr/lib/gconv/gconv-modules.cache
b50f6000-b5135000 r--p 00000000 08:01 5448361    /usr/lib/locale/en_US.utf8/LC_CTYPE
b5135000-b5138000 ---p 00000000 00:00 0 
b5138000-b5186000 rw-p 00000000 00:00 0 
b5186000-b5189000 ---p 00000000 00:00 0 
b5189000-b51d7000 rw-p 00000000 00:00 0 
b51d7000-b51d8000 ---p 00000000 00:00 0 
b51d8000-b5258000 rw-p 00000000 00:00 0 
b5258000-b525a000 r--s 0001d000 08:01 5644660    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b525a000-b525f000 r--s 00045000 08:01 5644658    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b525f000-b5292000 rw-p 00000000 00:00 0 
b5292000-b5422000 r--s 038c5000 08:01 5644836    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b5422000-b5429000 rw-p 00000000 00:00 0 
b5429000-b5443000 rw-p 00000000 00:00 0 
b5443000-b544d000 rw-p 00000000 00:00 0 
b544d000-b54ee000 rw-p 00000000 00:00 0 
b54ee000-b54f3000 rw-p 00000000 00:00 0 
b54f3000-b5543000 rw-p 00000000 00:00 0 
b5543000-b554d000 rw-p 00000000 00:00 0 
b554d000-b55ee000 rw-p 00000000 00:00 0 
b55ee000-b55f4000 rw-p 00000000 00:00 0 
b55f4000-b560e000 rw-p 00000000 00:00 0 
b560e000-b5624000 rw-p 00000000 00:00 0 
b5624000-b569a000 rw-p 00000000 00:00 0 
b569a000-b58e2000 rwxp 00000000 00:00 0 
b58e2000-b769a000 rw-p 00000000 00:00 0 
b769a000-b769d000 ---p 00000000 00:00 0 
b769d000-b76ee000 rw-p 00000000 00:00 0 
b76ee000-b76ef000 r--s 00000000 08:01 3851395    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b76ef000-b76f2000 r--s 0000f000 08:01 5644560    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b76f2000-b76f4000 r--s 00016000 08:01 4071554    /home/manij/minecraft.jar
b76f4000-b7701000 rw-p 00000000 00:00 0 
b7701000-b7709000 rw-s 00000000 08:01 4071560    /tmp/hsperfdata_manij/8095
b7709000-b770a000 rw-p 00000000 00:00 0 
b770a000-b770b000 r--p 00000000 00:00 0 
b770b000-b770d000 rw-p 00000000 00:00 0 
bfb91000-bfbc7000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/manij/minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/opt/kde3/bin:/opt/kde3/games:/opt/kde3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca40], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 4096, AS infinity
load average:0.93 0.46 0.34

/proc/meminfo:
MemTotal:        1801184 kB
MemFree:          103472 kB
Buffers:          189644 kB
Cached:           712716 kB
SwapCached:         4044 kB
Active:           848848 kB
Inactive:         691292 kB
Active(anon):     315196 kB
Inactive(anon):   337368 kB
Active(file):     533652 kB
Inactive(file):   353924 kB
Unevictable:        8452 kB
Mlocked:               0 kB
HighTotal:        924096 kB
HighFree:           1468 kB
LowTotal:         877088 kB
LowFree:          102004 kB
SwapTotal:       6217136 kB
SwapFree:        6201052 kB
Dirty:              6872 kB
Writeback:             0 kB
AnonPages:        643008 kB
Mapped:           145980 kB
Shmem:              6332 kB
Slab:             100136 kB
SReclaimable:      89536 kB
SUnreclaim:        10600 kB
KernelStack:        2816 kB
PageTables:         7720 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7117728 kB
Committed_AS:    1796592 kB
VmallocTotal:     122880 kB
VmallocUsed:       25020 kB
VmallocChunk:      92268 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 16 model 6 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, popcnt, mmxext, 3dnow, 3dnowext, lzcnt, sse4a

Memory: 4k page, physical 1801184k(103472k free), swap 6217136k(6201052k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 17 2012 07:30:23 by "buildd" with gcc 4.4.3

time: Fri Mar 16 19:44:05 2012
elapsed time: 45 seconds


```

---

### Post by regor210 on 2012-03-17
Looks like your ATI video drivers may be the problem.

 Run these in a terminal minus the $ 

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install mesa-utils


Now run these in terminal and post what you get.
video driver 3D test FPS

$ glxgears

video card and driver information

$ lspci -vmk | grep -A 8 -B 2 VGA

System information 
$ uname -a
$ lsb_release -a

Here's a thread with a similar issue. 
[http://ubuntuforums.org/showthread.php?t=1639074](http://ubuntuforums.org/showthread.php?t=1639074)

---

### Post by cloverasx on 2012-03-18
Sorry if I'm a little off topic on your post, but I'm trying to increase the java heap for minecraft (with the code: java -Xms512M -Xmx1024M -cp Minecraft.jar net.minecraft.launcher) and I receive the error "can't find the main class..."

I'm very new to ubuntu (any linux for that matter) so if you could explain with slight background, it would be appreciated. Thanks!

---

### Post by regor210 on 2012-03-18
Like this > minecraft.jar not Minrcraft.jar

$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame


working on the proper syntax here
[http://ubuntuforums.org/showthread.php?t=1942072](http://ubuntuforums.org/showthread.php?t=1942072)

---

### Post by cloverasx on 2012-03-18
Thank you for the help, but I am still having the same problem; this is what I put in/received:

cloverasx@ubuntu:~$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

Any ideas?

---

### Post by cloverasx on 2012-03-18
holy eff. Sorry, I moved the minecraft.jar folder from the desktop to home and it worked... Well, I learned something today. Thanks for the help

---

