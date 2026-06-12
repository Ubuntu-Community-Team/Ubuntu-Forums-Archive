---
title: "Mumble random crashes"
date: 2010-08-11
forum: Desktop Environments
---

### Post by James148 on 2010-08-11
I've used mumble plenty of times on ubuntu, but i stopped using it for a month or two, (which makes it hard to point out a specific patch or update that broke it) and when i started using it again, it often crashes randomly, without a message or anything, the icon on the gnome panel just disappears, and i have to open it again.

Here are some things i've noticed:
1) running music at the same time has no effect
2) it almost always crashes when i have my mic open
3) restarting the computer, or gdm, doesnt help
4) the crashes get more and more frequent until a reboot
5) when mumbles not in use at all it doesnt crash

i ran it for a bit through the terminal, to see if i could get an error message, and i got:
```
*** glibc detected *** mumble: free(): invalid next size (fast): 0x09a216c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x8b5c591]
/lib/tls/i686/cmov/libc.so.6(+0x6cde8)[0x8b5dde8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x8b60ecd]
/usr/lib/libX11.so.6(XFree+0x1d)[0x15e45d]
/usr/lib/libX11.so.6(_XFreeEventCookies+0x3c)[0x15e4ac]
/usr/lib/libX11.so.6(XNextEvent+0x3d)[0x14d5bd]
mumble[0x81ea672]
mumble[0x820664a]
/usr/lib/libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3a)[0x6ffac9a]
/usr/lib/libQtCore.so.4(_ZN11QMetaObject8activateEP7QObjectPKS_iPPv+0x2d5)[0x70093d5]
/usr/lib/libQtCore.so.4(_ZN15QSocketNotifier9activatedEi+0x43)[0x705a933]
/usr/lib/libQtCore.so.4(_ZN15QSocketNotifier5eventEP6QEvent+0x147)[0x70108e7]
/usr/lib/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xac)[0x10fc4dc]
/usr/lib/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x17e)[0x110305e]
/usr/lib/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x7b)[0x6ff5a3b]
/usr/lib/libQtCore.so.4(+0x1949aa)[0x70219aa]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0x2af85e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0x2afc2d8]
/lib/libglib-2.0.so.0(g_main_context_iteration+0x68)[0x2afc4b8]
/usr/lib/libQtCore.so.4(_ZN20QEventDispatcherGlib13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x65)[0x70215d5]
/usr/lib/libQtGui.so.4(+0x1f5135)[0x11bc135]
/usr/lib/libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x49)[0x6ff4059]
/usr/lib/libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xfa)[0x6ff44aa]
/usr/lib/libQtCore.so.4(_ZN16QCoreApplication4execEv+0xaf)[0x6ff869f]
/usr/lib/libQtGui.so.4(_ZN12QApplication4execEv+0x27)[0x10fc577]
mumble[0x80ed244]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x8b07bd6]
mumble[0x8074731]
======= Memory map: ========
00110000-00123000 r-xp 00000000 08:06 5677060    /usr/lib/sse2/libspeexdsp.so.1.5.0
00123000-00124000 r--p 00012000 08:06 5677060    /usr/lib/sse2/libspeexdsp.so.1.5.0
00124000-00125000 rw-p 00013000 08:06 5677060    /usr/lib/sse2/libspeexdsp.so.1.5.0
00125000-0023e000 r-xp 00000000 08:06 116275     /usr/lib/libX11.so.6.3.0
0023e000-0023f000 r--p 00118000 08:06 116275     /usr/lib/libX11.so.6.3.0
0023f000-00241000 rw-p 00119000 08:06 116275     /usr/lib/libX11.so.6.3.0
00241000-00242000 rw-p 00000000 00:00 0 
00242000-00247000 r-xp 00000000 08:06 117602     /usr/lib/libg15render.so.1.1.0
00247000-00248000 r--p 00004000 08:06 117602     /usr/lib/libg15render.so.1.1.0
00248000-00249000 rw-p 00005000 08:06 117602     /usr/lib/libg15render.so.1.1.0
0024a000-00250000 r-xp 00000000 08:06 117167     /usr/lib/libspeechd.so.2.1.1
00250000-00251000 r--p 00005000 08:06 117167     /usr/lib/libspeechd.so.2.1.1
00251000-00252000 rw-p 00006000 08:06 117167     /usr/lib/libspeechd.so.2.1.1
00252000-00259000 r-xp 00000000 08:06 116209     /usr/lib/libdns_sd.so.1.0.0
00259000-0025a000 r--p 00006000 08:06 116209     /usr/lib/libdns_sd.so.1.0.0
0025a000-0025b000 rw-p 00007000 08:06 116209     /usr/lib/libdns_sd.so.1.0.0
0025b000-00265000 r-xp 00000000 08:06 116373     /usr/lib/libavahi-common.so.3.5.1
00265000-00266000 r--p 00009000 08:06 116373     /usr/lib/libavahi-common.so.3.5.1
00266000-00267000 rw-p 0000a000 08:06 116373     /usr/lib/libavahi-common.so.3.5.1
00267000-0027c000 r-xp 00000000 08:06 4562965    /lib/tls/i686/cmov/libpthread-2.11.1.so
0027c000-0027d000 r--p 00014000 08:06 4562965    /lib/tls/i686/cmov/libpthread-2.11.1.so
0027d000-0027e000 rw-p 00015000 08:06 4562965    /lib/tls/i686/cmov/libpthread-2.11.1.so
0027e000-00280000 rw-p 00000000 00:00 0 
00280000-002bd000 r-xp 00000000 08:06 6062104    /usr/lib/libQtSql.so.4.6.2
002bd000-002be000 ---p 0003d000 08:06 6062104    /usr/lib/libQtSql.so.4.6.2
002be000-002bf000 r--p 0003d000 08:06 6062104    /usr/lib/libQtSql.so.4.6.2
002bf000-002c0000 rw-p 0003e000 08:06 6062104    /usr/lib/libQtSql.so.4.6.2
002c0000-00302000 r-xp 00000000 08:06 6062089    /usr/lib/libQtXml.so.4.6.2
00302000-00303000 ---p 00042000 08:06 6062089    /usr/lib/libQtXml.so.4.6.2
00303000-00304000 r--p 00042000 08:06 6062089    /usr/lib/libQtXml.so.4.6.2
00304000-00305000 rw-p 00043000 08:06 6062089    /usr/lib/libQtXml.so.4.6.2
00305000-00322000 r-xp 00000000 08:06 4538451    /lib/libgcc_s.so.1
00322000-00323000 r--p 0001c000 08:06 4538451    /lib/libgcc_s.so.1
00323000-00324000 rw-p 0001d000 08:06 4538451    /lib/libgcc_s.so.1
00324000-00337000 r-xp 00000000 08:06 4538566    /lib/libz.so.1.2.3.3
00337000-00338000 r--p 00012000 08:06 4538566    /lib/libz.so.1.2.3.3
00338000-00339000 rw-p 00013000 08:06 4538566    /lib/libz.so.1.2.3.3
00339000-0033c000 r-xp 00000000 08:06 117600     /usr/lib/libg15.so.1.0.0
0033c000-0033d000 r--p 00002000 08:06 117600     /usr/lib/libg15.so.1.0.0
0033d000-0033e000 rw-p 00003000 08:06 117600     /usr/lib/libg15.so.1.0.0
0033f000-0034d000 r-xp 00000000 08:06 116371     /usr/lib/libavahi-client.so.3.2.5
0034d000-0034e000 ---p 0000e000 08:06 116371     /usr/lib/libavahi-client.so.3.2.5
0034e000-0034f000 r--p 0000e000 08:06 116371     /usr/lib/libavahi-client.so.3.2.5
0034f000-00350000 rw-p 0000f000 08:06 116371     /usr/lib/libavahi-client.so.3.2.5
00350000-0035e000 r-xp 00000000 08:06 116292     /usr/lib/libXext.so.6.4.0
0035e000-0035f000 r--p 0000d000 08:06 116292     /usr/lib/libXext.so.6.4.0
0035f000-00360000 rw-p 0000e000 08:06 116292     /usr/lib/libXext.so.6.4.0
00360000-00362000 r-xp 00000000 08:06 4562954    /lib/tls/i686/cmov/libdl-2.11.1.so
00362000-00363000 r--p 00001000 08:06 4562954    /lib/tls/i686/cmov/libdl-2.11.1.so
00363000-00364000 rw-p 00002000 08:06 4562954    /lib/tls/i686/cmov/libdl-2.11.1.so
00364000-00369000 r-xp 00000000 08:06 117003     /usr/lib/libogg.so.0.6.0
00369000-0036a000 r--p 00004000 08:06 117003     /usr/lib/libogg.so.0.6.0
0036a000-0036b000 rw-p 00005000 08:06 117003     /usr/lib/libogg.so.0.6.0
0036b000-00372000 r-xp 00000000 08:06 116273     /usr/lib/libSM.so.6.0.1
00372000-00373000 r--p 00006000 08:06 116273     /usr/lib/libSM.so.6.0.1
00373000-00374000 rw-p 00007000 08:06 116273     /usr/lib/libSM.so.6.0.1
00374000-00375000 r-xp 00000000 08:06 148115     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
00375000-00376000 r--p 00000000 08:06 148115     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
00376000-00377000 rw-p 00001000 08:06 148115     /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
00377000-00392000 r-xp 00000000 08:06 4538507    /lib/ld-2.11.1.so
00392000-00393000 r--p 0001a000 08:06 4538507    /lib/ld-2.11.1.so
00393000-00394000 rw-p 0001b000 08:06 4538507    /lib/ld-2.11.1.so
00394000-0039c000 r-xp 00000000 08:06 116314     /usr/lib/libXrender.so.1.3.0
0039c000-0039d000 r--p 00007000 08:06 116314     /usr/lib/libXrender.so.1.3.0
0039d000-0039e000 rw-p 00008000 08:06 116314     /usr/lib/libXrender.so.1.3.0
003a1000-003c5000 r-xp 00000000 08:06 4562955    /lib/tls/i686/cmov/libm-2.11.1.soAborted

```

this means nothing to me, if anyone could shed some light on this it would be VERY appreciated.
Thanks.

---

