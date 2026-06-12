---
title: "GTA-Vice City under wine?"
date: 2006-03-16
forum: Gaming &amp; Leisure
---

### Post by wr0x2 on 2006-03-16
First, I am running breezy with a standard kernel and the latest wine install from the wine.sourceforge.net repository. Also, GTA:VC used to work under an older version of wine, although I don't know which one. When I try to start the vc executable (has cd crack so I can play) I get the error

```

unhandled exception c0000005 at address 00652f30

```
 in the terminal:
```

wr0x2@USSENTERPRISE:~/.wine/drive_c/VICE CITY$ wine gta-vc.exe
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
wine: Unhandled page fault on read access to 0x0000000d at address 0x652f30 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x0000000d in 32-bit code (0x00652f30).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00652f30 ESP:7fa4fbac EBP:00000001 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:00000000 ECX:ffffffff EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x00652f30 in gta-vc (+0x252f30) (0x00652f30)
  2 0x00000000 (0x00000000)
0x00652f30: cmpb        $0x0,0xd(%ebx)
Modules:
Module  Address                 Debug info      Name (81 modules)
PE      0x00400000-00a14000     Export          gta-vc
PE      0x21100000-2115c000     Deferred        mss32
ELF     0x73960000-73968000     Deferred        libxrender.so.1
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d17b000-7d190000     Deferred        midimap<elf>
  \-PE  0x7d180000-7d190000     \               midimap
ELF     0x7d2a8000-7d2cc000     Deferred        msacm32<elf>
  \-PE  0x7d2b0000-7d2cc000     \               msacm32
ELF     0x7d2cc000-7d2e3000     Deferred        msacm<elf>
  \-PE  0x7d2d0000-7d2e3000     \               msacm
ELF     0x7de73000-7deb6000     Deferred        wineoss<elf>
  \-PE  0x7de80000-7deb6000     \               wineoss
ELF     0x7ded7000-7dee0000     Deferred        libxcursor.so.1
ELF     0x7def0000-7df0c000     Deferred        imm32<elf>
  \-PE  0x7df00000-7df0c000     \               imm32
ELF     0x7df0c000-7df28000     Deferred        ximcp.so.2
ELF     0x7df28000-7df30000     Deferred        librt.so.1
ELF     0x7dfea000-7e72d000     Deferred        fglrx_dri.so
ELF     0x7e72d000-7e7ac000     Deferred        winex11<elf>
  \-PE  0x7e740000-7e7ac000     \               winex11
ELF     0x7e7ac000-7e7cb000     Deferred        libexpat.so.1
ELF     0x7e7cb000-7e7f9000     Deferred        libfontconfig.so.1
ELF     0x7e7f9000-7e80d000     Deferred        libz.so.1
ELF     0x7e80d000-7e877000     Deferred        libfreetype.so.6
ELF     0x7e877000-7e8fe000     Deferred        wined3d<elf>
  \-PE  0x7e890000-7e8fe000     \               wined3d
ELF     0x7e8fe000-7e974000     Deferred        libglu.so.1
ELF     0x7e974000-7ea13000     Deferred        libgl.so.1
ELF     0x7ea13000-7ea85000     Deferred        d3d8<elf>
  \-PE  0x7ea30000-7ea85000     \               d3d8
ELF     0x7ea85000-7eaae000     Deferred        ws2_32<elf>
  \-PE  0x7ea90000-7eaae000     \               ws2_32
ELF     0x7eaae000-7eac7000     Deferred        wsock32<elf>
  \-PE  0x7eab0000-7eac7000     \               wsock32
ELF     0x7eac7000-7eb49000     Deferred        winmm<elf>
  \-PE  0x7ead0000-7eb49000     \               winmm
ELF     0x7eb49000-7eb89000     Deferred        dinput<elf>
  \-PE  0x7eb60000-7eb89000     \               dinput
ELF     0x7eb89000-7eb9d000     Deferred        dinput8<elf>
  \-PE  0x7eb90000-7eb9d000     \               dinput8
ELF     0x7eb9d000-7ebbb000     Deferred        iphlpapi<elf>
  \-PE  0x7eba0000-7ebbb000     \               iphlpapi
ELF     0x7ebbb000-7ec03000     Deferred        rpcrt4<elf>
  \-PE  0x7ebd0000-7ec03000     \               rpcrt4
ELF     0x7ec03000-7ec0e000     Deferred        libgcc_s.so.1
ELF     0x7ecf4000-7f5f7000     Deferred        gdi32<elf>
  \-PE  0x7ed40000-7f5f7000     \               gdi32
ELF     0x7f5f7000-7f719000     Deferred        user32<elf>
  \-PE  0x7f610000-7f719000     \               user32
ELF     0x7f719000-7f7a3000     Deferred        ole32<elf>
  \-PE  0x7f730000-7f7a3000     \               ole32
ELF     0x7f7a3000-7f863000     Deferred        libx11.so.6
ELF     0x7f863000-7f870000     Deferred        libxext.so.6
ELF     0x7f870000-7f889000     Deferred        libice.so.6
ELF     0x7f889000-7f903000     Deferred        ddraw<elf>
  \-PE  0x7f8b0000-7f903000     \               ddraw
ELF     0x7f903000-7f940000     Deferred        advapi32<elf>
  \-PE  0x7f910000-7f940000     \               advapi32
ELF     0x7fa57000-7fa5b000     Deferred        libxdmcp.so.6
ELF     0x7fa5b000-7fa60000     Deferred        libxxf86vm.so.1
ELF     0x7fa64000-7fa69000     Deferred        libxxf86dga.so.1
ELF     0x7fa69000-7fa70000     Deferred        libsm.so.6
ELF     0x7fc70000-7fd70000     Deferred        kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe83000-7fe8d000     Deferred        libnss_files.so.2
ELF     0x7fe8d000-7fe96000     Deferred        libnss_nis.so.2
ELF     0x7fe96000-7feab000     Deferred        libnsl.so.1
ELF     0x7feab000-7feb4000     Deferred        libnss_compat.so.2
ELF     0x7febb000-7febf000     Deferred        libxfixes.so.3
ELF     0x7febf000-7fec1000     Deferred        xlcutf8load.so.2
ELF     0x7fec1000-7fec4000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7db0000-b7db3000     Deferred        libxau.so.6
ELF     0xb7dbd000-b7dc0000     Deferred        libdl.so.2
ELF     0xb7dc0000-b7eee000     Deferred        libc.so.6
ELF     0xb7eee000-b7f00000     Deferred        libpthread.so.0
ELF     0xb7f00000-b7f1a000     Deferred        libwine.so.1
ELF     0xb7f2d000-b7f43000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\VICE CITY\gta-vc.exe
        0000000a   -1
        00000009    0 <==
WineDbg terminated on pid 0x8

```

GTAVC was fairly playable before but now it doesnt work at all.

---

### Post by cogadh on 2007-06-18
You do realize you are responding to a post that is over a year old, don't you? I don't think he is still waiting patiently for an answer after all this time.

---

