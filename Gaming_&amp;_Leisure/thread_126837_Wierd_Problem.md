---
title: "Wierd Problem"
date: 2006-02-07
forum: Gaming &amp; Leisure
---

### Post by Iron_Monkey on 2006-02-07
I have successfully installed Ragnarok using Wine. However, I get seem to get it started. I keep getting this wierd error whenever I try to run "wine ~/.wine/drive_c/ProgramFiles/Gravity/RO/Ragnarok.exe"


-=-=-=-=-=Error starts here=-=-=-=-=-=-=
wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bebbd99).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7bebbd99 ESP:7fb0e764 EBP:7fb0e7c8 EFLAGS:00200212(   - 00      - -IA1)
 EAX:0000194e EBX:7bef37f0 ECX:7fdcb340 EDX:7fd70024
 ESI:7fb0e770 EDI:00000001
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7bebbd99 call_dll_entry_point+0x79 in ntdll (0x7bebbd99)
  2 0x00402052 in ragnarok (+0x2052) (0x00402052)
  3 0x00000000 (0x00000000)
0x7bebbd99 call_dll_entry_point+0x79 in ntdll: addl     $12,%esp
Modules:
Module  Address                 Debug info      Name (70 modules)
PE      0x00400000-00424000     Export          ragnarok
PE      0x5f400000-5f4ed000     Deferred        mfc42
PE      0x780c0000-78121000     Deferred        msvcp60
ELF     0x7be87000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e7e2000-7e813000     Deferred        uxtheme<elf>
  \-PE  0x7e7f0000-7e813000     \               uxtheme
ELF     0x7e831000-7e83a000     Deferred        libxcursor.so.1
ELF     0x7e843000-7e85f000     Deferred        imm32<elf>
  \-PE  0x7e850000-7e85f000     \               imm32
ELF     0x7e85f000-7e87b000     Deferred        ximcp.so.2
ELF     0x7e87b000-7e883000     Deferred        libxrender.so.1
ELF     0x7e883000-7e88a000     Deferred        libdrm.so.1
ELF     0x7e88a000-7e8f0000     Deferred        libgl.so.1
ELF     0x7e8f0000-7e9b0000     Deferred        libx11.so.6
ELF     0x7e9b0000-7e9bd000     Deferred        libxext.so.6
ELF     0x7e9bd000-7e9d6000     Deferred        libice.so.6
ELF     0x7e9d6000-7ea55000     Deferred        winex11<elf>
  \-PE  0x7e9f0000-7ea55000     \               winex11
ELF     0x7ea55000-7ea74000     Deferred        libexpat.so.1
ELF     0x7ea74000-7eaa2000     Deferred        libfontconfig.so.1
ELF     0x7eaa2000-7eab6000     Deferred        libz.so.1
ELF     0x7eab6000-7eb20000     Deferred        libfreetype.so.6
ELF     0x7eb30000-7eb33000     Deferred        libxrandr.so.2
ELF     0x7eb33000-7eb37000     Deferred        libxdmcp.so.6
ELF     0x7eb37000-7eb99000     Deferred        msvcrt<elf>
  \-PE  0x7eb50000-7eb99000     \               msvcrt
ELF     0x7eb99000-7ec4d000     Deferred        comctl32<elf>
  \-PE  0x7eba0000-7ec4d000     \               comctl32
ELF     0x7ec4d000-7ed10000     Deferred        shell32<elf>
  \-PE  0x7ec60000-7ed10000     \               shell32
ELF     0x7ed10000-7ed2e000     Deferred        iphlpapi<elf>
  \-PE  0x7ed20000-7ed2e000     \               iphlpapi
ELF     0x7ed2e000-7ed76000     Deferred        rpcrt4<elf>
  \-PE  0x7ed40000-7ed76000     \               rpcrt4
ELF     0x7ed76000-7ee00000     Deferred        ole32<elf>
  \-PE  0x7ed90000-7ee00000     \               ole32
ELF     0x7ee00000-7ee57000     Deferred        shlwapi<elf>
  \-PE  0x7ee10000-7ee57000     \               shlwapi
ELF     0x7ee57000-7ee94000     Deferred        advapi32<elf>
  \-PE  0x7ee60000-7ee94000     \               advapi32
ELF     0x7ef7a000-7f87d000     Deferred        gdi32<elf>
  \-PE  0x7efc0000-7f87d000     \               gdi32
ELF     0x7f87d000-7f99f000     Deferred        user32<elf>
  \-PE  0x7f8a0000-7f99f000     \               user32
ELF     0x7f99f000-7f9bd000     Deferred        mpr<elf>
  \-PE  0x7f9b0000-7f9bd000     \               mpr
ELF     0x7f9bd000-7fa00000     Deferred        wininet<elf>
  \-PE  0x7f9d0000-7fa00000     \               wininet
ELF     0x7fb10000-7fb15000     Deferred        libxxf86vm.so.1
ELF     0x7fb15000-7fb20000     Deferred        libgcc_s.so.1
ELF     0x7fb23000-7fb28000     Deferred        libxxf86dga.so.1
ELF     0x7fc70000-7fd70000     Deferred        kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe83000     Deferred        libxau.so.6
ELF     0x7fe83000-7fe8a000     Deferred        libsm.so.6
ELF     0x7fe8a000-7fe94000     Deferred        libnss_files.so.2
ELF     0x7fe94000-7fe9d000     Deferred        libnss_nis.so.2
ELF     0x7fe9d000-7feb2000     Deferred        libnsl.so.1
ELF     0x7feb2000-7febb000     Deferred        libnss_compat.so.2
ELF     0x7febe000-7fec2000     Deferred        libxfixes.so.3
ELF     0x7fec2000-7fec4000     Deferred        xlcutf8load.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e6b000-b7e6e000     Deferred        libdl.so.2
ELF     0xb7e6e000-b7f9c000     Deferred        libc.so.6
ELF     0xb7f9c000-b7fae000     Deferred        libpthread.so.0
ELF     0xb7fae000-b7fc8000     Deferred        libwine.so.1
ELF     0xb7fd4000-b7fea000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program\Gravity\RO\Ragnarok.exe
        00000009    0 <==
WineDbg terminated on pid 0x8
=-=-=-=-=-=Error Ends Here=-=-=-=-=-=-=

Is there anyway so switch Ubuntu over to 16bit?

---

