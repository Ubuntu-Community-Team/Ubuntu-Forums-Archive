---
title: "old 95/98 app using wine"
date: 2006-05-02
forum: Gaming &amp; Leisure
---

### Post by simon_is_learning on 2006-05-02
well you see, it's kinnda embarasing but I would really like to be able to run one of my old win98 apps on my ubuntu machine

the app in question is backpacker 2 - just a plain simple question game

the game is on a CD

I have installed wine using this guide:
[http://www.ubuntuforums.org/showthread.php?t=56892](http://www.ubuntuforums.org/showthread.php?t=56892)

also I have installed the winetools package

I mount the CD (but the result is the same if I copy the files over to the HDD)

The error message I recive when running 
sudo wine install.exe is:


> err:dc:CreateDCW no driver found for L"DIRDIB"
wine: Unhandled page fault on read access to 0xffffffff at address 0x13c7:0x00001006 (thread 000a), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0xffffffff in 16-bit code (13c7:1006).
In 16 bit mode.
Register dump:
 CS:13c7 SS:187f DS:187f ES:0000 FS:11df GS:0033
 IP:1006 SP:89a4 BP:89bc FLAGS:0246(   - 00      -RIZP1)
 AX:002c BX:0058 CX:0000 DX:0000 SI:0000 DI:89d0
Stack dump:
0x187f:0x89a4:  0000 617a 89c0 0a4f 1557 89d0 187f 0002
0x187f:0x89b4:  0056 0000 617a 89d0 8ae2 287d 154f 8ae0
0x187f:0x89c4:  187f 89d0 187f 0000 0000 0000 2c02 002a
030f: sel=187f base=7fdecd50 limit=00008d1f 16-bit rw-
023b: sel=11df base=7e818000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x13c7:0x1006 (0x13c7:0x1006)
  2 0x154f:0x287d (0x154f:0x287d)
  3 0x154f:0x28a7 (0x154f:0x28a7)
  4 0x1547:0x2688 (0x1547:0x2688)
  5 0x136f:0x07a0 (0x136f:0x07a0)
  6 0x136f:0x0939 (0x136f:0x0939)
  7 0x136f:0x0cdf (0x136f:0x0cdf)
  8 0x136f:0x13c4 (0x136f:0x13c4)
  9 0x136f:0x0ffd (0x136f:0x0ffd)
  10 0x136f:0x0fe7 (0x136f:0x0fe7)
  11 0x1277:0x7319 (0x1277:0x7319)
  12 0x1277:0x00c8 (0x1277:0x00c8)
0x13c7:0x1006: lesw     %es:0x0(%si),%si
Modules:
Module  Address                 Debug info      Name (89 modules)
ELF     0x7be86000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7dd7e000-7dd92000     Deferred        lz32<elf>
  \-PE  0x7dd80000-7dd92000     \               lz32
ELF     0x7dd92000-7ddab000     Deferred        version<elf>
  \-PE  0x7dda0000-7ddab000     \               version
ELF     0x7ddab000-7ddd0000     Deferred        msvfw32<elf>
  \-PE  0x7ddb0000-7ddd0000     \               msvfw32
ELF     0x7e095000-7e0e1000     Deferred        libgcrypt.so.11
ELF     0x7e0e1000-7e0f1000     Deferred        libtasn1.so.2
ELF     0x7e0f1000-7e153000     Deferred        libgnutls.so.11
ELF     0x7e153000-7e170000     Deferred        libcups.so.2
ELF     0x7e259000-7e28a000     Deferred        uxtheme<elf>
  \-PE  0x7e260000-7e28a000     \               uxtheme
ELF     0x7e28a000-7e2b5000     Deferred        winspool<elf>
  \-PE  0x7e290000-7e2b5000     \               winspool
ELF     0x7e2b5000-7e36a000     Deferred        comctl32<elf>
  \-PE  0x7e2c0000-7e36a000     \               comctl32
ELF     0x7e36a000-7e388000     Deferred        iphlpapi<elf>
  \-PE  0x7e370000-7e388000     \               iphlpapi
ELF     0x7e388000-7e3d1000     Deferred        rpcrt4<elf>
  \-PE  0x7e3a0000-7e3d1000     \               rpcrt4
ELF     0x7e3d1000-7e45d000     Deferred        ole32<elf>
  \-PE  0x7e3f0000-7e45d000     \               ole32
ELF     0x7e45d000-7e4b6000     Deferred        shlwapi<elf>
  \-PE  0x7e470000-7e4b6000     \               shlwapi
ELF     0x7e4b6000-7e582000     Deferred        shell32<elf>
  \-PE  0x7e4d0000-7e582000     \               shell32
ELF     0x7e582000-7e61f000     Deferred        comdlg32<elf>
  \-PE  0x7e590000-7e61f000     \               comdlg32
ELF     0x7e81b000-7e830000     Deferred        midimap<elf>
  \-PE  0x7e820000-7e830000     \               midimap
ELF     0x7e943000-7e947000     Deferred        libgpg-error.so.0
ELF     0x7e947000-7e96b000     Deferred        msacm32<elf>
  \-PE  0x7e950000-7e96b000     \               msacm32
ELF     0x7e96b000-7e982000     Deferred        msacm<elf>
  \-PE  0x7e970000-7e982000     \               msacm
ELF     0x7e982000-7e9c6000     Deferred        wineoss<elf>
  \-PE  0x7e990000-7e9c6000     \               wineoss
ELF     0x7e9c6000-7ea4c000     Deferred        winmm<elf>
  \-PE  0x7e9d0000-7ea4c000     \               winmm
ELF     0x7ea4c000-7eaab000     Deferred        winedos<elf>
  \-PE  0x7ea60000-7eaab000     \               winedos
ELF     0x7eafc000-7eb00000     Deferred        libxfixes.so.3
ELF     0x7eb00000-7eb09000     Deferred        libxcursor.so.1
ELF     0x7eb09000-7eb11000     Deferred        libxrender.so.1
ELF     0x7eb11000-7eb2d000     Deferred        imm32<elf>
  \-PE  0x7eb20000-7eb2d000     \               imm32
ELF     0x7eb2d000-7eb49000     Deferred        ximcp.so.2
ELF     0x7eb49000-7eb50000     Deferred        libdrm.so.1
ELF     0x7eb50000-7ebb6000     Deferred        libgl.so.1
ELF     0x7ebb6000-7ec76000     Deferred        libx11.so.6
ELF     0x7ec76000-7ec83000     Deferred        libxext.so.6
ELF     0x7ec83000-7ec9c000     Deferred        libice.so.6
ELF     0x7ec9c000-7ed1b000     Deferred        winex11<elf>
  \-PE  0x7ecb0000-7ed1b000     \               winex11
ELF     0x7ed1b000-7ed3a000     Deferred        libexpat.so.1
ELF     0x7ed3a000-7ed68000     Deferred        libfontconfig.so.1
ELF     0x7ed68000-7ed7c000     Deferred        libz.so.1
ELF     0x7ed7c000-7ede6000     Deferred        libfreetype.so.6
ELF     0x7ede6000-7ee24000     Deferred        advapi32<elf>
  \-PE  0x7edf0000-7ee24000     \               advapi32
ELF     0x7ef0a000-7f80e000     Deferred        gdi32<elf>
  \-PE  0x7ef50000-7f80e000     \               gdi32
ELF     0x7f80e000-7f930000     Deferred        user32<elf>
  \-PE  0x7f830000-7f930000     \               user32
ELF     0x7fa42000-7fa46000     Deferred        libxdmcp.so.6
ELF     0x7fa46000-7fa4b000     Deferred        libxxf86vm.so.1
ELF     0x7fa4b000-7fa60000     Deferred        winevdm<elf>
  \-PE  0x7fa50000-7fa60000     \               winevdm
ELF     0x7fa61000-7fa66000     Deferred        libxxf86dga.so.1
ELF     0x7fa66000-7fa71000     Deferred        libgcc_s.so.1
ELF     0x7fc71000-7fd70000     Deferred        kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe83000-7fe8e000     Deferred        libnss_files.so.2
ELF     0x7fe8e000-7fe98000     Deferred        libnss_nis.so.2
ELF     0x7fe98000-7feae000     Deferred        libnsl.so.1
ELF     0x7feae000-7feb8000     Deferred        libnss_compat.so.2
ELF     0x7febb000-7fec2000     Deferred        libsm.so.6
ELF     0x7fec6000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7dd0000-b7dd3000     Deferred        libxau.so.6
ELF     0xb7dd5000-b7dd9000     Deferred        libdl.so.2
ELF     0xb7dd9000-b7f07000     Deferred        libc.so.6
ELF     0xb7f07000-b7f1a000     Deferred        libpthread.so.0
ELF     0xb7f1a000-b7f1c000     Deferred        xlcutf8load.so.2
ELF     0xb7f24000-b7f3e000     Deferred        libwine.so.1
ELF     0xb7f40000-b7f56000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b
        0000000c    0
00000008 (D) c:\windows\system32\winevdm.exe
        0000000a    0 <==
        00000009    0



the no driver found part, is interesting me - but I havn't been able to track any driver down yet could it be the fault?

or what do you think - is it even possible to run old apps from a CD?

ps. first day using wine

thanks in advance

---

