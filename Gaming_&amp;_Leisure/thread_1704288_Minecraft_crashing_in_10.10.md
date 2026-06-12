---
title: "Minecraft crashing in 10.10"
date: 2011-03-10
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2011-03-10
I'm running Minecraft on x32 10.10 with Sun Java 6. It loads quickly, until I create a world. The app will automatically close. How do I fix this?

---

### Post by donkyhotay on 2011-03-10
launch it from terminal and post the crash dump here.

---

### Post by jmgrosen on 2011-03-13
I have the same problem.
Here's mine: (but it's really long)
```

Setting user: jmgrosen, 4714701796487544093
Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

143 recipes
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb778f424, pid=30852, tid=1800178544
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/john/Downloads/hs_err_pid30852.log
[thread 1874725744 also had an error]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted
john@usandy:~/Downloads$ java -Xmx1G -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
28
Setting user: [username], 3587138724117654651
Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb784a424, pid=30938, tid=1807371120
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# An error report file with more information is saved as:
# /home/john/Downloads/hs_err_pid30938.log
*** glibc detected *** java: malloc(): smallbin double linked list corrupted: 0x088e0368 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xb7713501]
/lib/libc.so.6(+0x6f679)[0xb7716679]
/lib/libc.so.6(__libc_malloc+0x63)[0xb7717f33]
/usr/lib/fglrx/dri/fglrx_dri.so(+0x15de0f3)[0x6b4b90f3]
/usr/lib/fglrx/dri/fglrx_dri.so(+0x1412260)[0x6b2ed260]
[0x0]
======= Memory map: ========
08048000-08052000 r-xp 00000000 08:01 533677     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 533677     /usr/lib/jvm/java-6-sun-1.6.0.24/jre/bin/java
08132000-0893d000 rwxp 00000000 00:00 0          [heap]
59010000-59011000 ---p 00000000 00:00 0 
59011000-59211000 rwxp 00000000 00:00 0 
59211000-59212000 ---p 00000000 00:00 0 
59212000-59412000 rwxp 00000000 00:00 0 
59412000-59413000 ---p 00000000 00:00 0 
59413000-59613000 rwxp 00000000 00:00 0 
59613000-59616000 ---p 00000000 00:00 0 
59616000-636a4000 rwxp 00000000 00:00 0 
636a4000-636a5000 ---p 00000000 00:00 0 
636a5000-63ea5000 rwxp 00000000 00:00 0 
63ea5000-63ea6000 ---p 00000000 00:00 0 
63ea6000-646a6000 rwxp 00000000 00:00 0 
646a6000-686a7000 rwxs 00000000 00:10 1137754    /dev/shm/pulse-shm-1589114456
686a7000-6880c000 r-xp 00000000 08:01 2235283    /usr/lib/libvorbisenc.so.2.0.7
6880c000-6880d000 ---p 00165000 08:01 2235283    /usr/lib/libvorbisenc.so.2.0.7
6880d000-6881e000 r-xp 00165000 08:01 2235283    /usr/lib/libvorbisenc.so.2.0.7
6881e000-6881f000 rwxp 00176000 08:01 2235283    /usr/lib/libvorbisenc.so.2.0.7
6881f000-68869000 r-xp 00000000 08:01 2236130    /usr/lib/libFLAC.so.8.2.0
68869000-6886a000 r-xp 00049000 08:01 2236130    /usr/lib/libFLAC.so.8.2.0
6886a000-6886b000 rwxp 0004a000 08:01 2236130    /usr/lib/libFLAC.so.8.2.0
6886b000-688cc000 r-xp 00000000 08:01 2236313    /usr/lib/libsndfile.so.1.0.21
688cc000-688cd000 ---p 00061000 08:01 2236313    /usr/lib/libsndfile.so.1.0.21
688cd000-688ce000 r-xp 00061000 08:01 2236313    /usr/lib/libsndfile.so.1.0.21
688ce000-688cf000 rwxp 00062000 08:01 2236313    /usr/lib/libsndfile.so.1.0.21
688cf000-688d3000 rwxp 00000000 00:00 0 
688d3000-6891b000 r-xp 00000000 08:01 2236773    /usr/lib/libpulsecommon-0.9.21.so
6891b000-6891c000 r-xp 00047000 08:01 2236773    /usr/lib/libpulsecommon-0.9.21.so
6891c000-6891d000 rwxp 00048000 08:01 2236773    /usr/lib/libpulsecommon-0.9.21.so
6891d000-6895c000 r-xp 00000000 08:01 2234289    /usr/lib/libpulse.so.0.12.2
6895c000-6895d000 ---p 0003f000 08:01 2234289    /usr/lib/libpulse.so.0.12.2
6895d000-6895e000 r-xp 0003f000 08:01 2234289    /usr/lib/libpulse.so.0.12.2
6895e000-6895f000 rwxp 00040000 08:01 2234289    /usr/lib/libpulse.so.0.12.2
6895f000-68a1f000 r-xp 00000000 08:01 2233896    /usr/lib/libasound.so.2.0.0
68a1f000-68a20000 ---p 000c0000 08:01 2233896    /usr/lib/libasound.so.2.0.0
68a20000-68a24000 r-xp 000c0000 08:01 2233896    /usr/lib/libasound.so.2.0.0
68a24000-68a25000 rwxp 000c4000 08:01 2233896    /usr/lib/libasound.so.2.0.0
68a25000-68a4a000 r-xp 00000000 08:07 18878179   /home/john/.minecraft/bin/natives/libopenal.so
68a4a000-68a4b000 rwxp 00025000 08:07 18878179   /home/john/.minecraft/bin/natives/libopenal.so
68a4b000-68b38000 rwxp 00000000 00:00 0 
68b38000-68b3b000 ---p 00000000 00:00 0 
68b3b000-68b89000 rwxp 00000000 00:00 0 
68b89000-68d89000 rwxs d79ce000 00:05 8351       /dev/ati/card0
68d89000-68e89000 rwxs 101e1000 00:05 8351       /dev/ati/card0
68e89000-6978d000 rwxp 00000000 00:00 0 
6978d000-697be000 r-xp 00000000 08:01 2364932    /usr/lib/fglrx/libatiadlxx.so
697be000-697bf000 rwxp 00030000 08:01 2364932    /usr/lib/fglrx/libatiadlxx.so
697d2000-697d9000 r-xp 00000000 08:01 394026     /lib/libwrap.so.0.7.6
697d9000-697da000 r-xp 00006000 08:01 394026     /lib/libwrap.so.0.7.6
697da000-697db000 rwxp 00007000 08:01 394026     /lib/libwrap.so.0.7.6
697db000-69edb000 rwxs 00006000 00:05 8351       /dev/ati/card0
69edb000-6b8f0000 r-xp 00000000 08:01 2364908    /usr/lib/fglrx/dri/fglrx_dri.so
6b8f0000-6b9b4000 rwxp 01a15000 08:01 2364908    /usr/lib/fglrx/dri/fglrx_dri.so
6b9b4000-6ba3f000 rwxp 00000000 00:00 0 
6ba3f000-6ba59000 r-xp 00000000 08:01 394086     /lib/libgcc_s.so.1
6ba59000-6ba5a000 r-xp 00019000 08:01 394086     /lib/libgcc_s.so.1
6ba5a000-6ba5b000 rwxp 0001a000 08:01 394086     /lib/libgcc_s.so.1
6ba5b000-6bb0f000 r-xp 00000000 08:01 2364910    /usr/lib/fglrx/libGL.so.1.2
6bb0f000-6bb1a000 rwxp 000b3000 08:01 2364910    /usr/lib/fglrx/libGL.so.1.2
6bb1a000-6bb1f000 rwxp 00000000 00:00 0 
6bb22000-6bb37000 r-xp 00000000 08:01 2235400    /usr/lib/libICE.so.6.3.0
6bb37000-6bb38000 r-xp 00014000 08:01 2235400    /usr/lib/libICE.so.6.3.0
6bb38000-6bb39000 rwxp 00015000 08:01 2235400    /usr/lib/libICE.so.6.3.0
6bb39000-6bb3b000 rwxp 00000000 00:00 0 
6bb3b000-6bb7c000 r-xp 00000000 08:07 18878174   /home/john/.minecraft/bin/natives/liblwjgl.so
6bb7c000-6bb7d000 rwxp 00041000 08:07 18878174   /home/john/.minecraft/bin/natives/liblwjgl.so
6bb80000-6bb83000 r-xp 00000000 08:01 410592     /lib/libuuid.so.1.3.0
6bb83000-6bb84000 r-xp 00002000 08:01 410592     /lib/libuuid.so.1.3.0
6bb84000-6bb85000 rwxp 00003000 08:01 410592     /lib/libuuid.so.1.3.0
6bb85000-6bb88000 r-xp 00000000 08:01 2236432    /usr/lib/libxcb-atom.so.1.0.0
6bb88000-6bb89000 r-xp 00002000 08:01 2236432    /usr/lib/libxcb-atom.so.1.0.0
6bb89000-6bb8a000 rwxp 00003000 08:01 2236432    /usr/lib/libxcb-atom.so.1.0.0
6bb8a000-6bb91000 r-xp 00000000 08:01 2235429    /usr/lib/libSM.so.6.0.1
6bb91000-6bb92000 r-xp 00006000 08:01 2235429    /usr/lib/libSM.so.6.0.1
6bb92000-6bb93000 rwxp 00007000 08:01 2235429    /usr/lib/libSM.so.6.0.1
6bb94000-6bb95000 ---p 00000000 00:00 0 
6bb95000-6bba5000 rwxp 00000000 00:00 0 
6bba5000-6bba9000 r-xp 00000000 08:01 2239942    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6bba9000-6bbaa000 r-xp 00003000 08:01 2239942    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6bbaa000-6bbab000 rwxp 00004000 08:01 2239942    /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
6bbab000-6bbb2000 r-xs 00000000 08:01 2248787    /usr/lib/gconv/gconv-modules.cache
6bbb2000-6bbf2000 rwxs 00011000 00:05 8351       /dev/ati/card0
6bbf2000-6bbf3000 rwxs 00005000 00:05 8351       /dev/ati/card0
6bbf3000-6bc13000 rwxs feae0000 00:05 8351       /dev/ati/card0
6bc13000-6bda4000 rwxs 00000000 00:04 306184275  /SYSV00000000 (deleted)
6bda4000-6bdaf000 r-xs 00127000 08:07 11017781   /home/john/.minecraft/bin/minecraft.jar
6bdaf000-6bdb4000 r-xs 0002f000 08:07 18747448   /home/john/.minecraft/bin/jinput.jar
6bdb4000-6bdbb000 r-xs 00083000 08:07 18747772   /home/john/.minecraft/bin/lwjgl.jar
6bdbb000-6be20000 rwxs 00000000 00:04 306151506  /SYSV00000000 (deleted)
6be20000-6be23000 ---p 00000000 00:00 0 
6be23000-6be71000 rwxp 00000000 00:00 0 
6be71000-6be74000 ---p 00000000 00:00 0 
6be74000-6bec2000 rwxp 00000000 00:00 0 
6bec2000-6c053000 rwxs 00000000 00:04 305037334  /SYSV00000000 (deleted)
6c053000-6c2bf000 rwxp 00000000 00:00 0 Aborted


```

HELP???

Thanks,
John

---

### Post by sdc444 on 2011-03-14
This site fixed my problems with Minecraft, though I only had to do the first few steps...

[http://timashley.me/node/596](http://timashley.me/node/596)

Good luck.

---

