---
title: "Black and White 2 Wine Adventure"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by thunderduck3141 on 2006-07-15
after much toil and dll searching, no cd patch applying and a couple pots of coffe, i have gotten the output from wine for bw2 to this:

[email]h4x0r@Mainframe:~/.wine[/email]/drive_c/Program Files/Lionhead Studios/Black & White 2$ wine white.exe
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
wine: Call from 0x611c68 to unimplemented function kernel32.dll.HeapSetInformation, aborting
wine: Unimplemented function kernel32.dll.HeapSetInformation called at address 0x611c68 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function kernel32.dll.HeapSetInformation called in 32-bit code (0x7ff98067).
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for ntdll<elf>
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7ff98067 ESP:7fc8fc4c EBP:7fc8fcb0 EFLAGS:00200206(   - 00      - -IP1)
 EAX:00d6c576 EBX:7ffd5288 ECX:0000000d EDX:7fc8fcdc
 ESI:7fc8fc58 EDI:7f83373f
Stack dump:
0x7fc8fc4c:  00000001 0000112e 00000000 80000100
0x7fc8fc5c:  00000001 00000000 00611c68 00000002
0x7fc8fc6c:  00d6be9a 00d6c576 7f83373f 7fc8fcb8
0x7fc8fc7c:  7f87716b 00010024 00000080 00000001
0x7fc8fc8c:  0000112e 00000000 00000000 7fc8fcb0
0x7fc8fc9c:  00000066 00000001 00000000 7f87711b
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7ff98067 stub_entry_point+0x4c(dll=0xd6be9a, name=0xd6c576) [/home/h4x0r/wine/dlls/ntdll/loader.c:184] in ntdll (0x7ff98067)
  2 0x00611c68 in white (+0x211c68) (0x00611c68)
  3 0x7ff9ccdc LdrInitializeThunk+0x548(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/h4x0r/wine/dlls/ntdll/loader.c:2163] in ntdll (0x7ff9ccdc)
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for kernel32<elf>
  4 0x7fd4a0f5 build_argv(cmdlineW=<register not in topmost frame>, reserved=0x0) [/home/h4x0r/wine/dlls/kernel/process.c:961] in kernel32 (0x7fd4a0f5)
fixme:dbghelp:elf_load_debug_info_from_map Alpha-support for Dwarf2 information for libwine.so.1
  5 0xb7ec61c3 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ec61c3)
0x7ff98067 stub_entry_point+0x4c [/home/h4x0r/wine/dlls/ntdll/loader.c:184] in ntdll: subl      $4,%esp
184         for (;;) RtlRaiseException( &rec );
Modules:
Module  Address                 Debug info      Name (87 modules)
PE      400000-242741e  Export          white
PE      18000000-18068000       Deferred        binkw32
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e13b000-7e150000       Deferred        midimap<elf>
  \-PE  7e140000-7e150000       \               midimap
ELF     7e28c000-7e2a4000       Deferred        msacm32<elf>
  \-PE  7e290000-7e2a4000       \               msacm32
ELF     7e2a4000-7e2e0000       Deferred        wineoss<elf>
  \-PE  7e2b0000-7e2e0000       \               wineoss
ELF     7e344000-7e375000       Deferred        uxtheme<elf>
  \-PE  7e350000-7e375000       \               uxtheme
ELF     7e375000-7e37e000       Deferred        libxcursor.so.1
ELF     7e38a000-7e405000       Deferred        winex11<elf>
  \-PE  7e3a0000-7e405000       \               winex11
ELF     7e405000-7e41a000       Deferred        psapi<elf>
  \-PE  7e410000-7e41a000       \               psapi
ELF     7e41a000-7e45f000       Deferred        dbghelp<elf>
  \-PE  7e420000-7e45f000       \               dbghelp
ELF     7e45f000-7e4c0000       Deferred        msvcrt<elf>
  \-PE  7e470000-7e4c0000       \               msvcrt
PE      7e4c0000-7e713000       Deferred        d3dx9_25
ELF     7e719000-7e742000       Deferred        d3d9<elf>
  \-PE  7e720000-7e742000       \               d3d9
ELF     7e742000-7e770000       Deferred        winspool<elf>
  \-PE  7e750000-7e770000       \               winspool
ELF     7e770000-7e80b000       Deferred        comdlg32<elf>
  \-PE  7e780000-7e80b000       \               comdlg32
ELF     7e80b000-7e893000       Deferred        winmm<elf>
  \-PE  7e820000-7e893000       \               winmm
ELF     7e893000-7e8e9000       Deferred        shlwapi<elf>
  \-PE  7e8a0000-7e8e9000       \               shlwapi
ELF     7e8e9000-7e9c2000       Deferred        shell32<elf>
  \-PE  7e900000-7e9c2000       \               shell32
ELF     7e9c2000-7e9ec000       Deferred        ws2_32<elf>
  \-PE  7e9d0000-7e9ec000       \               ws2_32
ELF     7e9ec000-7ea10000       Deferred        netapi32<elf>
  \-PE  7e9f0000-7ea10000       \               netapi32
ELF     7ea21000-7ea3d000       Deferred        imm32<elf>
  \-PE  7ea30000-7ea3d000       \               imm32
ELF     7ea3d000-7ea78000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea78000       \               dinput
ELF     7ea78000-7ea90000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea90000       \               dinput8
ELF     7ea90000-7eaaf000       Deferred        iphlpapi<elf>
  \-PE  7eaa0000-7eaaf000       \               iphlpapi
ELF     7eaaf000-7eafc000       Deferred        rpcrt4<elf>
  \-PE  7eac0000-7eafc000       \               rpcrt4
ELF     7eafc000-7eb8b000       Deferred        ole32<elf>
  \-PE  7eb10000-7eb8b000       \               ole32
ELF     7ecc1000-7f483000       Deferred        libglcore.so.1
ELF     7f483000-7f4f9000       Deferred        libglu.so.1
ELF     7f4f9000-7f57e000       Deferred        libgl.so.1
ELF     7f57e000-7f623000       Deferred        wined3d<elf>
  \-PE  7f590000-7f623000       \               wined3d
ELF     7f623000-7f709000       Deferred        libx11.so.6
ELF     7f709000-7f721000       Deferred        libice.so.6
ELF     7f721000-7f76a000       Deferred        ddraw<elf>
  \-PE  7f730000-7f76a000       \               ddraw
ELF     7f76a000-7f7ea000       Deferred        gdi32<elf>
  \-PE  7f780000-7f7ea000       \               gdi32
ELF     7f7ea000-7f91c000       Deferred        user32<elf>
  \-PE  7f800000-7f91c000       \               user32
ELF     7f91c000-7f9de000       Deferred        comctl32<elf>
  \-PE  7f930000-7f9de000       \               comctl32
ELF     7f9de000-7fa20000       Deferred        advapi32<elf>
  \-PE  7f9f0000-7fa20000       \               advapi32
ELF     7fc93000-7fca0000       Deferred        libxext.so.6
ELF     7fca2000-7fcac000       Deferred        libgcc_s.so.1
ELF     7fcdf000-7fde0000       Stabs           kernel32<elf>
  \-PE  7fd00000-7fde0000       \               kernel32
ELF     7fef0000-7fef4000       Deferred        libxfixes.so.3
ELF     7fef4000-7fef7000       Deferred        libxau.so.6
ELF     7fef7000-7feff000       Deferred        libsm.so.6
ELF     7feff000-7ff09000       Deferred        libnss_files.so.2
ELF     7ff09000-7ff12000       Deferred        libnss_nis.so.2
ELF     7ff12000-7ff27000       Deferred        libnsl.so.1
ELF     7ff27000-7ff30000       Deferred        libnss_compat.so.2
ELF     7ff32000-7ff3a000       Deferred        libxrender.so.1
ELF     7ff3e000-7ff40000       Deferred        libnvidia-tls.so.1
ELF     7ff40000-7ff62000       Deferred        libm.so.6
ELF     7ff62000-7ffe0000       Dwarf           ntdll<elf>
  \-PE  7ff70000-7ffe0000       \               ntdll
ELF     b7d6f000-b7d72000       Deferred        libdl.so.2
ELF     b7d72000-b7ea1000       Deferred        libc.so.6
ELF     b7ea1000-b7eb3000       Deferred        libpthread.so.0
ELF     b7ebf000-b7fcf000       Stabs           libwine.so.1
ELF     b7fd2000-b7fe8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Program Files\Lionhead Studios\Black & White 2\white.exe
        00000009    0 <==
[email]h4x0r@Mainframe:~/.wine[/email]/drive_c/Program Files/Lionhead Studios/Black & White 2$






now if anyone could even begin to figure out what wine is telling me, id apprectiate it
im running wine in windows xp mode, as it is required for the game
tried cedega, hate transgaimg (no better than windows)

---

### Post by DSn0wMan on 2006-09-28
Look at this line:

unimplemented function kernel32.dll.HeapSetInformation

Basically something is wrong with kernel32.dll

It's missing the HeatSetInformation function.

Kernel32.dll is the 32-bit dynamic link library found in the Windows operating system kernel. It handles memory management, input/output operations, and interrupts. When Windows boots up, kernel32.dll is loaded into a protected memory space so other applications do not take that space over.

I'd try taking it off a windows box (updated preferrebly) and sticking it into the system32 folder under wine.

---

