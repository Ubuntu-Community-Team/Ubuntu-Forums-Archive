---
title: "Missing OPENGL32.dll"
date: 2005-06-19
forum: Gaming &amp; Leisure
---

### Post by TheRealEdwin on 2005-06-19
Trying to get WoW running but I get this error. Obviously OPENGL32.dll is missing but I can't find anything on how to install/get it.

```
err:module:PE_fixup_imports Module (file) OPENGL32.dll (which is needed by G:\media\windows\World of Warcraft\WoW.exe) not found
```

Edit: Nevermind, just threw the file into the folder and fixed that error but caused more. Here is the new error:

with the cvscedega command
```
fixme:win32:PE_CreateModule Load Configuration directory ignored
err:win32:PE_fixup_imports No implementation for KERNEL32.dll.562(IsWow64Process) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GDI32.dll.324(GdiSwapBuffers) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GDI32.dll.320(GdiSetPixelFormat) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GDI32.dll.261(GdiDescribePixelFormat) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.49(gluTessProperty) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.47(gluTessEndPolygon) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.46(gluTessEndContour) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.43(gluTessBeginContour) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.44(gluTessBeginPolygon) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
err:win32:PE_fixup_imports No implementation for GLU32.dll.48(gluTessNormal) imported from G:\media\windows\World of Warcraft\opengl32.dll, setting to 0xdeadbeef
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:seh:EXC_RtlRaiseException possibly COM stub exception at 0xdeadbeef
wine: Unhandled exception, starting debugger...
err:ntdll:MODULE_THREAD_WaitThreadModuleSafe this should never happen. (unless wine crashed)

```

With the wine command:
```
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7bebda88).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7bebda88 ESP:7b9bfbb0 EBP:7b9bfc08 EFLAGS:00000216(   - 00      - IAP1)
 EAX:5eda22da EBX:7befcd00 ECX:7bc1001c EDX:00000050
 ESI:7b9bfbb0 EDI:00000001
Stack dump:
0x7b9bfbb0:  80000100 00000001 00000000 5ed09ec5
0x7b9bfbc0:  00000002 5eda2576 5eda22da 5edac720
0x7b9bfbd0:  00000001 7b9bfbf0 7beb03aa 7bc10000
0x7b9bfbe0:  00000002 00000020 7befcd00 7bb8b230
0x7b9bfbf0:  7b9bfc04 7beb0315 5edac720 00000000
0x7b9bfc00:  00000002 7bb8b230 7b9bfd60 5ed09ec5
Backtrace:
=>1 0x7bebda88 stub_entry_point+0x58(dll=0x5eda2576, name=0x5eda22da) [loader.c:187] in ntdll (0x7b9bfc08)
fixme:dbghelp:sffip_cb NIY on 'opengl32.pdb'
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x7b9bfd60)
  3 0x5ed0a366 EntryPoint+0x44 in opengl32 (0x7b9bfd6c)
  4 0x7bebda2a call_dll_entry_point+0x12 in ntdll (0x7b9bfd84)
  5 0x7bebefef MODULE_InitDLL+0x10f(wm=0x7bc112a8, reason=0x1, lpReserved=0x1) [/home/edwin/cvs/wine/dlls/ntdll/loader.c:827] in ntdll (0x7b9bfe00)
  6 0x7bebf1c2 process_attach+0xa2(wm=0x7bc112a8, lpReserved=0x1) [/home/edwin/cvs/wine/dlls/ntdll/loader.c:900] in ntdll (0x7b9bfe34)
  7 0x7bebf2ea process_attach+0x1ca(wm=0x7bc10798, lpReserved=0x1) [/home/edwin/cvs/wine/dlls/ntdll/loader.c:892] in ntdll (0x7b9bfe68)
  8 0x7bec1a7b LdrInitializeThunk+0x22b(main_file=0x1c, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/edwin/cvs/wine/dlls/ntdll/loader.c:1996] in ntdll (0x7b9bff20)
  9 0x7bb7719b start_process+0xbb(arg=0x0) [/home/edwin/cvs/wine/dlls/kernel/process.c:1034] in kernel32 (0x7b9bfff4)
  10 0xb7fc91b1 wine_switch_to_stack in libwine.so.1 (0x00000000)
0x7bebda88 stub_entry_point+0x58 [loader.c:187] in ntdll: subl  $4,%esp
Unable to open file 'loader.c'
Modules:
Module  Address                 Debug info      Name (78 modules)
PE      0x00400000-00acd000     Deferred        wow
PE      0x10000000-10069000     Deferred        divxdecoder
PE      0x5ed00000-5edcc000     Export          opengl32
ELF     0x7a667000-7a687000     Deferred        mpr<elf>
  \-PE  0x7a670000-7a687000     \               mpr
ELF     0x7a687000-7a6cc000     Deferred        wininet<elf>
  \-PE  0x7a690000-7a6cc000     \               wininet
ELF     0x7a6cc000-7a6f0000     Deferred        msacm32<elf>
  \-PE  0x7a6d0000-7a6f0000     \               msacm32
PE      0x7a6f0000-7a780000     Deferred        fmod
ELF     0x7a788000-7a809000     Deferred        winmm<elf>
  \-PE  0x7a7a0000-7a809000     \               winmm
ELF     0x7a809000-7a828000     Deferred        imm32<elf>
  \-PE  0x7a810000-7a828000     \               imm32
ELF     0x7a828000-7a86d000     Deferred        ddraw<elf>
  \-PE  0x7a840000-7a86d000     \               ddraw
ELF     0x7a905000-7a907000     Deferred        libnvidia-tls.so.1
ELF     0x7a907000-7b058000     Deferred        libglcore.so.1
ELF     0x7b058000-7b063000     Deferred        libgcc_s.so.1
ELF     0x7b11d000-7b195000     Deferred        libgl.so.1
ELF     0x7b195000-7b20b000     Deferred        libglu.so.1
ELF     0x7b20b000-7b2d0000     Deferred        libx11.so.6
ELF     0x7b2d0000-7b2dd000     Deferred        libxext.so.6
ELF     0x7b2dd000-7b2f5000     Deferred        libice.so.6
ELF     0x7b2f5000-7b2fe000     Deferred        libsm.so.6
ELF     0x7b309000-7b320000     Deferred        glu32<elf>
  \-PE  0x7b310000-7b320000     \               glu32
ELF     0x7b332000-7b35c000     Deferred        ws2_32<elf>
  \-PE  0x7b340000-7b35c000     \               ws2_32
ELF     0x7b35c000-7b378000     Deferred        wsock32<elf>
  \-PE  0x7b360000-7b378000     \               wsock32
ELF     0x7b378000-7b398000     Deferred        iphlpapi<elf>
  \-PE  0x7b380000-7b398000     \               iphlpapi
ELF     0x7b398000-7b3e2000     Deferred        rpcrt4<elf>
  \-PE  0x7b3b0000-7b3e2000     \               rpcrt4
ELF     0x7b3e2000-7b472000     Deferred        ole32<elf>
  \-PE  0x7b400000-7b472000     \               ole32
ELF     0x7b472000-7b4d0000     Deferred        shlwapi<elf>
  \-PE  0x7b490000-7b4d0000     \               shlwapi
ELF     0x7b4d0000-7b598000     Deferred        shell32<elf>
  \-PE  0x7b4f0000-7b598000     \               shell32
ELF     0x7b598000-7b5d8000     Deferred        advapi32<elf>
  \-PE  0x7b5b0000-7b5d8000     \               advapi32
ELF     0x7b5d8000-7b667000     Deferred        gdi32<elf>
  \-PE  0x7b5f0000-7b667000     \               gdi32
ELF     0x7b667000-7b79a000     Deferred        user32<elf>
  \-PE  0x7b690000-7b79a000     \               user32
ELF     0x7b79a000-7b85c000     Deferred        comctl32<elf>
  \-PE  0x7b7b0000-7b85c000     \               comctl32
ELF     0x7b85c000-7b8c0000     Deferred        msvcrt<elf>
  \-PE  0x7b870000-7b8c0000     \               msvcrt
ELF     0x7bafe000-7bc10000     Stabs           kernel32<elf>
  \-PE  0x7bb30000-7bc10000     \               kernel32
ELF     0x7bd2b000-7bd34000     Deferred        libnss_files.so.2
ELF     0x7bd34000-7bd3d000     Deferred        libnss_nis.so.2
ELF     0x7bd3d000-7bd51000     Deferred        libnsl.so.1
ELF     0x7bd51000-7bd59000     Deferred        libnss_compat.so.2
ELF     0x7bd64000-7bd85000     Deferred        libm.so.6
ELF     0x7bd85000-7be7a000     Deferred        libwine_unicode.so.1
ELF     0x7be85000-7bf00000     Stabs           ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7fe66000-7fe82000     Deferred        ximcp.so.2
ELF     0x7fe82000-7fe86000     Deferred        libxrandr.so.2
ELF     0x7fe91000-7fe9a000     Deferred        libxcursor.so.1
ELF     0x7fe9a000-7fea2000     Deferred        libxrender.so.1
ELF     0x7feab000-7fead000     Deferred        xlcutf8load.so.2
ELF     0x7fead000-7ff30000     Deferred        winex11.drv<elf>
  \-PE  0x7fec0000-7ff30000     \               winex11.drv
ELF     0x7ff30000-7ff50000     Deferred        libexpat.so.1
ELF     0x7ff50000-7ff77000     Deferred        libfontconfig.so.1
ELF     0x7ff77000-7ff88000     Deferred        libz.so.1
ELF     0x7ff88000-7fff5000     Deferred        libfreetype.so.6
ELF     0xb7e83000-b7e86000     Deferred        libdl.so.2
ELF     0xb7e87000-b7fb4000     Deferred        libc.so.6
ELF     0xb7fb4000-b7fc4000     Deferred        libpthread.so.0
ELF     0xb7fc4000-b7fdd000     DIA             libwine.so.1
ELF     0xb7fea000-b8000000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\windows\World of Warcraft\WoW.exe
        00000009    0 <==
WineDbg terminated on pid 0x8

```

---

### Post by jdodson on 2005-06-19
what version of cedega are you using?

---

### Post by TheRealEdwin on 2005-06-19
[QUOTE=jdodson]what version of cedega are you using?[/QUOTE]
 CedegaCVS as stated with this guide: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

---

### Post by jdodson on 2005-06-19
hmmmm.  i think, due to debugging, and the fact that CVS might be unstable, i recommend using the releases of cedega.  i know they cost money, but its the best option available.

else, finding a wine howto for halflife 2.

---

