---
title: "Help needed with Wine and Sim Theme Park"
date: 2006-01-05
forum: Gaming &amp; Leisure
---

### Post by kennyhow on 2006-01-05
Sim Theme Park will be my second windows application installed.  Actually, it already is installed and without a glitch.  But now when I try to run it I get the following error.  I have changed winecfg to use win3.1 and winnt4.0 as well as win98 for this program.

```
kenny@ubuntu:~$ wine "C:\Program Files\SimTheme Park\TP.exe"
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvid.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004262a2).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:004262a2 ESP:7fb3daa4 EBP:7fb3daf0 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:c0317000 EBX:00000001 ECX:7fb3db18 EDX:7fb3dbe5
 ESI:00000000 EDI:00400000
Stack dump:
0x7fb3daa4:  00400000 7fd22517 7fb3daf0 7fb3dac4
0x7fb3dab4:  00000001 7fb3dbe5 7fb3db18 00001010
0x7fb3dac4:  00400000 7fd22517 00000001 00001010
0x7fb3dad4:  00000073 00015180 700007ff 7fb3c031
0x7fb3dae4:  00000000 f9cd3a22 00000002 7fb3dbb4
0x7fb3daf4:  0042641f 00001010 7fb3db18 00400000
0200: sel=1007 base=b7f48000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x004262a2 in tp (+0x262a2) (0x7fb3daf0)
  2 0x0042641f in tp (+0x2641f) (0x7fb3dbb4)
  3 0x00422d9c in tp (+0x22d9c) (0x7fb3dc64)
  4 0x00421e56 in tp (+0x21e56) (0x7fb3dc84)
  5 0x0042111e in tp (+0x2111e) (0x7fb3dcc8)
  6 0x00420bea in tp (+0x20bea) (0x7fb3fd24)
  7 0x0042087e in tp (+0x2087e) (0x7fb3fd7c)
  8 0x00422506 in tp (+0x22506) (0x7fb3fdb4)
  9 0x0040e279 in tp (+0xe279) (0x7fb3fe94)
  10 0x004169b2 EntryPoint+0x152 in tp (0x7fb3ff20)
  11 0x7fd18e63 in kernel32 (+0x48e63) (0x7fb3fff4)
  12 0xb7f28c45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x004262a2: movl        0x0(%esi),%edi
Modules:
Module  Address                 Debug info      Name (51 modules)
PE      0x00400000-00444000     Export          tp
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7ebc5000-7ebc9000     Deferred        libxfixes.so.3
ELF     0x7ebc9000-7ebd2000     Deferred        libxcursor.so.1
ELF     0x7ebd2000-7ebef000     Deferred        imm32<elf>
  \-PE  0x7ebe0000-7ebef000     \               imm32
ELF     0x7ebef000-7ec0b000     Deferred        ximcp.so.2
ELF     0x7ec0b000-7ec0e000     Deferred        libxrandr.so.2
ELF     0x7ec0e000-7ec16000     Deferred        libxrender.so.1
ELF     0x7ec16000-7ec1d000     Deferred        libdrm.so.1
ELF     0x7ec1d000-7ec22000     Deferred        libxxf86vm.so.1
ELF     0x7ec22000-7ec88000     Deferred        libgl.so.1
ELF     0x7ec88000-7ed48000     Deferred        libx11.so.6
ELF     0x7ed48000-7ed61000     Deferred        libice.so.6
ELF     0x7ed61000-7ede3000     Deferred        winex11.drv<elf>
  \-PE  0x7ed70000-7ede3000     \               winex11.drv
ELF     0x7ede3000-7ee02000     Deferred        libexpat.so.1
ELF     0x7ee02000-7ee30000     Deferred        libfontconfig.so.1
ELF     0x7ee30000-7ee3d000     Deferred        libxext.so.6
ELF     0x7ee3d000-7ee51000     Deferred        libz.so.1
ELF     0x7ee51000-7eebb000     Deferred        libfreetype.so.6
ELF     0x7eebb000-7eecf000     Deferred        lz32<elf>
  \-PE  0x7eec0000-7eecf000     \               lz32
ELF     0x7eecf000-7eeea000     Deferred        version<elf>
  \-PE  0x7eee0000-7eeea000     \               version
ELF     0x7eeea000-7ef2b000     Deferred        advapi32<elf>
  \-PE  0x7ef00000-7ef2b000     \               advapi32
ELF     0x7f011000-7f914000     Deferred        gdi32<elf>
  \-PE  0x7f060000-7f914000     \               gdi32
ELF     0x7f914000-7fa40000     Deferred        user32<elf>
  \-PE  0x7f940000-7fa40000     \               user32
ELF     0x7fb42000-7fb46000     Deferred        libxdmcp.so.6
ELF     0x7fb46000-7fb49000     Deferred        libxau.so.6
ELF     0x7fb49000-7fb50000     Deferred        libsm.so.6
ELF     0x7fb52000-7fb5d000     Deferred        libgcc_s.so.1
ELF     0x7fca5000-7fdb0000     Export          kernel32<elf>
  \-PE  0x7fcd0000-7fdb0000     \               kernel32
ELF     0x7fec1000-7fecb000     Deferred        libnss_files.so.2
ELF     0x7fecb000-7fed4000     Deferred        libnss_nis.so.2
ELF     0x7fed4000-7fee9000     Deferred        libnsl.so.1
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7ddd000-b7ddf000     Deferred        xlcutf8load.so.2
ELF     0xb7de1000-b7de4000     Deferred        libdl.so.2
ELF     0xb7de4000-b7f12000     Deferred        libc.so.6
ELF     0xb7f12000-b7f24000     Deferred        libpthread.so.0
ELF     0xb7f24000-b7f3d000     Export          libwine.so.1
ELF     0xb7f3f000-b7f48000     Deferred        libnss_compat.so.2
ELF     0xb7f4d000-b7f63000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\SimTheme Park\TP.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
```

---

