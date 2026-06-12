---
title: "Wine Problem!"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Majes on 2006-02-18
Hi all.

Im kinda noobish in ubuntu, and in english, so, i will try to explain myself as best as I can.

I have installed wine, and when I try to execute a program ($ wine installer.exe)

it doesnt work, it gives me this log.

> majes@ubuntu:~$ wine /home/majes/Desktop/RCT_Setup.exe
wine: creating configuration directory '/home/majes/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ebe04ff (t hread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7 ebe04ff).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ebe04ff ESP:7faafc2c EBP:7faafc68 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c119690 ECX:b7f55900 EDX:7c01d3a0
 ESI:7c01d3a0 EDI:7c01d3a0
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ebe04ff in libgl.so.1 (+0x304ff) (0x7ebe04ff)
  2 0x7ed4edb7 X11DRV_GDI_Finalize+0x27 in winex11 (0x7ed4edb7)
  3 0x7ed65251 DllMain+0x41 in winex11 (0x7ed65251)
  4 0x7ed7432c in winex11 (+0x5432c) (0x7ed7432c)
  5 0x7bebc0e5 call_dll_entry_point+0x15 in ntdll (0x7bebc0e5)
  6 0x7bebcefa in ntdll (+0x1cefa) (0x7bebcefa)
  7 0x7bebd1da in ntdll (+0x1d1da) (0x7bebd1da)
  8 0x7fcdb799 ExitProcess+0x19 in kernel32 (0x7fcdb799)
  9 0x7faceb36 in rundll32 (+0xeb36) (0x7faceb36)
  10 0x7fcdce0f in kernel32 (+0x4ce0f) (0x7fcdce0f)
  11 0xb7f6f237 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f6f237)
0x7ebe04ff: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (94 modules)
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d9c9000-7d9e0000     Deferred        advpack<elf>
  \-PE  0x7d9d0000-7d9e0000     \               advpack
ELF     0x7db23000-7db7b000     Deferred        shlwapi<elf>
  \-PE  0x7db40000-7db7b000     \               shlwapi
ELF     0x7db7b000-7dc40000     Deferred        shell32<elf>
  \-PE  0x7db90000-7dc40000     \               shell32
ELF     0x7dc40000-7dc71000     Deferred        uxtheme<elf>
  \-PE  0x7dc50000-7dc71000     \               uxtheme
ELF     0x7dc71000-7dd25000     Deferred        comctl32<elf>
  \-PE  0x7dc80000-7dd25000     \               comctl32
ELF     0x7dd25000-7dd75000     Deferred        dsound<elf>
  \-PE  0x7dd40000-7dd75000     \               dsound
ELF     0x7dd75000-7ddd0000     Deferred        quartz<elf>
  \-PE  0x7dd90000-7ddd0000     \               quartz
ELF     0x7dee9000-7defe000     Deferred        midimap<elf>
  \-PE  0x7def0000-7defe000     \               midimap
ELF     0x7defe000-7df15000     Deferred        msacm<elf>
  \-PE  0x7df00000-7df15000     \               msacm
ELF     0x7df15000-7df58000     Deferred        wineoss<elf>
  \-PE  0x7df30000-7df58000     \               wineoss
ELF     0x7df7b000-7dfa0000     Deferred        msvfw32<elf>
  \-PE  0x7df80000-7dfa0000     \               msvfw32
ELF     0x7dfa0000-7e031000     Deferred        oleaut32<elf>
  \-PE  0x7dfc0000-7e031000     \               oleaut32
ELF     0x7e031000-7e0bc000     Deferred        ole32<elf>
  \-PE  0x7e050000-7e0bc000     \               ole32
ELF     0x7e0bc000-7e143000     Deferred        winmm<elf>
  \-PE  0x7e0d0000-7e143000     \               winmm
ELF     0x7e15a000-7e180000     Deferred        devenum<elf>
  \-PE  0x7e170000-7e180000     \               devenum
ELF     0x7e290000-7e2a4000     Deferred        avicap32<elf>
  \-PE  0x7e2a0000-7e2a4000     \               avicap32
ELF     0x7e2a4000-7e2c8000     Deferred        msacm32<elf>
  \-PE  0x7e2b0000-7e2c8000     \               msacm32
ELF     0x7e2c8000-7e2e6000     Deferred        iphlpapi<elf>
  \-PE  0x7e2d0000-7e2e6000     \               iphlpapi
ELF     0x7e2e6000-7e32e000     Deferred        rpcrt4<elf>
  \-PE  0x7e300000-7e32e000     \               rpcrt4
ELF     0x7e32e000-7e342000     Deferred        lz32<elf>
  \-PE  0x7e330000-7e342000     \               lz32
ELF     0x7e342000-7e35b000     Deferred        version<elf>
  \-PE  0x7e350000-7e35b000     \               version
ELF     0x7e35b000-7e3ae000     Deferred        setupapi<elf>
  \-PE  0x7e370000-7e3ae000     \               setupapi
ELF     0x7e408000-7e40c000     Deferred        libxfixes.so.3
ELF     0x7e40c000-7e415000     Deferred        libxcursor.so.1
ELF     0x7e415000-7e431000     Deferred        imm32<elf>
  \-PE  0x7e420000-7e431000     \               imm32
ELF     0x7e431000-7e44d000     Deferred        ximcp.so.2
ELF     0x7e44d000-7e455000     Deferred        libxrender.so.1
ELF     0x7e45f000-7ebb0000     Deferred        libglcore.so.1
ELF     0x7ebb0000-7ec28000     Export          libgl.so.1
ELF     0x7ec28000-7ece8000     Deferred        libx11.so.6
ELF     0x7ece8000-7ecf5000     Deferred        libxext.so.6
ELF     0x7ecf5000-7ed0e000     Deferred        libice.so.6
ELF     0x7ed0e000-7ed8d000     Export          winex11<elf>
  \-PE  0x7ed20000-7ed8d000     \               winex11
ELF     0x7ed8d000-7edac000     Deferred        libexpat.so.1
ELF     0x7edac000-7edda000     Deferred        libfontconfig.so.1
ELF     0x7edda000-7edee000     Deferred        libz.so.1
ELF     0x7edee000-7ee58000     Deferred        libfreetype.so.6
ELF     0x7ee58000-7ee95000     Deferred        advapi32<elf>
  \-PE  0x7ee60000-7ee95000     \               advapi32
ELF     0x7ef7b000-7f87e000     Deferred        gdi32<elf>
  \-PE  0x7efc0000-7f87e000     \               gdi32
ELF     0x7f87e000-7f9a0000     Deferred        user32<elf>
  \-PE  0x7f8a0000-7f9a0000     \               user32
ELF     0x7fab0000-7fab4000     Deferred        libxdmcp.so.6
ELF     0x7fab4000-7fab7000     Deferred        libxau.so.6
ELF     0x7fab7000-7fabc000     Deferred        libxxf86vm.so.1
ELF     0x7fabc000-7fad0000     Export          rundll32<elf>
  \-PE  0x7fac0000-7fad0000     \               rundll32
ELF     0x7fad1000-7fad6000     Deferred        libxxf86dga.so.1
ELF     0x7fad6000-7fae1000     Deferred        libgcc_s.so.1
ELF     0x7fc71000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe82000-7fe89000     Deferred        libsm.so.6
ELF     0x7fe89000-7fe93000     Deferred        libnss_files.so.2
ELF     0x7fe93000-7fe9c000     Deferred        libnss_nis.so.2
ELF     0x7fe9c000-7feb1000     Deferred        libnsl.so.1
ELF     0x7feb1000-7feba000     Deferred        libnss_compat.so.2
ELF     0x7febd000-7febf000     Deferred        xlcutf8load.so.2
ELF     0x7febf000-7fec2000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e27000-b7e2a000     Deferred        libdl.so.2
ELF     0xb7e2a000-b7f58000     Deferred        libc.so.6
ELF     0xb7f58000-b7f6a000     Deferred        libpthread.so.0
ELF     0xb7f6a000-b7f84000     Export          libwine.so.1
ELF     0xb7f84000-b7f86000     Deferred        libnvidia-tls.so.1
ELF     0xb7f91000-b7fa7000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==
WineDbg terminated on pid 0x8


What could it be ?

Thanks.

---

