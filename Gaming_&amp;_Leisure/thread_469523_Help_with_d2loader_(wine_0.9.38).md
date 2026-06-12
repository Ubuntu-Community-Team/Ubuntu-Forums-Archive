---
title: "Help with d2loader (wine 0.9.38)"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by magic_ninja on 2007-06-10
Hey I've properly installed d2loader and diablo II (infact I've been playing without d2loader for some time now) and I now get this error when I attempt to load d2loader.  Its a mass of output, but the juicy stuff is this 

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:winmm:MMDRV_Exit Closing while ll-driver open
wine: Unhandled page fault on read access to 0x01e70000 at address 0x6f9b9878 (thread 0012), starting debugger...
Unhandled exception: page fault on read access to 0x01e70000 in 32-bit code (0x6f9b9878).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f9b9878 ESP:7ad4e9f4 EBP:00000000 EFLAGS:00010206(   - 00      - RIP1)
 EAX:01e70000 EBX:7bc7b470 ECX:7ee50940 EDX:01e70000
 ESI:00000000 EDI:6f9b9800
Stack dump:
0x7ad4e9f4:  6f9b9800 00000000 7ad4ea28 7bc7b470
0x7ad4ea04:  7ad4eaac 01e70000 00000000 b7ca61a9
0x7ad4ea14:  b7dd0ff4 00000000 7bc5d37e 00000000
0x7ad4ea24:  6f9b9800 7ad4eac8 7bc5e052 6f9b9800
0x7ad4ea34:  00000000 b7dba120 7af99330 7af99330
0x7ad4ea44:  b7dc8e70 7ad4fd80 7af99328 00000000
Backtrace:
=>1 0x6f9b9878 in d2sound (+0x9878) (0x00000000)
0x6f9b9878: movl        0x0(%edx),%ebx
```

I'm not sure where to start, but I hope someone here has a good idea of where to :-)

---

### Post by magic_ninja on 2007-06-10
Okay, I changed my windows version from XP to 2000, and now d2loader is working, now I just have to figure out how to initiate the plugins via d2hackit

---

### Post by magic_ninja on 2007-06-10
Ok, i figured out its from using d2hackit to load the maphack like the guide suggests, for some reason when d2hacket loads it crashes d2.

---

