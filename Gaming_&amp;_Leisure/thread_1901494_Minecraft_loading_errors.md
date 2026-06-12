---
title: "Minecraft loading errors"
date: 2011-12-28
forum: Gaming &amp; Leisure
---

### Post by skhubbard on 2011-12-28
I am fairly new to Ubuntu and I want to resume playing Minecraft like I used to on windows.

I have followed various posts and threads to help install it onto my system, but now playing it is the problem. I can open it and login and everything just fine, but once I get to the title screen I have like a 10 second window to do anything. It crashes when I try to create a new world, and when I open one of my worlds that I moved over from my other system it starts to load. If I'm fast enough I can see the game after it loads, but only for maybe a second. :confused:

I am using Ubuntu 11.10 with OpenJDK 6. I've tried every way of installing Minecraft and it won't work. :( The only thing that I think could be wrong with it is that the JRE times out, but idk why or how it would do that.

Any help would be much appreciated.

Also this error log appears in my "/.minecraft/install_files" folder.


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb78d5424, pid=4824, tid=1793153904
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [+0x424]  __kernel_vsyscall+0x10
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x000012d8

Registers:
EAX=0x00000000, EBX=0x000012d8, ECX=0x0000130d, EDX=0x0000000b
ESP=0x6ae15280, EBP=0x6ae15398, ESI=0x00000020, EDI=0xb78baff4
EIP=0xb78d5424, EFLAGS=0x00000206, CR2=0xb78c6000

Top of Stack: (sp=0x6ae15280)
0x6ae15280:   6ae15398 0000000b 0000130d b78b1e6e
0x6ae15290:   b78baff4 6a76d880 6a14d743 0000000b
0x6ae152a0:   00000000 00000000 00000000 00001000
0x6ae152b0:   00000000 00000000 00000000 00000000
0x6ae152c0:   00000000 7fffffff fffffffe ffffffff
0x6ae152d0:   ffffffff ffffffff ffffffff ffffffff
0x6ae152e0:   ffffffff ffffffff ffffffff ffffffff
0x6ae152f0:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb78d5424)
0xb78d5404:   00 00 cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90
0xb78d5414:   51 52 55 89 e5 0f 34 90 90 90 90 90 90 90 cd 80
0xb78d5424:   5d 5a 59 c3 00 2e 73 68 73 74 72 74 61 62 00 2e
0xb78d5434:   68 61 73 68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x000012d8 is an unknown value
ECX=0x0000130d is an unknown value
EDX=0x0000000b is an unknown value
ESP=0x6ae15280 is an unknown value
EBP=0x6ae15398 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb78baff4: <offset 0x17ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb78a3000


Stack: [0x6ae05000,0x6ae16000],  sp=0x6ae15280,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x424]  __kernel_vsyscall+0x10
C  [libpthread.so.0+0x6d31]
[error occurred during error reporting (printing native stack), id 0xb]




It continues on forever.

---

### Post by ergo-proxy on 2011-12-29
You need to install propietary oracle java...

---

