---
title: "Problems with WoW after installing latest updates with the auto-updater."
date: 2005-09-12
forum: Gaming &amp; Leisure
---

### Post by Enetheru on 2005-09-12
This is sort of relevant to a bunch of forums at once, and at the same time none at all. I hope it's alright to stick it here.

I just installed the latest updates by way of the Hoary auto-updater thing. Among these was the latest x.org server update. I later tried to start of world of warcraft with cedega and it would not start. I think it's due to the x.org update. If anyone has this problem, or if they can tell me down to downgrade the last changes, I'd be much obliged.

Oh, and I may as well point out that my card is an Nvidia Geforce 4 MX 440. The game was working fine until this morning. (September 13.)

Thanks!

Edit: I just checked glxgears, and got the following-

Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.

Edit the Second:
I just ran the little Point2Play hardware wizard again, and it couldn't even identify my card. It had previously. This is getting more and more involved...

---

### Post by strikeforce on 2005-09-12
It means you don't have your video card drivers installed properly.  I'm assuming in the process you updated the kernel?

If so thats possibly the reason.  You might have to reinstall your video drivers.

---

### Post by Enetheru on 2005-09-12
Sounds right to me. Thanks, I'll check that.

---

### Post by Oni-Dracula on 2005-10-06
Similar problems here after patching...
```

oni@ubuntu:~$ cedega /home/oni/TransGaming_Drive/Program\ Files/World\ of\ Warcr aft/WoW.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 18 09; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
wine: Unhandled exception, starting debugger...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 18 09; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x000 00000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libn tdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libw ine.so' (0x4011c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unic ode.so' (0x40131000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port .so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x40207000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x40229000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40357000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40369000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32. so' (0x40839000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32. so' (0x408ba000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so ' (0x4093f000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so'  (0x40a67000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32. so' (0x40ade000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.s o' (0x40b05000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libpng.so.3'  (0x40b81000)
No debug information in ELF '/usr/lib/libz.so.1' (0x40bb8000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libole32.so'  (0x40bcc000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/librpcrt4.so ' (0x40c31000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.s o' (0x40c77000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwsock32.s o' (0x40cb7000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libws2_32.so ' (0x40cc4000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libiphlpapi. so' (0x40cdc000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libopengl32. so' (0x40ceb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx1 1.so' (0x40d79000)
No debug information in ELF '/usr/lib/libSM.so.6' (0x40d96000)
No debug information in ELF '/usr/lib/libICE.so.6' (0x40d9d000)
No debug information in ELF '/usr/lib/libGL.so.1' (0x40db6000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1'  (0x40e35000)
No debug information in ELF '/usr/lib/libXext.so.6' (0x40ef0000)
No debug information in ELF '/usr/lib/libX11.so.6' (0x40efd000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0x40fbd000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0x41726000)
No debug information in ELF '/usr/lib/libXau.so.6' (0x41728000)
No debug information in ELF '/usr/lib/libXdmcp.so.6' (0x4172b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libddraw.so'  (0x4178a000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libimm32.so'  (0x417cf000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so'  (0x417de000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm32.s o' (0x418c4000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwininet.s o' (0x418d6000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserve r.so' (0x418f5000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0x41a5b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so ' (0x41ac5000)
No debug information in ELF '/usr/lib/X11/locale/common/xlcUTF8Load.so.2' (0x41b 45000)
No debug information in ELF '/usr/lib/X11/locale/common/ximcp.so.2' (0x41b47000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0x41b6e000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0x41b77000)
No debug information in ELF '/usr/lib/libXfixes.so.3' (0x41b7f000)
No debug information in 32bit DLL 'C:\Program Files\World of Warcraft\WoW.exe' ( 0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40056000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x4086c000)
No debug information in 32bit DLL 'C:\WINDOWS\SYSTEM32\MSVCRT.DLL' (0x407f3000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x40af0000)
No debug information in 32bit DLL 'GDI32.DLL' (0x40a86000)
No debug information in 32bit DLL 'USER32.DLL' (0x40976000)
No debug information in 32bit DLL 'COMCTL32.DLL' (0x408c8000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0x40c54000)
No debug information in 32bit DLL 'OLE32.DLL' (0x40beb000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0x40c94000)
No debug information in 32bit DLL 'SHELL32.DLL' (0x40b2b000)
No debug information in 32bit DLL 'IPHLPAPI.DLL' (0x40ce3000)
No debug information in 32bit DLL 'WS2_32.DLL' (0x40ccc000)
No debug information in 32bit DLL 'WSOCK32.DLL' (0x40cbb000)
No debug information in 32bit DLL 'DDRAW.DLL' (0x417a0000)
No debug information in 32bit DLL 'OPENGL32.DLL' (0x40d32000)
No debug information in 32bit DLL 'IMM32.DLL' (0x417d5000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\WORLD OF WARCRAFT\DIVXDECODE R.DLL' (0x10000000)
No debug information in 32bit DLL 'WINMM.DLL' (0x417ec000)
No debug information in 32bit DLL 'MSACM32.DLL' (0x418c9000)
No debug information in 32bit DLL 'C:\PROGRAM FILES\WORLD OF WARCRAFT\FMOD.DLL' (0x41834000)
No debug information in 32bit DLL 'WININET.DLL' (0x418e1000)
No debug information in 32bit DLL 'X11DRV.DLL' (0x41ae4000)
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0 0000000).
In 32-bit mode.
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:00000000 ESP:407e20e0 EBP:407e21b4 EFLAGS:00010246(  R- 00  I  Z- -P1 )
EAX:417ce340 EBX:40d773f0 ECX:41af221c EDX:407e209c
ESI:40d71df0 EDI:00000001
Stack dump:
0x407e20e0 (NTDLL.DLL.memcpy+0x54d8c0):  40d37174 407e20f8 00000002 40accdac
0x407e20f0 (NTDLL.DLL.memcpy+0x54d8d0):  40062255 40accdac 00000000 00000000
0x407e2100 (NTDLL.DLL.memcpy+0x54d8e0):  00000000 ffffffff 00000000 00000000
0x407e2110 (NTDLL.DLL.memcpy+0x54d8f0):  403a62b4 407e2134 40aa8433 4039c380
0x407e2120 (NTDLL.DLL.memcpy+0x54d900):  00000000 4039c380 417cd278 00000001
0x407e2130 (NTDLL.DLL.memcpy+0x54d910):  00000864 407e2170 417acc9a 00000864
0x407e2140 (NTDLL.DLL.memcpy+0x54d920):
Backtrace:
=>0 0x00000000 (ebp=407e21b4)
1 0x40d37174 (OPENGL32.DLL.wglGetSwapIntervalEXT+0x4c0 in libopengl32.so) (ebp =407e21b4, null call assumed)
2 0x40d372ed (OPENGL32.DLL.EntryPoint+0x81 in libopengl32.so) (ebp=407e21c0)
3 0x4008ce67 (KERNEL32.DLL.__wine_call_from_16_regs+0x6887 in libntdll.so) (eb p=407e21e4)
4 0x400885d5 (KERNEL32.DLL.__wine_call_from_16_regs+0x1ff5 in libntdll.so) (eb p=407e220c)
5 0x40088753 (KERNEL32.DLL.__wine_call_from_16_regs+0x2173 in libntdll.so) (eb p=407e2234)
6 0x4008879b (KERNEL32.DLL.__wine_call_from_16_regs+0x21bb in libntdll.so) (eb p=407e2258)
7 0x400ca370 (NTDLL.DLL.wine_server_call+0x1de4 in libntdll.so) (ebp=407e2304)
8 0x400ca513 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407e2438)
9 0x4035c361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407e24b8)
10 0x402f1bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Address                 Module  Name
0x00400000-00ae7000     (PE)    C:\Program Files\World of Warcraft\WoW.exe
0x10000000-10069000     (PE)    C:\PROGRAM FILES\WORLD OF WARCRAFT\DIVXDECODER.D LL
0x40056000-40058000     (PE)    NTDLL.DLL
0x407f3000-40839000     (PE)    C:\WINDOWS\SYSTEM32\MSVCRT.DLL
0x4086c000-4086e000     (PE)    KERNEL32.DLL
0x408c8000-408ca000     (PE)    COMCTL32.DLL
0x40976000-40978000     (PE)    USER32.DLL
0x40a86000-40a88000     (PE)    GDI32.DLL
0x40af0000-40af2000     (PE)    ADVAPI32.DLL
0x40b2b000-40b2d000     (PE)    SHELL32.DLL
0x40beb000-40bed000     (PE)    OLE32.DLL
0x40c54000-40c56000     (PE)    RPCRT4.DLL
0x40c94000-40c96000     (PE)    SHLWAPI.DLL
0x40cbb000-40cbd000     (PE)    WSOCK32.DLL
0x40ccc000-40cce000     (PE)    WS2_32.DLL
0x40ce3000-40ce5000     (PE)    IPHLPAPI.DLL
0x40d32000-40d34000     (PE)    OPENGL32.DLL
0x417a0000-417a2000     (PE)    DDRAW.DLL
0x417d5000-417d7000     (PE)    IMM32.DLL
0x417ec000-417ee000     (PE)    WINMM.DLL
0x41834000-418c4000     (PE)    C:\PROGRAM FILES\WORLD OF WARCRAFT\FMOD.DLL
0x418c9000-418cb000     (PE)    MSACM32.DLL
0x418e1000-418e3000     (PE)    WININET.DLL
0x41ae4000-41ae6000     (PE)    X11DRV.DLL
Threads:
process  tid      prio
00000001 (D) C:\Program Files\World of Warcraft\WoW.exe
00000002    0 <==
WineDbg terminated on pid 1

```

---

