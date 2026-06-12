---
title: "runescape+arch=white screen"
date: 2008-12-18
forum: General Help
---

### Post by doorknob60 on 2008-12-18
Well, I get a white screen whenever I try to play RS now. I tried the beta 64 bit plugin (that worked a couple days ago) and the 32 bit Plugin I used to use. Both show the loading screen fine, then it just turns to a white box that fills most of the browser. No terminal output either. I tried Firefox, Seamonkey, and Konqueror. Same thing pretty much (the screen was black in Konqueror). Also, Funorb (another Java games site) works fine. I tried holding down s for the RS safe mode option but it doesn't do anything. The only thing I've messed with on my system since it last worked was graphics stuff (might have worked after that too though). I was experimenting with fglrx to see how it progressed using my integrated ATI card (wasn't at all satisfied FYI) and then I removed all the drivers etc I installed and reinstalled Nvidia and put my card back. OpenGL works fine for everything and everything except RS works as well as it did before I messed with it, and as far as I know everything's the same. I looked for extra packages that were installed that could be conflicting but I can't find anything...any ideas? Even weirder, it works as good as it used to in OpenJDK (but that has sound problems, so it's only a temporary solution I hope)

Pic: [http://i43.tinypic.com/2znvpd2.png]("http://i43.tinypic.com/2znvpd2.png")

I know this is in Arch but it's still Linux so there could be a universal solution :-)

EDIT: Found an error log:
```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f1989f592a2, pid=7202, tid=139747394877776
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (11.2-b01 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5802a2]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x000000004080cc00):  JavaThread "CompilerThread0" daemon [_thread_in_native, id=7214, stack(0x00007f1979c47000,0x00007f1979d48000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x0000000000000008

Registers:
RAX=0x0000000041555810, RBX=0x0000000000000000, RCX=0x00007f198a1b3a20, RDX=0x0000000041555830
RSP=0x00007f1979d414f0, RBP=0x00007f1979d41620, RSI=0x0000000000000020, RDI=0x00007f1979d463f8
R8 =0x00007f1979d46330, R9 =0x000000007fffffff, R10=0x0000000041bbb2b0, R11=0x00000000000037b4
R12=0x0000000000000000, R13=0x0000000041555650, R14=0x0000000040e9d080, R15=0x00007f1979d416c0
RIP=0x00007f1989f592a2, EFL=0x0000000000010202, CSGSFS=0x0000000000000033, ERR=0x0000000000000004
  TRAPNO=0x000000000000000e

Top of Stack: (sp=0x00007f1979d414f0)
0x00007f1979d414f0:   00007f1979d417a8 00007f1979d417a0
0x00007f1979d41500:   00007f1979d41830 00007f1979d41750
0x00007f1979d41510:   00007f1979d415b0 00007f1979d41738
0x00007f1979d41520:   000000010101a961 00000000415557b0
0x00007f1979d41530:   0000000041555630 0000000040e2b360
0x00007f1979d41540:   ffffffff00000000 00000000415557b0
0x00007f1979d41550:   0000000000000000 0000000041555770
0x00007f1979d41560:   0000000141922780 0000000040e2b360
0x00007f1979d41570:   00000000410c3ad0 00007f1979d416c0
0x00007f1979d41580:   00000000410c3878 00000000410c3878
0x00007f1979d41590:   0000027800000000 0000000000000000
0x00007f1979d415a0:   0000004000000000 0000000040e2a960
0x00007f1979d415b0:   0000000040e9d080 00007f1979d416c0
0x00007f1979d415c0:   00000000410c3878 00000000410c3878
0x00007f1979d415d0:   0000027800000000 0000000000000000
0x00007f1979d415e0:   0000000000000000 0000000000000007
0x00007f1979d415f0:   00007f1979d416c0 00007f198a19e7d0
0x00007f1979d41600:   0000000040e2a960 00000000412fb590
0x00007f1979d41610:   00007f1979d416c0 00007f1979d416d8
0x00007f1979d41620:   00007f1979d41660 00007f1989f57c80
0x00007f1979d41630:   0000000000000000 0000000040e56840
0x00007f1979d41640:   00007f1979d416c0 00007f1979d419d0
0x00007f1979d41650:   0000000000000001 00007f1979d41880
0x00007f1979d41660:   00007f1979d41940 00007f1989e5aff5
0x00007f1979d41670:   00007f1974781b10 00007f1979d418b0
0x00007f1979d41680:   0000000000000000 0000000000000000
0x00007f1979d41690:   00007f1979d418f0 00007f1979d42378
0x00007f1979d416a0:   00007f1979d42358 01007f197478ca80
0x00007f1979d416b0:   0000000000000000 00007f1979d44c90
0x00007f1979d416c0:   00007f1979d419d0 00007f1979d463f8
0x00007f1979d416d0:   00007f1979d44c90 0000002000000000
0x00007f1979d416e0:   00007f1979d463f8 0000000041555530 

Instructions: (pc=0x00007f1989f592a2)
0x00007f1989f59292:   da be 20 00 00 00 e8 e3 18 c5 ff 48 85 c0 74 2d
0x00007f1989f592a2:   49 8b 54 24 08 49 8b 7d 10 4c 89 60 08 4c 89 28 

Stack: [0x00007f1979c47000,0x00007f1979d48000],  sp=0x00007f1979d414f0,  free space=1001k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x5802a2]
V  [libjvm.so+0x57ec80]
V  [libjvm.so+0x481ff5]
V  [libjvm.so+0x2411e2]
V  [libjvm.so+0x23e2a4]
V  [libjvm.so+0x1ddf87]
V  [libjvm.so+0x2461d8]
V  [libjvm.so+0x245b76]
V  [libjvm.so+0x5c45b9]
V  [libjvm.so+0x5be4c1]
V  [libjvm.so+0x4e310a]


Current CompileTask:
C2:279  !   cf.<init>([B)V (2712 bytes)


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0000000040fe9000 JavaThread "Thread-15" daemon [_thread_blocked, id=7251, stack(0x00007f1971742000,0x00007f1971843000)]
  0x00007f197419a400 JavaThread "Headspace mixer frame proc thread" daemon [_thread_blocked, id=7250, stack(0x00007f1971843000,0x00007f1971944000)]
  0x00007f19740a1400 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=7249, stack(0x00007f19726fc000,0x00007f19727fd000)]
  0x0000000040b71000 JavaThread "Thread-13" daemon [_thread_blocked, id=7248, stack(0x00007f19721f2000,0x00007f19722f3000)]
  0x0000000040babc00 JavaThread "Thread-12" daemon [_thread_blocked, id=7247, stack(0x00007f19725fb000,0x00007f19726fc000)]
  0x0000000040c19800 JavaThread "Thread-11" daemon [_thread_in_Java, id=7246, stack(0x00007f1972c1a000,0x00007f1972d1b000)]
  0x0000000040b73000 JavaThread "Thread-10" daemon [_thread_blocked, id=7243, stack(0x00007f19722f3000,0x00007f19723f4000)]
  0x0000000040964800 JavaThread "thread applet-loader.class-1" [_thread_blocked, id=7239, stack(0x00007f1972d1b000,0x00007f1972e1c000)]
  0x0000000040ac7800 JavaThread "AWT-EventQueue-2" [_thread_blocked, id=7238, stack(0x00007f1972e1c000,0x00007f1972f1d000)]
  0x0000000040ac7000 JavaThread "Applet 1 LiveConnect Worker Thread" [_thread_blocked, id=7237, stack(0x00007f1973ce3000,0x00007f1973de4000)]
  0x00000000408bb400 JavaThread "Browser Side Object Cleanup Thread" [_thread_blocked, id=7234, stack(0x00007f19792d2000,0x00007f19793d3000)]
  0x00007f197407e800 JavaThread "AWT-EventQueue-1" [_thread_blocked, id=7233, stack(0x00007f1972f1d000,0x00007f197301e000)]
  0x00007f197407e000 JavaThread "AWT-Shutdown" [_thread_blocked, id=7232, stack(0x00007f1973ae1000,0x00007f1973be2000)]
  0x00007f197407c400 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=7231, stack(0x00007f197301e000,0x00007f197311f000)]
  0x00007f1974036400 JavaThread "CacheCleanUpThread" daemon [_thread_blocked, id=7230, stack(0x00007f1973637000,0x00007f1973738000)]
  0x00007f1974034c00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=7229, stack(0x00007f1973738000,0x00007f1973839000)]
  0x00007f1974032c00 JavaThread "CacheMemoryCleanUpThread" daemon [_thread_blocked, id=7228, stack(0x00007f1973839000,0x00007f197393a000)]
  0x0000000040966c00 JavaThread "Java Plug-In Heartbeat Thread" [_thread_blocked, id=7224, stack(0x00007f1973be2000,0x00007f1973ce3000)]
  0x00000000407f7c00 JavaThread "Java Plug-In Pipe Worker Thread (Client-Side)" daemon [_thread_in_native, id=7222, stack(0x00007f19791d1000,0x00007f19792d2000)]
  0x0000000040840400 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=7219, stack(0x00007f19793d3000,0x00007f19794d4000)]
  0x000000004082a000 JavaThread "Timer-0" [_thread_blocked, id=7218, stack(0x00007f19796f3000,0x00007f19797f4000)]
  0x0000000040813400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=7216, stack(0x00007f1979a45000,0x00007f1979b46000)]
  0x000000004080f400 JavaThread "CompilerThread1" daemon [_thread_in_native, id=7215, stack(0x00007f1979b46000,0x00007f1979c47000)]
=>0x000000004080cc00 JavaThread "CompilerThread0" daemon [_thread_in_native, id=7214, stack(0x00007f1979c47000,0x00007f1979d48000)]
  0x000000004080ac00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=7213, stack(0x00007f1979d48000,0x00007f1979e49000)]
  0x00000000407ec800 JavaThread "Finalizer" daemon [_thread_blocked, id=7212, stack(0x00007f1979fc7000,0x00007f197a0c8000)]
  0x00000000407e5800 JavaThread "Reference Handler" daemon [_thread_blocked, id=7211, stack(0x00007f197a0c8000,0x00007f197a1c9000)]
  0x000000004077f000 JavaThread "main" [_thread_blocked, id=7207, stack(0x00007f1989655000,0x00007f1989756000)]

Other Threads:
  0x00000000407dd000 VMThread [stack: 0x00007f197a1c9000,0x00007f197a2ca000] [id=7210]
  0x0000000040815c00 WatcherThread [stack: 0x00007f1979944000,0x00007f1979a45000] [id=7217]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 25920K, used 18700K [0x00007f1983bc0000, 0x00007f1985bc0000, 0x00007f1985bc0000)
  eden space 19072K, 79% used [0x00007f1983bc0000,0x00007f1984a9a7b8,0x00007f1984e60000)
  from space 6848K, 50% used [0x00007f1984e60000,0x00007f19851c89c0,0x00007f1985510000)
  to   space 6656K, 0% used [0x00007f1985540000,0x00007f1985540000,0x00007f1985bc0000)
 PSOldGen        total 22784K, used 12774K [0x00007f197fbc0000, 0x00007f1981200000, 0x00007f1983bc0000)
  object space 22784K, 56% used [0x00007f197fbc0000,0x00007f1980839bf0,0x00007f1981200000)
 PSPermGen       total 37376K, used 19933K [0x00007f197a7c0000, 0x00007f197cc40000, 0x00007f197fbc0000)
  object space 37376K, 53% used [0x00007f197a7c0000,0x00007f197bb375e0,0x00007f197cc40000)

Dynamic libraries:
40000000-40009000 r-xp 00000000 08:03 670454                             /opt/jre1.6.0_12/bin/java
40108000-4010a000 rwxp 00008000 08:03 670454                             /opt/jre1.6.0_12/bin/java
40778000-425ee000 rwxp 40778000 00:00 0                                  [heap]
7f19715ca000-7f1971742000 rwxs 00000000 00:08 10518537                   /SYSV00000000 (deleted)
7f1971742000-7f1971745000 ---p 7f1971742000 00:00 0 
7f1971745000-7f1971843000 rwxp 7f1971745000 00:00 0 
7f1971843000-7f1971846000 ---p 7f1971843000 00:00 0 
7f1971846000-7f1971944000 rwxp 7f1971846000 00:00 0 
7f1971944000-7f1971959000 r-xs 00000000 08:03 631263                     /var/cache/fontconfig/8d4af663993b81a124ee82e610bb31f9-x86-64.cache-2
7f1971959000-7f1971960000 r-xs 00000000 08:03 630547                     /var/cache/fontconfig/a98d8961fa319a64d3cfd8640c79e62d-x86-64.cache-2
7f1971960000-7f1971968000 r-xs 00000000 08:03 631261                     /var/cache/fontconfig/d62e99ef547d1d24cdb1bd22ec1a2976-x86-64.cache-2
7f1971968000-7f1971993000 r-xs 00000000 08:03 631260                     /var/cache/fontconfig/f6b893a7224233d96cb72fd88691c0b4-x86-64.cache-2
7f1971993000-7f19719ef000 r-xs 00000000 08:03 631259                     /var/cache/fontconfig/17090aa38d5c6f09fb8c5c354938f1d7-x86-64.cache-2
7f1971aab000-7f1971b88000 r-xp 00000000 08:03 192771                     /usr/lib/libasound.so.2.0.0
7f1971b88000-7f1971d88000 ---p 000dd000 08:03 192771                     /usr/lib/libasound.so.2.0.0
7f1971d88000-7f1971d90000 rwxp 000dd000 08:03 192771                     /usr/lib/libasound.so.2.0.0
7f1971d90000-7f1971d9e000 r-xp 00000000 08:03 671048                     /opt/jre1.6.0_12/lib/amd64/libjsoundalsa.so
7f1971d9e000-7f1971e9d000 ---p 0000e000 08:03 671048                     /opt/jre1.6.0_12/lib/amd64/libjsoundalsa.so
7f1971e9d000-7f1971ea0000 rwxp 0000d000 08:03 671048                     /opt/jre1.6.0_12/lib/amd64/libjsoundalsa.so
7f1971ea0000-7f1971eb7000 r-xp 00000000 08:03 671016                     /opt/jre1.6.0_12/lib/amd64/libunpack.so
7f1971eb7000-7f1971fb6000 ---p 00017000 08:03 671016                     /opt/jre1.6.0_12/lib/amd64/libunpack.so
7f1971fb6000-7f1971fbb000 rwxp 00016000 08:03 671016                     /opt/jre1.6.0_12/lib/amd64/libunpack.so
7f1971fbb000-7f1971fcb000 rwxp 7f1971fbb000 00:00 0 
7f19720bc000-7f19720e8000 r-xp 00000000 08:03 671027                     /opt/jre1.6.0_12/lib/amd64/libjsound.so
7f19720e8000-7f19721e8000 ---p 0002c000 08:03 671027                     /opt/jre1.6.0_12/lib/amd64/libjsound.so
7f19721e8000-7f19721f0000 rwxp 0002c000 08:03 671027                     /opt/jre1.6.0_12/lib/amd64/libjsound.so
7f19721f0000-7f19721f2000 rwxp 7f19721f0000 00:00 0 
7f19721f2000-7f19721f5000 ---p 7f19721f2000 00:00 0 
7f19721f5000-7f19722f3000 rwxp 7f19721f5000 00:00 0 
7f19722f3000-7f19722f6000 ---p 7f19722f3000 00:00 0 
7f19722f6000-7f19723f4000 rwxp 7f19722f6000 00:00 0 
7f19723f4000-7f19723fb000 r-xp 00000000 08:03 192266                     /usr/lib/libXrandr.so.2.1.0
7f19723fb000-7f19725fa000 ---p 00007000 08:03 192266                     /usr/lib/libXrandr.so.2.1.0
7f19725fa000-7f19725fb000 rwxp 00006000 08:03 192266                     /usr/lib/libXrandr.so.2.1.0
7f19725fb000-7f19725fe000 ---p 7f19725fb000 00:00 0 
7f19725fe000-7f19726fc000 rwxp 7f19725fe000 00:00 0 
7f19726fc000-7f19726ff000 ---p 7f19726fc000 00:00 0 
7f19726ff000-7f19727fd000 rwxp 7f19726ff000 00:00 0 
7f19727fd000-7f1972810000 r-xp 00000000 08:03 652845                     /lib/libresolv-2.9.so
7f1972810000-7f1972a10000 ---p 00013000 08:03 652845                     /lib/libresolv-2.9.so
7f1972a10000-7f1972a11000 r-xp 00013000 08:03 652845                     /lib/libresolv-2.9.so
7f1972a11000-7f1972a12000 rwxp 00014000 08:03 652845                     /lib/libresolv-2.9.so
7f1972a12000-7f1972a14000 rwxp 7f1972a12000 00:00 0 
7f1972a14000-7f1972a19000 r-xp 00000000 08:03 652846                     /lib/libnss_dns-2.9.so
7f1972a19000-7f1972c18000 ---p 00005000 08:03 652846                     /lib/libnss_dns-2.9.so
7f1972c18000-7f1972c19000 r-xp 00004000 08:03 652846                     /lib/libnss_dns-2.9.so
7f1972c19000-7f1972c1a000 rwxp 00005000 08:03 652846                     /lib/libnss_dns-2.9.so
7f1972c1a000-7f1972c1d000 ---p 7f1972c1a000 00:00 0 
7f1972c1d000-7f1972d1b000 rwxp 7f1972c1d000 00:00 0 
7f1972d1b000-7f1972d1e000 ---p 7f1972d1b000 00:00 0 
7f1972d1e000-7f1972e1c000 rwxp 7f1972d1e000 00:00 0 
7f1972e1c000-7f1972e1f000 ---p 7f1972e1c000 00:00 0 
7f1972e1f000-7f1972f1d000 rwxp 7f1972e1f000 00:00 0 
7f1972f1d000-7f1972f20000 ---p 7f1972f1d000 00:00 0 
7f1972f20000-7f197301e000 rwxp 7f1972f20000 00:00 0 
7f197301e000-7f1973021000 ---p 7f197301e000 00:00 0 
7f1973021000-7f197311f000 rwxp 7f1973021000 00:00 0 
7f197311f000-7f1973124000 r-xp 00000000 08:03 192360                     /usr/lib/libXfixes.so.3.1.0
7f1973124000-7f1973223000 ---p 00005000 08:03 192360                     /usr/lib/libXfixes.so.3.1.0
7f1973223000-7f1973224000 rwxp 00004000 08:03 192360                     /usr/lib/libXfixes.so.3.1.0
7f1973224000-7f197322d000 r-xp 00000000 08:03 192263                     /usr/lib/libXrender.so.1.3.0
7f197322d000-7f197342c000 ---p 00009000 08:03 192263                     /usr/lib/libXrender.so.1.3.0
7f197342c000-7f197342d000 rwxp 00008000 08:03 192263                     /usr/lib/libXrender.so.1.3.0
7f197342d000-7f1973436000 r-xp 00000000 08:03 192398                     /usr/lib/libXcursor.so.1.0.2
7f1973436000-7f1973636000 ---p 00009000 08:03 192398                     /usr/lib/libXcursor.so.1.0.2
7f1973636000-7f1973637000 rwxp 00009000 08:03 192398                     /usr/lib/libXcursor.so.1.0.2
7f1973637000-7f197363a000 ---p 7f1973637000 00:00 0 
7f197363a000-7f1973738000 rwxp 7f197363a000 00:00 0 
7f1973738000-7f197373b000 ---p 7f1973738000 00:00 0 
7f197373b000-7f1973839000 rwxp 7f197373b000 00:00 0 
7f1973839000-7f197383c000 ---p 7f1973839000 00:00 0 
7f197383c000-7f197393a000 rwxp 7f197383c000 00:00 0 
7f197393a000-7f19739b8000 r-xp 00000000 08:03 671019                     /opt/jre1.6.0_12/lib/amd64/libfontmanager.so
7f19739b8000-7f1973aba000 ---p 0007e000 08:03 671019                     /opt/jre1.6.0_12/lib/amd64/libfontmanager.so
7f1973aba000-7f1973ad0000 rwxp 00080000 08:03 671019                     /opt/jre1.6.0_12/lib/amd64/libfontmanager.so
7f1973ad0000-7f1973ae1000 rwxp 7f1973ad0000 00:00 0 
7f1973ae1000-7f1973ae4000 ---p 7f1973ae1000 00:00 0 
7f1973ae4000-7f1973be2000 rwxp 7f1973ae4000 00:00 0 
7f1973be2000-7f1973be5000 ---p 7f1973be2000 00:00 0 
7f1973be5000-7f1973ce3000 rwxp 7f1973be5000 00:00 0 
7f1973ce3000-7f1973ce6000 ---p 7f1973ce3000 00:00 0 
7f1973ce6000-7f1973de4000 rwxp 7f1973ce6000 00:00 0 
7f1973de4000-7f1973dff000 r-xp 00000000 08:03 191802                     /usr/lib/libxcb.so.1.0.0
7f1973dff000-7f1973fff000 ---p 0001b000 08:03 191802                     /usr/lib/libxcb.so.1.0.0
7f1973fff000-7f1974000000 rwxp 0001b000 08:03 191802                     /usr/lib/libxcb.so.1.0.0
7f1974000000-7f1975618000 rwxp 7f1974000000 00:00 0 
7f1975618000-7f1978000000 ---p 7f1975618000 00:00 0 
7f197800c000-7f1978068000 r-xs 00000000 08:03 631215                     /var/cache/fontconfig/df311e82a1a24c41a75c2c930223552e-x86-64.cache-2
7f1978068000-7f197806d000 r-xp 00000000 08:03 190226                     /usr/lib/libXdmcp.so.6.0.0
7f197806d000-7f197816c000 ---p 00005000 08:03 190226                     /usr/lib/libXdmcp.so.6.0.0
7f197816c000-7f197816d000 rwxp 00004000 08:03 190226                     /usr/lib/libXdmcp.so.6.0.0
7f197816d000-7f197816e000 r-xp 00000000 08:03 191858                     /usr/lib/libxcb-xlib.so.0.0.0
7f197816e000-7f197836d000 ---p 00001000 08:03 191858                     /usr/lib/libxcb-xlib.so.0.0.0
7f197836d000-7f197836e000 rwxp 00000000 08:03 191858                     /usr/lib/libxcb-xlib.so.0.0.0
7f197836e000-7f1978370000 r-xp 00000000 08:03 190231                     /usr/lib/libXau.so.6.0.0
7f1978370000-7f197856f000 ---p 00002000 08:03 190231                     /usr/lib/libXau.so.6.0.0
7f197856f000-7f1978570000 rwxp 00001000 08:03 190231                     /usr/lib/libXau.so.6.0.0
7f1978570000-7f1978579000 r-xp 00000000 08:03 190297                     /usr/lib/libXi.so.6.0.0
7f1978579000-7f1978778000 ---p 00009000 08:03 190297                     /usr/lib/libXi.so.6.0.0
7f1978778000-7f1978779000 rwxp 00008000 08:03 190297                     /usr/lib/libXi.so.6.0.0
7f1978779000-7f197877e000 r-xp 00000000 08:03 192318                     /usr/lib/libXtst.so.6.1.0
7f197877e000-7f197897d000 ---p 00005000 08:03 192318                     /usr/lib/libXtst.so.6.1.0
7f197897d000-7f197897e000 rwxp 00004000 08:03 192318                     /usr/lib/libXtst.so.6.1.0
7f197897e000-7f1978a84000 r-xp 00000000 08:03 191865                     /usr/lib/libX11.so.6.2.0
7f1978a84000-7f1978c84000 ---p 00106000 08:03 191865                     /usr/lib/libX11.so.6.2.0
7f1978c84000-7f1978c8a000 rwxp 00106000 08:03 191865                     /usr/lib/libX11.so.6.2.0
7f1978c8a000-7f1978c9a000 r-xp 00000000 08:03 192154                     /usr/lib/libXext.so.6.4.0
7f1978c9a000-7f1978e9a000 ---p 00010000 08:03 192154                     /usr/lib/libXext.so.6.4.0
7f1978e9a000-7f1978e9b000 rwxp 00010000 08:03 192154                     /usr/lib/libXext.so.6.4.0
7f1978eba000-7f1978efb000 r-xp 00000000 08:03 671045                     /opt/jre1.6.0_12/lib/amd64/xawt/libmawt.so
7f1978efb000-7f1978ffa000 ---p 00041000 08:03 671045                     /opt/jre1.6.0_12/lib/amd64/xawt/libmawt.so
7f1978ffa000-7f1979006000 rwxp 00040000 08:03 671045                     /opt/jre1.6.0_12/lib/amd64/xawt/libmawt.so
7f1979006000-7f1979007000 rwxp 7f1979006000 00:00 0 
7f1979007000-7f1979094000 r-xp 00000000 08:03 671020                     /opt/jre1.6.0_12/lib/amd64/libawt.so
7f1979094000-7f1979193000 ---p 0008d000 08:03 671020                     /opt/jre1.6.0_12/lib/amd64/libawt.so
7f1979193000-7f19791ac000 rwxp 0008c000 08:03 671020                     /opt/jre1.6.0_12/lib/amd64/libawt.so
7f19791ac000-7f19791d1000 rwxp 7f19791ac000 00:00 0 
7f19791d1000-7f19791d4000 ---p 7f19791d1000 00:00 0 
7f19791d4000-7f19792d2000 rwxp 7f19791d4000 00:00 0 
7f19792d2000-7f19792d5000 ---p 7f19792d2000 00:00 0 
7f19792d5000-7f19793d3000 rwxp 7f19792d5000 00:00 0 
7f19793d3000-7f19793d6000 ---p 7f19793d3000 00:00 0 
7f19793d6000-7f19794d4000 rwxp 7f19793d6000 00:00 0 
7f19794d4000-7f19794db000 r-xp 00000000 08:03 671033                     /opt/jre1.6.0_12/lib/amd64/libnio.so
7f19794db000-7f19795da000 ---p 00007000 08:03 671033                     /opt/jre1.6.0_12/lib/amd64/libnio.so
7f19795da000-7f19795dc000 rwxp 00006000 08:03 671033                     /opt/jre1.6.0_12/lib/amd64/libnio.so
7f19795dc000-7f19795ef000 r-xp 00000000 08:03 671035                     /opt/jre1.6.0_12/lib/amd64/libnet.so
7f19795ef000-7f19796f0000 ---p 00013000 08:03 671035                     /opt/jre1.6.0_12/lib/amd64/libnet.so
7f19796f0000-7f19796f3000 rwxp 00014000 08:03 671035                     /opt/jre1.6.0_12/lib/amd64/libnet.so
7f19796f3000-7f19796f6000 ---p 7f19796f3000 00:00 0 
7f19796f6000-7f19797f4000 rwxp 7f19796f6000 00:00 0 
7f19797f4000-7f1979807000 r-xp 00000000 08:03 671032                     /opt/jre1.6.0_12/lib/amd64/libdeploy.so
7f1979807000-7f1979908000 ---p 00013000 08:03 671032                     /opt/jre1.6.0_12/lib/amd64/libdeploy.so
7f1979908000-7f197990c000 rwxp 00014000 08:03 671032                     /opt/jre1.6.0_12/lib/amd64/libdeploy.so
7f197990c000-7f197991c000 rwxp 7f197990c000 00:00 0 
7f197991c000-7f197992d000 r-xs 00173000 08:03 670529                     /opt/jre1.6.0_12/lib/plugin.jar
7f197992d000-7f1979935000 r-xs 000a4000 08:03 671153                     /opt/jre1.6.0_12/lib/javaws.jar
7f1979935000-7f1979944000 r-xs 002bb000 08:03 671210                     /opt/jre1.6.0_12/lib/deploy.jar
7f1979944000-7f1979945000 ---p 7f1979944000 00:00 0 
7f1979945000-7f1979a45000 rwxp 7f1979945000 00:00 0 
7f1979a45000-7f1979a48000 ---p 7f1979a45000 00:00 0 
7f1979a48000-7f1979b46000 rwxp 7f1979a48000 00:00 0 
7f1979b46000-7f1979b49000 ---p 7f1979b46000 00:00 0 
7f1979b49000-7f1979c47000 rwxp 7f1979b49000 00:00 0 
7f1979c47000-7f1979c4a000 ---p 7f1979c47000 00:00 0 
7f1979c4a000-7f1979d48000 rwxp 7f1979c4a000 00:00 0 
7f1979d48000-7f1979d4b000 ---p 7f1979d48000 00:00 0 
7f1979d4b000-7f1979e49000 rwxp 7f1979d4b000 00:00 0 
7f1979e49000-7f1979fc7000 r-xp 00000000 08:03 245227                     /usr/lib/locale/locale-archive
7f1979fc7000-7f1979fca000 ---p 7f1979fc7000 00:00 0 
7f1979fca000-7f197a0c8000 rwxp 7f1979fca000 00:00 0 
7f197a0c8000-7f197a0cb000 ---p 7f197a0c8000 00:00 0 
7f197a0cb000-7f197a1c9000 rwxp 7f197a0cb000 00:00 0 
7f197a1c9000-7f197a1ca000 ---p 7f197a1c9000 00:00 0 
7f197a1ca000-7f197a360000 rwxp 7f197a1ca000 00:00 0 
7f197a360000-7f197a4f1000 r-xs 02a2f000 08:03 670465                     /opt/jre1.6.0_12/lib/rt.jar
7f197a4f1000-7f197a519000 rwxp 7f197a4f1000 00:00 0 
7f197a519000-7f197a51a000 ---p 7f197a519000 00:00 0 
7f197a51a000-7f197a61a000 rwxp 7f197a51a000 00:00 0 
7f197a61a000-7f197a61b000 ---p 7f197a61a000 00:00 0 
7f197a61b000-7f197a72e000 rwxp 7f197a61b000 00:00 0 
7f197a72e000-7f197a745000 rwxp 7f197a72e000 00:00 0 
7f197a745000-7f197a751000 rwxp 7f197a745000 00:00 0 
7f197a751000-7f197a765000 rwxp 7f197a751000 00:00 0 
7f197a765000-7f197a778000 rwxp 7f197a765000 00:00 0 
7f197a778000-7f197a78f000 rwxp 7f197a778000 00:00 0 
7f197a78f000-7f197a79b000 rwxp 7f197a78f000 00:00 0 
7f197a79b000-7f197a7af000 rwxp 7f197a79b000 00:00 0 
7f197a7af000-7f197a7bf000 rwxp 7f197a7af000 00:00 0 
7f197a7bf000-7f197cc40000 rwxp 7f197a7bf000 00:00 0 
7f197cc40000-7f197fbc0000 rwxp 7f197cc40000 00:00 0 
7f197fbc0000-7f1981200000 rwxp 7f197fbc0000 00:00 0 
7f1981200000-7f1983bc0000 rwxp 7f1981200000 00:00 0 
7f1983bc0000-7f1985bc0000 rwxp 7f1983bc0000 00:00 0 
7f1985bcc000-7f1985e3c000 rwxp 7f1985bcc000 00:00 0 
7f1985e3c000-7f1988bcc000 rwxp 7f1985e3c000 00:00 0 
7f1988bcc000-7f1988bda000 r-xp 00000000 08:03 671024                     /opt/jre1.6.0_12/lib/amd64/libzip.so
7f1988bda000-7f1988cdc000 ---p 0000e000 08:03 671024                     /opt/jre1.6.0_12/lib/amd64/libzip.so
7f1988cdc000-7f1988cdf000 rwxp 00010000 08:03 671024                     /opt/jre1.6.0_12/lib/amd64/libzip.so
7f1988cdf000-7f1988ce0000 rwxp 7f1988cdf000 00:00 0 
7f1988ce0000-7f1988d09000 r-xp 00000000 08:03 671007                     /opt/jre1.6.0_12/lib/amd64/libjava.so
7f1988d09000-7f1988e08000 ---p 00029000 08:03 671007                     /opt/jre1.6.0_12/lib/amd64/libjava.so
7f1988e08000-7f1988e0f000 rwxp 00028000 08:03 671007                     /opt/jre1.6.0_12/lib/amd64/libjava.so
7f1988e0f000-7f1988e1c000 r-xp 00000000 08:03 671051                     /opt/jre1.6.0_12/lib/amd64/libverify.so
7f1988e1c000-7f1988f1b000 ---p 0000d000 08:03 671051                     /opt/jre1.6.0_12/lib/amd64/libverify.so
7f1988f1b000-7f1988f1e000 rwxp 0000c000 08:03 671051                     /opt/jre1.6.0_12/lib/amd64/libverify.so
7f1988f1e000-7f1988f29000 r-xp 00000000 08:03 652849                     /lib/libnss_files-2.9.so
7f1988f29000-7f1989128000 ---p 0000b000 08:03 652849                     /lib/libnss_files-2.9.so
7f1989128000-7f1989129000 r-xp 0000a000 08:03 652849                     /lib/libnss_files-2.9.so
7f1989129000-7f198912a000 rwxp 0000b000 08:03 652849                     /lib/libnss_files-2.9.so
7f198912a000-7f198913f000 r-xp 00000000 08:03 652912                     /lib/libnsl-2.9.so
7f198913f000-7f198933e000 ---p 00015000 08:03 652912                     /lib/libnsl-2.9.so
7f198933e000-7f198933f000 r-xp 00014000 08:03 652912                     /lib/libnsl-2.9.so
7f198933f000-7f1989340000 rwxp 00015000 08:03 652912                     /lib/libnsl-2.9.so
7f1989340000-7f1989342000 rwxp 7f1989340000 00:00 0 
7f1989342000-7f1989349000 r-xp 00000000 08:03 671050                     /opt/jre1.6.0_12/lib/amd64/native_threads/libhpi.so
7f1989349000-7f198944a000 ---p 00007000 08:03 671050                     /opt/jre1.6.0_12/lib/amd64/native_threads/libhpi.so
7f198944a000-7f198944c000 rwxp 00008000 08:03 671050                     /opt/jre1.6.0_12/lib/amd64/native_threads/libhpi.so
7f198944c000-7f198944d000 rwxp 7f198944c000 00:00 0 
7f198944d000-7f1989454000 r-xp 00000000 08:03 652850                     /lib/librt-2.9.so
7f1989454000-7f1989653000 ---p 00007000 08:03 652850                     /lib/librt-2.9.so
7f1989653000-7f1989654000 r-xp 00006000 08:03 652850                     /lib/librt-2.9.so
7f1989654000-7f1989655000 rwxp 00007000 08:03 652850                     /lib/librt-2.9.so
7f1989655000-7f1989658000 ---p 7f1989655000 00:00 0 
7f1989658000-7f1989756000 rwxp 7f1989658000 00:00 0 
7f1989756000-7f19897d8000 r-xp 00000000 08:03 652824                     /lib/libm-2.9.so
7f19897d8000-7f19899d7000 ---p 00082000 08:03 652824                     /lib/libm-2.9.so
7f19899d7000-7f19899d8000 r-xp 00081000 08:03 652824                     /lib/libm-2.9.so
7f19899d8000-7f19899d9000 rwxp 00082000 08:03 652824                     /lib/libm-2.9.so
7f19899d9000-7f198a066000 r-xp 00000000 08:03 671038                     /opt/jre1.6.0_12/lib/amd64/server/libjvm.so
7f198a066000-7f198a165000 ---p 0068d000 08:03 671038                     /opt/jre1.6.0_12/lib/amd64/server/libjvm.so
7f198a165000-7f198a2b6000 rwxp 0068c000 08:03 671038                     /opt/jre1.6.0_12/lib/amd64/server/libjvm.so
7f198a2b6000-7f198a2f3000 rwxp 7f198a2b6000 00:00 0 
7f198a2f3000-7f198a43d000 r-xp 00000000 08:03 654263                     /lib/libc-2.9.so
7f198a43d000-7f198a63d000 ---p 0014a000 08:03 654263                     /lib/libc-2.9.so
7f198a63d000-7f198a641000 r-xp 0014a000 08:03 654263                     /lib/libc-2.9.so
7f198a641000-7f198a642000 rwxp 0014e000 08:03 654263                     /lib/libc-2.9.so
7f198a642000-7f198a647000 rwxp 7f198a642000 00:00 0 
7f198a647000-7f198a649000 r-xp 00000000 08:03 652834                     /lib/libdl-2.9.so
7f198a649000-7f198a849000 ---p 00002000 08:03 652834                     /lib/libdl-2.9.so
7f198a849000-7f198a84a000 r-xp 00002000 08:03 652834                     /lib/libdl-2.9.so
7f198a84a000-7f198a84b000 rwxp 00003000 08:03 652834                     /lib/libdl-2.9.so
7f198a84b000-7f198a861000 r-xp 00000000 08:03 652844                     /lib/libpthread-2.9.so
7f198a861000-7f198aa61000 ---p 00016000 08:03 652844                     /lib/libpthread-2.9.so
7f198aa61000-7f198aa62000 r-xp 00016000 08:03 652844                     /lib/libpthread-2.9.so
7f198aa62000-7f198aa63000 rwxp 00017000 08:03 652844                     /lib/libpthread-2.9.so
7f198aa63000-7f198aa67000 rwxp 7f198aa63000 00:00 0 
7f198aa67000-7f198aa84000 r-xp 00000000 08:03 654262                     /lib/ld-2.9.so
7f198aa95000-7f198aa9f000 rwxp 7f198aa95000 00:00 0 
7f198aa9f000-7f198ab55000 rwxp 7f198aa9f000 00:00 0 
7f198ab55000-7f198ab58000 rwxp 7f198ab55000 00:00 0 
7f198ab58000-7f198ab5f000 r-xp 00000000 08:03 671014                     /opt/jre1.6.0_12/lib/amd64/jli/libjli.so
7f198ab5f000-7f198ac60000 ---p 00007000 08:03 671014                     /opt/jre1.6.0_12/lib/amd64/jli/libjli.so
7f198ac60000-7f198ac62000 rwxp 00008000 08:03 671014                     /opt/jre1.6.0_12/lib/amd64/jli/libjli.so
7f198ac62000-7f198ac63000 rwxp 7f198ac62000 00:00 0 
7f198ac6e000-7f198ac75000 r-xs 00110000 08:03 670507                     /opt/jre1.6.0_12/lib/resources.jar
7f198ac75000-7f198ac77000 r-xs 00007000 08:02 6004738                    /home/austin/.java/deployment/cache/6.0/40/24b883a8-2f7c8297
7f198ac77000-7f198ac7f000 rwxs 00000000 08:03 122433                     /tmp/hsperfdata_austin/7202
7f198ac7f000-7f198ac80000 rwxp 7f198ac7f000 00:00 0 
7f198ac80000-7f198ac81000 r-xp 7f198ac80000 00:00 0 
7f198ac81000-7f198ac83000 rwxp 7f198ac81000 00:00 0 
7f198ac83000-7f198ac84000 r-xp 0001c000 08:03 654262                     /lib/ld-2.9.so
7f198ac84000-7f198ac85000 rwxp 0001d000 08:03 654262                     /lib/ld-2.9.so
7fff92c6f000-7fff92c84000 rwxp 7ffffffea000 00:00 0                      [stack]
7fff92dfe000-7fff92dff000 r-xp 7fff92dfe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
jvm_args: -D__jvm_launched=231682346806 -Xbootclasspath/a:/opt/jre1.6.0_12/lib/deploy.jar:/opt/jre1.6.0_12/lib/javaws.jar:/opt/jre1.6.0_12/lib/plugin.jar -Xmx96m -Dsun.java2d.noddraw=true 
java_command: sun.plugin2.main.client.PluginMain write_pipe_name=/tmp/.com.sun.deploy.net.socket.7169.10958713328915891.AF_UNIX
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/bin:/home/austin/bin:/bin:/usr/bin:/sbin:/usr/sbin:/usr/bin/perlbin/site:/usr/bin/perlbin/vendor:/usr/bin/perlbin/core
LD_LIBRARY_PATH=/opt/jre1.6.0_12/lib/amd64/server:/opt/jre1.6.0_12/lib/amd64:/opt/jre1.6.0_12/../lib/amd64
SHELL=/bin/zsh
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5fcd20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5fcd20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4e0eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4e0eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4e0eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4e0eb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4e35d0], sa_mask[0]=0x00000004, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4e3320], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4e3320], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4e3320], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4e3320], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Linux
uname:Linux 2.6.27-ARCH #1 SMP PREEMPT Sun Dec 14 09:18:00 UTC 2008 x86_64
libc:glibc 2.9 NPTL 2.9 
rlimit: STACK 8192k, CORE 0k, NPROC 16380, NOFILE 1024, AS infinity
load average:0.15 0.24 0.17

CPU:total 2 (2 cores per cpu, 1 threads per core) family 15 model 67 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2059516k(194296k free), swap 2096472k(2096472k free)

vm_info: Java HotSpot(TM) 64-Bit Server VM (11.2-b01) for linux-amd64 JRE (1.6.0_12-ea-b02), built on Dec  8 2008 01:49:50 by "java_re" with gcc 3.2.2 (SuSE Linux)

time: Thu Dec 18 15:42:58 2008
elapsed time: 40 seconds


```

---

### Post by doorknob60 on 2008-12-20
Yay! I half solved my problem. I found a way to play RS that I like, but it's not optimal (I want to use my 64 bit FF)

JRE64+Firefox64=White Screen on RS, fine with anything else
JRE64+Seamonkey64=Java fails to load altogether
JRE32+Firefox32=White Screen on RS, fine with anything else
JRE64+Konqueror64=Black Screen on RS, probably works fine with other stuff, didn't check

That was my old situation...look at my solution:

JRE32+Seamonkey32=WORKS!!!

Finally, although I still don't know why all the other previously working combinations fail to work now, that could be helpful, so I'm not calling this solved yet.

---

