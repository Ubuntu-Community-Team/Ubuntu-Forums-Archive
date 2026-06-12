---
title: "wine problem"
date: 2006-01-15
forum: General Help
---

### Post by gachejad on 2006-01-15
can somebody teach me how to activate wine. whenever i type wine in the terminal this msg. pops-up

>>wine: creating configuration directory '/home/chichi/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ec3713f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ec3713f).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ec3713f ESP:7faffc8c EBP:7faffcc8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c0d29f8 ECX:b7f8a900 EDX:7c01d5b0
 ESI:7c01d5b0 EDI:7c01d5b0
Stack dump:
0x7faffc8c:  7c01d5b0 7ec6c9a0 7c01d5b0 7ec35ab6
0x7faffc9c:  7c01d5b0 7c01d5b0 7ed447d0 7c0d2a10
0x7faffcac:  7ec99883 7c01d5b0 7c0d2a14 00000001
0x7faffcbc:  7ede05cc 7ede93d8 00000001 7faffcdc
0x7faffccc:  7edace34 7c01d5b0 7ede05cc 7beffc3c
0x7faffcdc:  7faffe10 7edc2541 7beb382e 7faffdac
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ec3713f in libgl.so.1 (+0x3613f) (0x7ec3713f)
  2 0x7edace34 X11DRV_GDI_Finalize+0x24 in winex11 (0x7edace34)
  3 0x7edc2541 DllMain+0x41 in winex11 (0x7edc2541)
  4 0x7edd0f58 in winex11 (+0x50f58) (0x7edd0f58)
  5 0x7bec00b5 call_dll_entry_point+0x15 in ntdll (0x7bec00b5)
  6 0x7bec0e6a in ntdll (+0x20e6a) (0x7bec0e6a)
  7 0x7bec1124 in ntdll (+0x21124) (0x7bec1124)
  8 0x7fcdc729 ExitProcess+0x19 in kernel32 (0x7fcdc729)
  9 0x7fb1ea4c in rundll32 (+0xea4c) (0x7fb1ea4c)
  10 0x7fcddc67 in kernel32 (+0x4dc67) (0x7fcddc67)
  11 0xb7fa3c17 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7fa3c17)
0x7ec3713f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (90 modules)
ELF     0x7be8c000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7db9a000-7dbb0000     Deferred        advpack<elf>
  \-PE  0x7dba0000-7dbb0000     \               advpack
ELF     0x7dce9000-7dd3e000     Deferred        shlwapi<elf>
  \-PE  0x7dd00000-7dd3e000     \               shlwapi
ELF     0x7dd3e000-7ddfd000     Deferred        shell32<elf>
  \-PE  0x7dd50000-7ddfd000     \               shell32
ELF     0x7ddfd000-7de2d000     Deferred        uxtheme<elf>
  \-PE  0x7de00000-7de2d000     \               uxtheme
ELF     0x7de2d000-7dedc000     Deferred        comctl32<elf>
  \-PE  0x7de40000-7dedc000     \               comctl32
ELF     0x7dedc000-7df27000     Deferred        dsound<elf>
  \-PE  0x7def0000-7df27000     \               dsound
ELF     0x7df27000-7df80000     Deferred        quartz<elf>
  \-PE  0x7df40000-7df80000     \               quartz
ELF     0x7e0a0000-7e0b5000     Deferred        midimap<elf>
  \-PE  0x7e0b0000-7e0b5000     \               midimap
ELF     0x7e0b5000-7e0cc000     Deferred        msacm<elf>
  \-PE  0x7e0c0000-7e0cc000     \               msacm
ELF     0x7e0cc000-7e10e000     Deferred        wineoss<elf>
  \-PE  0x7e0e0000-7e10e000     \               wineoss
ELF     0x7e130000-7e154000     Deferred        msvfw32<elf>
  \-PE  0x7e140000-7e154000     \               msvfw32
ELF     0x7e154000-7e1e1000     Deferred        oleaut32<elf>
  \-PE  0x7e170000-7e1e1000     \               oleaut32
ELF     0x7e1e1000-7e267000     Deferred        ole32<elf>
  \-PE  0x7e200000-7e267000     \               ole32
ELF     0x7e267000-7e2e8000     Deferred        winmm<elf>
  \-PE  0x7e270000-7e2e8000     \               winmm
ELF     0x7e2e8000-7e30a000     Deferred        msacm32<elf>
  \-PE  0x7e2f0000-7e30a000     \               msacm32
ELF     0x7e30c000-7e320000     Deferred        avicap32<elf>
  \-PE  0x7e310000-7e320000     \               avicap32
ELF     0x7e320000-7e346000     Deferred        devenum<elf>
  \-PE  0x7e330000-7e346000     \               devenum
ELF     0x7e346000-7e364000     Deferred        iphlpapi<elf>
  \-PE  0x7e350000-7e364000     \               iphlpapi
ELF     0x7e364000-7e3a8000     Deferred        rpcrt4<elf>
  \-PE  0x7e370000-7e3a8000     \               rpcrt4
ELF     0x7e3a8000-7e3bc000     Deferred        lz32<elf>
  \-PE  0x7e3b0000-7e3bc000     \               lz32
ELF     0x7e3bc000-7e3d4000     Deferred        version<elf>
  \-PE  0x7e3c0000-7e3d4000     \               version
ELF     0x7e3d4000-7e426000     Deferred        setupapi<elf>
  \-PE  0x7e3e0000-7e426000     \               setupapi
ELF     0x7e480000-7e484000     Deferred        libxfixes.so.3
ELF     0x7e484000-7e48d000     Deferred        libxcursor.so.1
ELF     0x7e48d000-7e490000     Deferred        libxrandr.so.2
ELF     0x7e490000-7e498000     Deferred        libxrender.so.1
ELF     0x7e498000-7ec01000     Deferred        libglcore.so.1
ELF     0x7ec01000-7ec80000     Export          libgl.so.1
ELF     0x7ec80000-7ec84000     Deferred        libxdmcp.so.6
ELF     0x7ec84000-7ec87000     Deferred        libxau.so.6
ELF     0x7ec87000-7ed47000     Deferred        libx11.so.6
ELF     0x7ed47000-7ed54000     Deferred        libxext.so.6
ELF     0x7ed54000-7ed6d000     Deferred        libice.so.6
ELF     0x7ed6d000-7edea000     Export          winex11<elf>
  \-PE  0x7ed80000-7edea000     \               winex11
ELF     0x7edea000-7ee09000     Deferred        libexpat.so.1
ELF     0x7ee09000-7ee37000     Deferred        libfontconfig.so.1
ELF     0x7ee37000-7ee4b000     Deferred        libz.so.1
ELF     0x7ee4b000-7eeb5000     Deferred        libfreetype.so.6
ELF     0x7eeb5000-7eef1000     Deferred        advapi32<elf>
  \-PE  0x7eec0000-7eef1000     \               advapi32
ELF     0x7efd7000-7f8d7000     Deferred        gdi32<elf>
  \-PE  0x7f020000-7f8d7000     \               gdi32
ELF     0x7f8d7000-7f9f0000     Deferred        user32<elf>
  \-PE  0x7f8f0000-7f9f0000     \               user32
ELF     0x7fb02000-7fb07000     Deferred        libxxf86vm.so.1
ELF     0x7fb07000-7fb0c000     Deferred        libxxf86dga.so.1
ELF     0x7fb0c000-7fb20000     Export          rundll32<elf>
  \-PE  0x7fb10000-7fb20000     \               rundll32
ELF     0x7fb21000-7fb2c000     Deferred        libgcc_s.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe82000-7fe89000     Deferred        libsm.so.6
ELF     0x7fe89000-7fe93000     Deferred        libnss_files.so.2
ELF     0x7fe93000-7fe9c000     Deferred        libnss_nis.so.2
ELF     0x7fe9c000-7feb1000     Deferred        libnsl.so.1
ELF     0x7feb1000-7feba000     Deferred        libnss_compat.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e5c000-b7e5f000     Deferred        libdl.so.2
ELF     0xb7e5f000-b7f8d000     Deferred        libc.so.6
ELF     0xb7f8d000-b7f9f000     Deferred        libpthread.so.0
ELF     0xb7f9f000-b7fb9000     Export          libwine.so.1
ELF     0xb7fb9000-b7fbb000     Deferred        libnvidia-tls.so.1
ELF     0xb7fc6000-b7fdc000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8


>>i just couldn't make sense of it...:confused:

---

