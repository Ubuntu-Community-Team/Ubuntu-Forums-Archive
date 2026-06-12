---
title: "Gears of war"
date: 2007-11-14
forum: Gaming &amp; Leisure
---

### Post by desertboy on 2007-11-14
Installs alright but crashes out with

> fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:powrprof:DllMain (0x7d8b0000, 1, (nil)) not fully implemented
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:msxml:domdoc_setProperty Unknown property L"SelectionNamespaces"
ERROR: Reference to undefined property "VideoDeviceVendorId"
fixme:process:IsWow64Process (0xffffffff 0x34b408) stub!
ERROR: Reference to undefined property "IsSLIEnabled"
ERROR: Reference to undefined property "IsCrossfireEnabled"
ERROR: Reference to undefined property "VideoDeviceVideoMemory"
ERROR: Reference to undefined property "CpuManuf"
wine: Unhandled page fault on read access to 0x66315f43 at address 0x100028c2 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x66315f43 in 32-bit code (0x100028c2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:100028c2 ESP:0034b3d4 EBP:0034fa20 EFLAGS:00210206(   - 00      - RIP1)
 EAX:66315f43 EBX:1000ddd0 ECX:00000000 EDX:66315f43
 ESI:006bd2a0 EDI:66315f43
Stack dump:
0x0034b3d4:  006bd300 00000000 10001710 66315f43
0x0034b3e4:  1000ddd0 00400000 00000002 00000000
0x0034b3f4:  52432e30 00005f54 00000000 00000000
0x0034b404:  00383165 00000000 352e302e 37323730
0x0034b414:  3336332e 772d785f 00000000 38346131
0x0034b424:  6d2e6466 66696e61 00747365 00000000
Backtrace:
=>1 0x100028c2 in startup (+0x28c2) (0x0034fa20)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 00475314 in module L"startup"
  2 0x0040d742 in startup (+0xd742) (0x00110436)
  3 0x53550000 (0x01180000)
  4 0x00000000 (0x00000000)
0x100028c2: movzwl      0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  484000       Export          startup
PE        6b0000-  70c000       Deferred        pccompat
PE      10000000-1002c000       Export          startup
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d280000-7d2b4000       Deferred        libxslt.so.1
ELF     7d2b4000-7d3d2000       Deferred        libxml2.so.2
ELF     7d3e7000-7d414000       Deferred        msxml3<elf>
  \-PE  7d3f0000-7d414000       \               msxml3
ELF     7d414000-7d4f4000       Deferred        wined3d<elf>
  \-PE  7d430000-7d4f4000       \               wined3d
ELF     7d4f4000-7d523000       Deferred        d3d9<elf>
  \-PE  7d500000-7d523000       \               d3d9
ELF     7d523000-7d537000       Deferred        lz32<elf>
  \-PE  7d530000-7d537000       \               lz32
ELF     7d537000-7d551000       Deferred        version<elf>
  \-PE  7d540000-7d551000       \               version
ELF     7d551000-7d57e000       Deferred        ws2_32<elf>
  \-PE  7d560000-7d57e000       \               ws2_32
ELF     7d89f000-7d8b4000       Deferred        powrprof<elf>
  \-PE  7d8b0000-7d8b4000       \               powrprof
ELF     7d8b4000-7d8e6000       Deferred        uxtheme<elf>
  \-PE  7d8c0000-7d8e6000       \               uxtheme
ELF     7d8e6000-7d8ef000       Deferred        libxcursor.so.1
ELF     7d8ef000-7d90c000       Deferred        imm32<elf>
  \-PE  7d900000-7d90c000       \               imm32
ELF     7d90c000-7d912000       Deferred        libxrandr.so.2
ELF     7d912000-7d91a000       Deferred        libxrender.so.1
ELF     7d9ca000-7d9cc000       Deferred        libnvidia-tls.so.1
ELF     7d9cc000-7e364000       Deferred        libglcore.so.1
ELF     7e364000-7e3fa000       Deferred        libgl.so.1
ELF     7e3fa000-7e3ff000       Deferred        libxdmcp.so.6
ELF     7e3ff000-7e402000       Deferred        libxau.so.6
ELF     7e402000-7e4f3000       Deferred        libx11.so.6
ELF     7e4f3000-7e501000       Deferred        libxext.so.6
ELF     7e501000-7e506000       Deferred        libxxf86vm.so.1
ELF     7e506000-7e51e000       Deferred        libice.so.6
ELF     7e51e000-7e526000       Deferred        libsm.so.6
ELF     7e526000-7e52b000       Deferred        libxfixes.so.3
ELF     7e53b000-7e5c6000       Deferred        winex11<elf>
  \-PE  7e550000-7e5c6000       \               winex11
ELF     7e659000-7e679000       Deferred        libexpat.so.1
ELF     7e679000-7e6a4000       Deferred        libfontconfig.so.1
ELF     7e6a4000-7e6b9000       Deferred        libz.so.1
ELF     7e6b9000-7e729000       Deferred        libfreetype.so.6
ELF     7e729000-7e749000       Deferred        mpr<elf>
  \-PE  7e730000-7e749000       \               mpr
ELF     7e749000-7e793000       Deferred        wininet<elf>
  \-PE  7e750000-7e793000       \               wininet
ELF     7e793000-7e7ce000       Deferred        urlmon<elf>
  \-PE  7e7a0000-7e7ce000       \               urlmon
ELF     7e7ce000-7e86c000       Deferred        oleaut32<elf>
  \-PE  7e7e0000-7e86c000       \               oleaut32
ELF     7e86c000-7e87f000       Deferred        libresolv.so.2
ELF     7e894000-7e8b2000       Deferred        iphlpapi<elf>
  \-PE  7e8a0000-7e8b2000       \               iphlpapi
ELF     7e8b2000-7e90b000       Deferred        rpcrt4<elf>
  \-PE  7e8c0000-7e90b000       \               rpcrt4
ELF     7e90b000-7e9ac000       Deferred        ole32<elf>
  \-PE  7e920000-7e9ac000       \               ole32
ELF     7e9ac000-7ea6a000       Deferred        comctl32<elf>
  \-PE  7e9c0000-7ea6a000       \               comctl32
ELF     7ea6a000-7eac3000       Deferred        shlwapi<elf>
  \-PE  7ea80000-7eac3000       \               shlwapi
ELF     7eac3000-7ebc6000       Deferred        shell32<elf>
  \-PE  7ead0000-7ebc6000       \               shell32
ELF     7ebc6000-7ec0f000       Deferred        advapi32<elf>
  \-PE  7ebd0000-7ec0f000       \               advapi32
ELF     7ec0f000-7ecaa000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecaa000       \               gdi32
ELF     7ecaa000-7ede8000       Deferred        user32<elf>
  \-PE  7ecd0000-7ede8000       \               user32
ELF     7ede8000-7ee49000       Deferred        crypt32<elf>
  \-PE  7edf0000-7ee49000       \               crypt32
ELF     7ee68000-7ee8f000       Deferred        wintrust<elf>
  \-PE  7ee70000-7ee8f000       \               wintrust
ELF     7efae000-7efc6000       Deferred        libnsl.so.1
ELF     7efc6000-7efeb000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c62000-b7c6b000       Deferred        libnss_compat.so.2
ELF     b7c6c000-b7c70000       Deferred        libdl.so.2
ELF     b7c70000-b7dba000       Deferred        libc.so.6
ELF     b7dbb000-b7dd3000       Deferred        libpthread.so.0
ELF     b7de8000-b7efc000       Deferred        libwine.so.1
ELF     b7efe000-b7f1a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Microsoft Games\Gears of War\Binaries\Startup.exe
        00000009    0 <==


---

### Post by Ferrat on 2007-11-14
not a big chances you will get this to run but hope you do :)

Have you enabled GLSL?

---

