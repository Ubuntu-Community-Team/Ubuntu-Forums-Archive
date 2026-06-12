---
title: "Problems to run Ragnarok Online"
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by ][FëaNarO][ on 2006-07-11
Hello everyone, this is my first post, so be clement please. This being said lets start with the question, I'm a total n00b to playing games under Linux based systems and right now I'm about to break after 3 days of testing this distro and trying to make Ragnarok Online work, and there's no way for me do it. I think that the problems can be because I play in a private server with modified executables files. I've configured wine (version 0.9.9) to use a virtual desktop at 1024x768, the drives have been auto detected and I'm using the OSS audio driver. I didn't reinstalled the game, I'm using a previous installed version.

My system:

CPU: 	       	   Pentium IV 3.0E
Mobo:          	   ABIT VT7
Graphics Card: 	   Sapphire ATI RADEON x1600Pro
RAM:           	   2 x 512MB DDR 400 (PC3200) Dual Channel
Hard Drives:   	   40GB Seagate Barracuda IDE 133
	       	   160GB Seagate Barracuda IDE 133
	       	   160GB Maxtor 6 SATA I
	       	   300GB Maxtor 6 SATA I
Power Supply:      Cooler Master 400W
Operating Systems: Windows XP Pro SP2, updated daily
		   Debian Linux Unstable, updated daily
		   Ubuntu Linux 6.06 LTS (Dapper Drake), updated daily
Monitor:	   NEC MultiSync V721 17"



This is what i get when trying to run it:

```
wine: Call from 0x402042 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402042 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7ff9c137).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ff9c137 ESP:7fb9e714 EBP:7fb9e778 EFLAGS:00200206(   - 00      - -IP1)
 EAX:0000194e EBX:7ffd51fc ECX:7fd5efa0 EDX:7fcf0024
 ESI:7fb9e720 EDI:00000001
Stack dump:
0x7fb9e714:  00010026 00000000 00000000 80000100
0x7fb9e724:  00000001 00000000 00402042 00000002
0x7fb9e734:  0041de52 0000194e 00000002 00000000
0x7fb9e744:  7f9f7dc0 7f9dd664 7fcf0000 7f43d524
0x7fb9e754:  ffffffff 00000001 7fb9e77c 7f424263
0x7fb9e764:  7fcf0000 00000000 000004c8 7f8808b2
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ff9c137 call_dll_entry_point+0x67 in ntdll (0x7ff9c137)
  2 0x00402042 in futur0 (+0x2042) (0x00402042)
  3 0x00000000 (0x00000000)
0x7ff9c137 call_dll_entry_point+0x67 in ntdll: subl     $4,%esp
Modules:
Module  Address                 Debug info      Name (67 modules)
PE      0x00400000-00427000     Export          futur0
PE      0x5f400000-5f4ed000     Deferred        mfc42
PE      0x780c0000-78121000     Deferred        msvcp60
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7de29000-7de5a000     Deferred        uxtheme<elf>
  \-PE  0x7de30000-7de5a000     \               uxtheme
ELF     0x7de78000-7de80000     Deferred        libxrender.so.1
ELF     0x7de80000-7de9c000     Deferred        imm32<elf>
  \-PE  0x7de90000-7de9c000     \               imm32
ELF     0x7e72c000-7e734000     Deferred        librt.so.1
ELF     0x7e737000-7e740000     Deferred        libxcursor.so.1
ELF     0x7e7fa000-7f0f5000     Deferred        fglrx_dri.so
ELF     0x7f0f5000-7f195000     Deferred        libgl.so.1
ELF     0x7f195000-7f27b000     Deferred        libx11.so.6
ELF     0x7f27b000-7f293000     Deferred        libice.so.6
ELF     0x7f293000-7f316000     Deferred        winex11<elf>
  \-PE  0x7f2a0000-7f316000     \               winex11
ELF     0x7f316000-7f335000     Deferred        libexpat.so.1
ELF     0x7f335000-7f363000     Deferred        libfontconfig.so.1
ELF     0x7f363000-7f377000     Deferred        libz.so.1
ELF     0x7f377000-7f3e0000     Deferred        libfreetype.so.6
ELF     0x7f3f3000-7f3f7000     Deferred        libxfixes.so.3
ELF     0x7f3f7000-7f458000     Deferred        msvcrt<elf>
  \-PE  0x7f410000-7f458000     \               msvcrt
ELF     0x7f458000-7f518000     Deferred        comctl32<elf>
  \-PE  0x7f460000-7f518000     \               comctl32
ELF     0x7f518000-7f5e4000     Deferred        shell32<elf>
  \-PE  0x7f530000-7f5e4000     \               shell32
ELF     0x7f5e4000-7f603000     Deferred        iphlpapi<elf>
  \-PE  0x7f5f0000-7f603000     \               iphlpapi
ELF     0x7f603000-7f64c000     Deferred        rpcrt4<elf>
  \-PE  0x7f610000-7f64c000     \               rpcrt4
ELF     0x7f64c000-7f6dd000     Deferred        ole32<elf>
  \-PE  0x7f660000-7f6dd000     \               ole32
ELF     0x7f6dd000-7f738000     Deferred        shlwapi<elf>
  \-PE  0x7f6f0000-7f738000     \               shlwapi
ELF     0x7f738000-7f778000     Deferred        advapi32<elf>
  \-PE  0x7f740000-7f778000     \               advapi32
ELF     0x7f84d000-7f8fe000     Deferred        gdi32<elf>
  \-PE  0x7f860000-7f8fe000     \               gdi32
ELF     0x7f8fe000-7fa2a000     Deferred        user32<elf>
  \-PE  0x7f920000-7fa2a000     \               user32
ELF     0x7fa2a000-7fa49000     Deferred        mpr<elf>
  \-PE  0x7fa30000-7fa49000     \               mpr
ELF     0x7fa49000-7fa90000     Deferred        wininet<elf>
  \-PE  0x7fa50000-7fa90000     \               wininet
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb1000-7fbb6000     Deferred        libxxf86vm.so.1
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86dga.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe03000-7fe0d000     Deferred        libgcc_s.so.1
ELF     0x7fe0d000-7fe17000     Deferred        libnss_files.so.2
ELF     0x7fe17000-7fe20000     Deferred        libnss_nis.so.2
ELF     0x7fe20000-7fe35000     Deferred        libnsl.so.1
ELF     0x7fe35000-7fe3e000     Deferred        libnss_compat.so.2
ELF     0x7fe3f000-7fe42000     Deferred        libxau.so.6
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e2a000-b7e2d000     Deferred        libdl.so.2
ELF     0xb7e2d000-b7f5c000     Deferred        libc.so.6
ELF     0xb7f5c000-b7f6e000     Deferred        libpthread.so.0
ELF     0xb7f7b000-b7f95000     Deferred        libwine.so.1
ELF     0xb7f98000-b7fae000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) L:\games\Gravity\ro\futur0.exe
        0000000a    0
        00000009    0 <==

```

Thanks in advace,

                ][FëaNaro][

---

### Post by fuzzypig on 2007-06-25
Looks like you need a new version of MFC42.dll. Get it at [http://www.gn0me.org/mfc42.dll](http://www.gn0me.org/mfc42.dll)
put it in ~/.wine/drive_c/windows/system32

---

### Post by Lukasz Tarkowski on 2008-03-01
That didn't fix my problem [http://www.gn0me.org/mfc42.dll](http://www.gn0me.org/mfc42.dll) :(

---

