---
title: "Picasa on Wine problem"
date: 2006-03-26
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-03-26
Im trying to run Picasa on Wine but keep getting this error:
```
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:CoInternetGetSession (0, 0x7fa6d4a4, 0): stub
fixme:urlmon:URLMON_DllGetClassObject {79eac9e2-baf9-11ce-8c82-00aa004ba90b}: no class found.
wine: Unhandled exception (thread 0032), starting debugger...
WineDbg starting on pid 0x31
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00609329).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:00609329 ESP:7fa6d494 EBP:7fa6fe94 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:797c25f4 ECX:797c3550 EDX:00000000
 ESI:007f547c EDI:797c25f0
Stack dump:
0x7fa6d494:  00000000 007f547c 00000000 797c3550
0x7fa6d4a4:  00000000 005dbef6 7beff980 00000000
0x7fa6d4b4:  00000000 7fda001c 005156de 7beff980
0x7fa6d4c4:  00000000 7fd38ff4 00000000 00000000
0x7fa6d4d4:  7fa6e5e0 7fa6e5dc 7fa6e5d8 7c0738f8
0x7fa6d4e4:  00000000 7c0781b7 7ca7f043 7fa6d5c8
0200: sel=1007 base=b7f73000 limit=00001f97 32-bit rw-
Backtrace:
=>1 0x00609329 in picasa2 (+0x209329) (0x7fa6fe94)
  2 0x00620942 EntryPoint+0xe0 in picasa2 (0x7fa6ff20)
  3 0x7fcf8e63 in kernel32 (+0x48e63) (0x7fa6fff4)
  4 0xb7f52c45 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x00609329: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (107 modules)
PE      0x00400000-0083e000     Export          picasa2
PE      0x10000000-10a43000     Deferred        picasai18n
PE      0x79480000-7957a000     Deferred        expwebsites.yti
ELF     0x798b1000-798b9000     Deferred        libxrender.so.1
ELF     0x7be87000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
PE      0x7c510000-7c547000     Deferred        ytitivo.yti
PE      0x7c550000-7c579000     Deferred        cdvdr.yti
ELF     0x7c764000-7c7c6000     Deferred        libgnutls.so.11
ELF     0x7c7c6000-7c7e3000     Deferred        libcups.so.2
ELF     0x7c7f4000-7c840000     Deferred        libgcrypt.so.11
ELF     0x7c840000-7c850000     Deferred        libtasn1.so.2
ELF     0x7c9ac000-7c9c1000     Deferred        midimap<elf>
  \-PE  0x7c9b0000-7c9c1000     \               midimap
ELF     0x7c9c1000-7c9da000     Deferred        msacm.drv<elf>
  \-PE  0x7c9d0000-7c9da000     \               msacm.drv
ELF     0x7c9da000-7ca1d000     Deferred        wineoss.drv<elf>
  \-PE  0x7c9f0000-7ca1d000     \               wineoss.drv
ELF     0x7ca61000-7ca6a000     Deferred        libxcursor.so.1
ELF     0x7ca78000-7ca94000     Deferred        ximcp.so.2
ELF     0x7e296000-7e499000     Deferred        i915_dri.so
ELF     0x7e499000-7e4a0000     Deferred        libdrm.so.1
ELF     0x7e4a0000-7e4a5000     Deferred        libxxf86vm.so.1
ELF     0x7e4a5000-7e50b000     Deferred        libgl.so.1
ELF     0x7e50b000-7e58d000     Deferred        winex11.drv<elf>
  \-PE  0x7e520000-7e58d000     \               winex11.drv
ELF     0x7e58d000-7e5ac000     Deferred        libexpat.so.1
ELF     0x7e5ac000-7e5da000     Deferred        libfontconfig.so.1
ELF     0x7e5da000-7e5ee000     Deferred        libz.so.1
ELF     0x7e5ee000-7e658000     Deferred        libfreetype.so.6
ELF     0x7e658000-7e671000     Deferred        wintrust<elf>
  \-PE  0x7e660000-7e671000     \               wintrust
ELF     0x7e671000-7e731000     Deferred        libx11.so.6
ELF     0x7e731000-7e74a000     Deferred        libice.so.6
ELF     0x7e74a000-7e7c2000     Deferred        ddraw<elf>
  \-PE  0x7e770000-7e7c2000     \               ddraw
ELF     0x7e7c2000-7e7df000     Deferred        imm32<elf>
  \-PE  0x7e7d0000-7e7df000     \               imm32
ELF     0x7e7df000-7e874000     Deferred        oleaut32<elf>
  \-PE  0x7e800000-7e874000     \               oleaut32
ELF     0x7e874000-7e89f000     Deferred        winspool.drv<elf>
  \-PE  0x7e880000-7e89f000     \               winspool.drv
ELF     0x7e89f000-7e92f000     Deferred        comdlg32<elf>
  \-PE  0x7e8b0000-7e92f000     \               comdlg32
ELF     0x7e92f000-7e958000     Deferred        cabinet<elf>
  \-PE  0x7e940000-7e958000     \               cabinet
ELF     0x7e958000-7e980000     Deferred        urlmon<elf>
  \-PE  0x7e970000-7e980000     \               urlmon
ELF     0x7e980000-7ea46000     Deferred        shell32<elf>
  \-PE  0x7e9a0000-7ea46000     \               shell32
ELF     0x7ea46000-7eaa2000     Deferred        shlwapi<elf>
  \-PE  0x7ea60000-7eaa2000     \               shlwapi
ELF     0x7eaa2000-7eac1000     Deferred        mpr<elf>
  \-PE  0x7eab0000-7eac1000     \               mpr
ELF     0x7eac1000-7eb05000     Deferred        wininet<elf>
  \-PE  0x7ead0000-7eb05000     \               wininet
ELF     0x7eb05000-7eb30000     Deferred        ws2_32<elf>
  \-PE  0x7eb10000-7eb30000     \               ws2_32
ELF     0x7eb30000-7eb51000     Deferred        iphlpapi<elf>
  \-PE  0x7eb40000-7eb51000     \               iphlpapi
ELF     0x7eb51000-7eb9b000     Deferred        rpcrt4<elf>
  \-PE  0x7eb70000-7eb9b000     \               rpcrt4
ELF     0x7eb9b000-7ec25000     Deferred        ole32<elf>
  \-PE  0x7ebb0000-7ec25000     \               ole32
ELF     0x7ec25000-7ece4000     Deferred        comctl32<elf>
  \-PE  0x7ec30000-7ece4000     \               comctl32
ELF     0x7ece4000-7ed09000     Deferred        msvfw32<elf>
  \-PE  0x7ecf0000-7ed09000     \               msvfw32
ELF     0x7ed09000-7ed4a000     Deferred        advapi32<elf>
  \-PE  0x7ed20000-7ed4a000     \               advapi32
ELF     0x7ee30000-7f733000     Deferred        gdi32<elf>
  \-PE  0x7ee80000-7f733000     \               gdi32
ELF     0x7f733000-7f85f000     Deferred        user32<elf>
  \-PE  0x7f750000-7f85f000     \               user32
ELF     0x7f85f000-7f8df000     Deferred        winmm<elf>
  \-PE  0x7f870000-7f8df000     \               winmm
ELF     0x7f8df000-7f902000     Deferred        msacm32<elf>
  \-PE  0x7f8f0000-7f902000     \               msacm32
ELF     0x7f902000-7f941000     Deferred        avifil32<elf>
  \-PE  0x7f910000-7f941000     \               avifil32
ELF     0x7f941000-7f955000     Deferred        lz32<elf>
  \-PE  0x7f950000-7f955000     \               lz32
ELF     0x7f955000-7f970000     Deferred        version<elf>
  \-PE  0x7f960000-7f970000     \               version
ELF     0x7fa73000-7fa80000     Deferred        libxext.so.6
ELF     0x7fa81000-7fa85000     Deferred        libxdmcp.so.6
ELF     0x7fc85000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fd95000-7fda0000     Deferred        libgcc_s.so.1
ELF     0x7feb3000-7febd000     Deferred        libnss_files.so.2
ELF     0x7febd000-7fed2000     Deferred        libnsl.so.1
ELF     0x7fed2000-7fedb000     Deferred        libnss_compat.so.2
ELF     0x7fede000-7fee2000     Deferred        libgpg-error.so.0
ELF     0x7fee2000-7fee6000     Deferred        libxfixes.so.3
ELF     0x7fee6000-7fee9000     Deferred        libxrandr.so.2
ELF     0x7fee9000-7ff0b000     Deferred        libm.so.6
ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7e00000-b7e02000     Deferred        xlcutf8load.so.2
ELF     0xb7e02000-b7e09000     Deferred        libsm.so.6
ELF     0xb7e0a000-b7e0d000     Deferred        libdl.so.2
ELF     0xb7e0d000-b7f3b000     Deferred        libc.so.6
ELF     0xb7f3c000-b7f4e000     Deferred        libpthread.so.0
ELF     0xb7f4e000-b7f67000     Export          libwine.so.1
ELF     0xb7f67000-b7f6a000     Deferred        libxau.so.6
ELF     0xb7f6a000-b7f73000     Deferred        libnss_nis.so.2
ELF     0xb7f78000-b7f8e000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000031 (D) C:\Program Files\Picasa2\Picasa2.exe
        00000032    0 <==
0000002f
        00000030    0
0000001b
        00000021    1
        0000001c    0
WineDbg terminated on pid 0x31
```
I have the latest version of Wine and the latest Picasa
any ideas what's the source of this error?

---

