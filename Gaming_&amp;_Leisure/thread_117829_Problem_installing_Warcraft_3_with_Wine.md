---
title: "Problem installing Warcraft 3 with Wine"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by three_sixteen on 2006-01-15
When I try to install it using wine the install process works for about 15 seconds and then closes itself with this error:

```
austin@threesixteen:~$ sudo wine /media/cdrom0/install.exe
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
fixme:bitblt:X11DRV_BitBlt potential optimization - client-side DIB copy
wine: Unhandled page fault on read access to 0x0000000c at address 0x7edabc16 (thread 000c), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x7edabc16).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:114f GS:0033
 EIP:7edabc16 ESP:7d71e92c EBP:7d71e93c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:7beffc60 EBX:7edc1520 ECX:00000000 EDX:00000000
 ESI:7fd70ad8 EDI:00000000
Stack dump:
0x7d71e92c:  7edbbb90 7edc1520 7fd70ad8 00000003
0x7d71e93c:  7d71e95c 7edbbbb8 7ed90000 00000003
0x7d71e94c:  00000000 7bef41b0 7fd70ad8 7edbbb90
0x7d71e95c:  7d71e97c 7bebffe5 7ed90000 00000003
0x7d71e96c:  00000000 00000000 00000000 7bef41b0
0x7d71e97c:  7d71ea08 7bec0d9a 7edbbb90 7ed90000
0229: sel=114f base=7d73c000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7edabc16 DllMain+0x1d6 in msvcrt (0x7edabc16)
  2 0x7edbbbb8 in msvcrt (+0x2bbb8) (0x7edbbbb8)
  3 0x7bebffe5 call_dll_entry_point+0x15 in ntdll (0x7bebffe5)
  4 0x7bec0d9a in ntdll (+0x20d9a) (0x7bec0d9a)
  5 0x7bec14e9 LdrShutdownThread+0x99 in ntdll (0x7bec14e9)
  6 0x7bedcdc5 RtlExitUserThread+0x15 in ntdll (0x7bedcdc5)
  7 0x7fcf72e5 in kernel32 (+0x672e5) (0x7fcf72e5)
  8 0x7e0357d7 in wineoss (+0x57d7) (0x7e0357d7)
  9 0x7e035b1b in wineoss (+0x5b1b) (0x7e035b1b)
  10 0x7fcf7a47 in kernel32 (+0x67a47) (0x7fcf7a47)
  11 0x7bedd75f in ntdll (+0x3d75f) (0x7bedd75f)
  12 0xb7ef4361 start_thread+0x81 in libpthread.so.0 (0xb7ef4361)
  13 0xb7e89bde __clone+0x5e in libc.so.6 (0xb7e89bde)
0x7edabc16 DllMain+0x1d6 in msvcrt: movl        0xc(%edi),%esi
Modules:
Module  Address                 Debug info      Name (79 modules)
PE      0x00400000-00457000     Deferred        install
ELF     0x7be8c000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7de7b000-7deab000     Deferred        uxtheme<elf>
  \-PE  0x7de80000-7deab000     \               uxtheme
ELF     0x7deab000-7dec0000     Deferred        midimap<elf>
  \-PE  0x7deb0000-7dec0000     \               midimap
ELF     0x7dfde000-7e000000     Deferred        msacm32<elf>
  \-PE  0x7dff0000-7e000000     \               msacm32
ELF     0x7e000000-7e017000     Deferred        msacm<elf>
  \-PE  0x7e010000-7e017000     \               msacm
ELF     0x7e017000-7e059000     Export          wineoss<elf>
  \-PE  0x7e030000-7e059000     \               wineoss
ELF     0x7e09d000-7e0a6000     Deferred        libxcursor.so.1
ELF     0x7e0a6000-7e0c1000     Deferred        imm32<elf>
  \-PE  0x7e0b0000-7e0c1000     \               imm32
ELF     0x7e0c1000-7e0dd000     Deferred        ximcp.so.2
ELF     0x7e0dd000-7e0e5000     Deferred        libxrender.so.1
ELF     0x7e0f2000-7e0f4000     Deferred        libnvidia-tls.so.1
ELF     0x7e0f4000-7e85d000     Deferred        libglcore.so.1
ELF     0x7e85d000-7e8dc000     Deferred        libgl.so.1
ELF     0x7e8dc000-7e8e0000     Deferred        libxdmcp.so.6
ELF     0x7e8e0000-7e9a0000     Deferred        libx11.so.6
ELF     0x7e9a0000-7e9ad000     Deferred        libxext.so.6
ELF     0x7e9ad000-7e9c6000     Deferred        libice.so.6
ELF     0x7e9c6000-7ea43000     Deferred        winex11<elf>
  \-PE  0x7e9e0000-7ea43000     \               winex11
ELF     0x7ea43000-7ea62000     Deferred        libexpat.so.1
ELF     0x7ea62000-7ea90000     Deferred        libfontconfig.so.1
ELF     0x7ea90000-7eaa4000     Deferred        libz.so.1
ELF     0x7eaa4000-7eb0e000     Deferred        libfreetype.so.6
ELF     0x7eb0e000-7ebbd000     Deferred        comctl32<elf>
  \-PE  0x7eb20000-7ebbd000     \               comctl32
ELF     0x7ebbd000-7ec12000     Deferred        shlwapi<elf>
  \-PE  0x7ebd0000-7ec12000     \               shlwapi
ELF     0x7ec12000-7ecd0000     Deferred        shell32<elf>
  \-PE  0x7ec30000-7ecd0000     \               shell32
ELF     0x7ecd0000-7ece4000     Deferred        lz32<elf>
  \-PE  0x7ece0000-7ece4000     \               lz32
ELF     0x7ece4000-7ecfc000     Deferred        version<elf>
  \-PE  0x7ecf0000-7ecfc000     \               version
ELF     0x7ecfc000-7ed7d000     Deferred        winmm<elf>
  \-PE  0x7ed10000-7ed7d000     \               winmm
ELF     0x7ed7d000-7eddd000     Export          msvcrt<elf>
  \-PE  0x7ed90000-7eddd000     \               msvcrt
ELF     0x7eddd000-7edfb000     Deferred        iphlpapi<elf>
  \-PE  0x7ede0000-7edfb000     \               iphlpapi
ELF     0x7edfb000-7ee3f000     Deferred        rpcrt4<elf>
  \-PE  0x7ee10000-7ee3f000     \               rpcrt4
ELF     0x7ef25000-7f825000     Deferred        gdi32<elf>
  \-PE  0x7ef70000-7f825000     \               gdi32
ELF     0x7f825000-7f93e000     Deferred        user32<elf>
  \-PE  0x7f840000-7f93e000     \               user32
ELF     0x7f93e000-7f97a000     Deferred        advapi32<elf>
  \-PE  0x7f950000-7f97a000     \               advapi32
ELF     0x7f97a000-7fa00000     Deferred        ole32<elf>
  \-PE  0x7f990000-7fa00000     \               ole32
ELF     0x7fb11000-7fb14000     Deferred        libxau.so.6
ELF     0x7fb14000-7fb19000     Deferred        libxxf86vm.so.1
ELF     0x7fb19000-7fb20000     Deferred        libsm.so.6
ELF     0x7fb21000-7fb2c000     Deferred        libgcc_s.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe81000-7fe86000     Deferred        libxxf86dga.so.1
ELF     0x7fe86000-7fe90000     Deferred        libnss_files.so.2
ELF     0x7fe90000-7fe99000     Deferred        libnss_nis.so.2
ELF     0x7fe99000-7feae000     Deferred        libnsl.so.1
ELF     0x7feae000-7feb7000     Deferred        libnss_compat.so.2
ELF     0x7feb9000-7febd000     Deferred        libxfixes.so.3
ELF     0x7febd000-7febf000     Deferred        xlcutf8load.so.2
ELF     0x7febf000-7fec2000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dbe000-b7dc1000     Deferred        libdl.so.2
ELF     0xb7dc1000-b7eef000     Export          libc.so.6
ELF     0xb7eef000-b7f01000     Export          libpthread.so.0
ELF     0xb7f01000-b7f1b000     Deferred        libwine.so.1
ELF     0xb7f2b000-b7f41000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\install.exe
        0000000c   15 <==
        0000000b   15
        0000000a    1
        00000009    0
WineDbg terminated on pid 0x8

```

Whats going on? :(

---

