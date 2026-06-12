---
title: "Wine Kernal"
date: 2007-01-02
forum: Gaming &amp; Leisure
---

### Post by Torn on 2007-01-02
At 1st it was just a missing opengl32.dll i replaced

then this

torn@torn-desktop:~$ cd /windows/world\ of\ warcraft/
torn@torn-desktop:/windows/world of warcraft$ wine wow.exe -opengl
wine: Call from 0x5ed09ec5 to unimplemented function KERNEL32.dll.IsWow64Process, aborting
wine: Unimplemented function KERNEL32.dll.IsWow64Process called at address 0x5ed09ec5 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function KERNEL32.dll.IsWow64Process called in 32-bit code (0x7ffbd9c7).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ffbd9c7 ESP:7fbbfb70 EBP:7fbbfbc8 EFLAGS:00200212(   - 00      - -IA1)
 EAX:5eda22da EBX:7fff51b0 ECX:7fd10020 EDX:00000000
 ESI:7fbbfb70 EDI:00000001
Stack dump:
0x7fbbfb70:  80000100 00000001 00000000 5ed09ec5
0x7fbbfb80:  00000002 5eda2576 5eda22da 7fe6c000
0x7fbbfb90:  7fbbfbb0 7ffaf51a 7fd10000 7f928a75
0x7fbbfba0:  00000020 7fff51b0 7fc8f20f 00000001
0x7fbbfbb0:  7fbbfbc4 7ffaf5cb 5edac720 00000000
0x7fbbfbc0:  00000002 7fc8f20f 7fbbfd20 5ed09ec5
0200: sel=1007 base=7fe6c000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ffbd9c7 stub_entry_point+0x4c(dll=0x5eda2576, name=0x5eda22da) [/home/torn/Desktop/wine/dlls/ntdll/loader.c:181] in ntdll (0x7ffbd9c7)
fixme:dbghelp:sffip_cb NIY on 'opengl32.pdb'
  2 0x5ed09ec5 in opengl32 (+0x9ec5) (0x5ed09ec5)
  3 0x5ed0a366 EntryPoint+0x44 in opengl32 (0x5ed0a366)
  4 0x7ffbd975 call_dll_entry_point+0x15 in ntdll (0x7ffbd975)
  5 0x7ffbe737 MODULE_InitDLL+0x168 [/home/torn/Desktop/wine/dlls/ntdll/loader.c:816] in ntdll (0x7ffbe737)
  6 0x7ffbf08a process_attach+0x98 [/home/torn/Desktop/wine/dlls/ntdll/loader.c:891] in ntdll (0x7ffbf08a)
  7 0x7ffbf05e process_attach+0x6c [/home/torn/Desktop/wine/dlls/ntdll/loader.c:883] in ntdll (0x7ffbf05e)
  8 0x7ffc1a38 LdrInitializeThunk+0x394(main_file=0x1c, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/home/torn/Desktop/wine/dlls/ntdll/loader.c:2001] in ntdll (0x7ffc1a38)
  9 0x7fc7b3df start_process+0xb1(arg=0x0) [/home/torn/Desktop/wine/dlls/kernel/process.c:1015] in kernel32 (0x7fc7b3df)
  10 0xb7ed7b2b wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ed7b2b)
0x7ffbd9c7 stub_entry_point+0x4c [/home/torn/Desktop/wine/dlls/ntdll/loader.c:181] in ntdll: subl       $4,%esp
181         for (;;) RtlRaiseException( &rec );
Modules:
Module  Address                 Debug info      Name (73 modules)
PE      0x00400000-00d8d000     Deferred        wow
PE      0x10000000-10069000     Deferred        divxdecoder
PE      0x5ed00000-5edcc000     Export          opengl32
PE      0x68b20000-68b40000     Deferred        glu32
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7f160000-7f191000     Deferred        uxtheme<elf>
  \-PE  0x7f170000-7f191000     \               uxtheme
ELF     0x7f191000-7f209000     Deferred        winex11<elf>
  \-PE  0x7f1a0000-7f209000     \               winex11
ELF     0x7f209000-7f227000     Deferred        mpr<elf>
  \-PE  0x7f210000-7f227000     \               mpr
ELF     0x7f227000-7f26b000     Deferred        wininet<elf>
  \-PE  0x7f230000-7f26b000     \               wininet
ELF     0x7f26b000-7f290000     Deferred        msacm32<elf>
  \-PE  0x7f270000-7f290000     \               msacm32
PE      0x7f290000-7f320000     Deferred        fmod
ELF     0x7f321000-7f335000     Deferred        lz32<elf>
  \-PE  0x7f330000-7f335000     \               lz32
ELF     0x7f335000-7f34e000     Deferred        version<elf>
  \-PE  0x7f340000-7f34e000     \               version
ELF     0x7f34e000-7f3d2000     Deferred        winmm<elf>
  \-PE  0x7f360000-7f3d2000     \               winmm
ELF     0x7f3d2000-7f3ee000     Deferred        imm32<elf>
  \-PE  0x7f3e0000-7f3ee000     \               imm32
ELF     0x7f3ee000-7f4d4000     Deferred        libx11.so.6
ELF     0x7f4d4000-7f4ec000     Deferred        libice.so.6
ELF     0x7f4ec000-7f530000     Deferred        ddraw<elf>
  \-PE  0x7f500000-7f530000     \               ddraw
ELF     0x7f545000-7f549000     Deferred        libxfixes.so.3
ELF     0x7f549000-7f5a9000     Deferred        msvcrt<elf>
  \-PE  0x7f560000-7f5a9000     \               msvcrt
ELF     0x7f5a9000-7f5d3000     Deferred        ws2_32<elf>
  \-PE  0x7f5b0000-7f5d3000     \               ws2_32
ELF     0x7f5d3000-7f5ed000     Deferred        wsock32<elf>
  \-PE  0x7f5e0000-7f5ed000     \               wsock32
ELF     0x7f5ed000-7f60c000     Deferred        iphlpapi<elf>
  \-PE  0x7f5f0000-7f60c000     \               iphlpapi
ELF     0x7f60c000-7f655000     Deferred        rpcrt4<elf>
  \-PE  0x7f620000-7f655000     \               rpcrt4
ELF     0x7f655000-7f6e4000     Deferred        ole32<elf>
  \-PE  0x7f670000-7f6e4000     \               ole32
ELF     0x7f6e4000-7f73e000     Deferred        shlwapi<elf>
  \-PE  0x7f700000-7f73e000     \               shlwapi
ELF     0x7f73e000-7f807000     Deferred        shell32<elf>
  \-PE  0x7f750000-7f807000     \               shell32
ELF     0x7f807000-7f886000     Deferred        gdi32<elf>
  \-PE  0x7f820000-7f886000     \               gdi32
ELF     0x7f886000-7f9b1000     Deferred        user32<elf>
  \-PE  0x7f8a0000-7f9b1000     \               user32
ELF     0x7f9b1000-7fa71000     Deferred        comctl32<elf>
  \-PE  0x7f9c0000-7fa71000     \               comctl32
ELF     0x7fa71000-7fab0000     Deferred        advapi32<elf>
  \-PE  0x7fa80000-7fab0000     \               advapi32
ELF     0x7fbc3000-7fbd0000     Deferred        libxext.so.6
ELF     0x7fbd2000-7fbdb000     Deferred        libxcursor.so.1
ELF     0x7fc0e000-7fd10000     Stabs           kernel32<elf>
  \-PE  0x7fc30000-7fd10000     \               kernel32
ELF     0x7fe20000-7fe28000     Deferred        libxrender.so.1
ELF     0x7fe28000-7fe30000     Deferred        libsm.so.6
ELF     0x7fe30000-7fe3a000     Deferred        libnss_files.so.2
ELF     0x7fe3a000-7fe43000     Deferred        libnss_nis.so.2
ELF     0x7fe43000-7fe58000     Deferred        libnsl.so.1
ELF     0x7fe58000-7fe61000     Deferred        libnss_compat.so.2
ELF     0x7fe70000-7fe92000     Deferred        libm.so.6
ELF     0x7fe92000-7ff88000     Deferred        libwine_unicode.so.1
ELF     0x7ff88000-80000000     Stabs           ntdll<elf>
  \-PE  0x7ffa0000-80000000     \               ntdll
ELF     0xb7d8f000-b7d92000     Deferred        libdl.so.2
ELF     0xb7d92000-b7ec1000     Deferred        libc.so.6
ELF     0xb7ec1000-b7ed3000     Deferred        libpthread.so.0
ELF     0xb7ed3000-b7eec000     DIA             libwine.so.1
ELF     0xb7eec000-b7eef000     Deferred        libxau.so.6
ELF     0xb7efa000-b7f10000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\windows\World of Warcraft\wow.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
torn@torn-desktop:/windows/world of warcraft$

may be in the wrong forums please move if needed
going to search around on google see if i can come up with anything

---

### Post by taurus on 2007-01-02
Move over to Gaming & Leisure.

---

