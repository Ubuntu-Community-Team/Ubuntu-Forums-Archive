---
title: "Errors with WINE and Magic Workstation"
date: 2007-07-03
forum: Gaming &amp; Leisure
---

### Post by ielliott on 2007-07-03
WINE 0.9.40

I get this when i try and run magic workstation

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
fixme:win:EnumDisplayDevicesW ((null),0,0x33f698,0x00000000), stub!
wine: Unhandled page fault on write access to 0x00000000 at address 0x7bc3a537 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc3a537).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3a537 ESP:0033f2dc EBP:0033f324 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000000 EBX:7bc7c138 ECX:00000000 EDX:00000000
 ESI:0000000b EDI:003c0000
Stack dump:
0x0033f2dc:  000003ec 0033f310 00cf4104 00000000
0x0033f2ec:  00000001 00000001 00000000 0033f880
0x0033f2fc:  0033f9bd 0033f320 7bc37961 00000053
0x0033f30c:  00176e00 00000000 7bc3a52b 7bc7c138
0x0033f31c:  0000000b 003c0000 0033fe84 7bc407d4
0x0033f32c:  00000000 00030000 0033fd34 7bc37961
Backtrace:
=>1 0x7bc3a537 LdrQueryProcessModuleInformation+0x17() in ntdll (0x0033f324)
  2 0x7bc407d4 NtQuerySystemInformation+0x444() in ntdll (0x0033fe84)
  3 0x003d129f (0x0033fec8)
  4 0x003d2d00 (0x0033fee0)
  5 0x00000000 (0x00a3147b)
  6 0x5d895b5b (0x5d895b5d)
  7 0x00000000 (0x00000000)
0x7bc3a537 LdrQueryProcessModuleInformation+0x17 in ntdll: movl $0x0,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (97 modules)
PE        400000-  a47000       Deferred        magicworkstation
PE        a50000-  b1f000       Deferred        mwsdraw
PE      70d00000-70ea0000       Deferred        gdiplus
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bdc8000-7bddd000       Deferred        midimap<elf>
  \-PE  7bdd0000-7bddd000       \               midimap
ELF     7bddd000-7be03000       Deferred        msacm32<elf>
  \-PE  7bde0000-7be03000       \               msacm32
ELF     7be03000-7be1b000       Deferred        msacm32<elf>
  \-PE  7be10000-7be1b000       \               msacm32
ELF     7be3f000-7be90000       Deferred        libgcrypt.so.11
ELF     7be90000-7bf00000       Deferred        libgnutls.so.13
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf12000-7bf16000       Deferred        libgpg-error.so.0
ELF     7bf16000-7bf2b000       Deferred        libtasn1.so.3
ELF     7bf2b000-7bf59000       Deferred        libcrypt.so.1
ELF     7bf69000-7bf9a000       Deferred        libcups.so.2
ELF     7bf9a000-7bfcc000       Deferred        uxtheme<elf>
  \-PE  7bfa0000-7bfcc000       \               uxtheme
ELF     7bfcc000-7bfd5000       Deferred        libxcursor.so.1
ELF     7bfd5000-7bfdb000       Deferred        libxrandr.so.2
ELF     7cd89000-7cd8e000       Deferred        libxfixes.so.3
ELF     7cd8e000-7cd96000       Deferred        libxrender.so.1
ELF     7d754000-7d75d000       Deferred        librt.so.1
ELF     7d761000-7d764000       Deferred        libxinerama.so
ELF     7d827000-7e158000       Deferred        fglrx_dri.so
ELF     7e158000-7e1f8000       Deferred        libgl.so.1
ELF     7e1f8000-7e1fd000       Deferred        libxdmcp.so.6
ELF     7e1fd000-7e200000       Deferred        libxau.so.6
ELF     7e200000-7e2f1000       Deferred        libx11.so.6
ELF     7e2f1000-7e2ff000       Deferred        libxext.so.6
ELF     7e2ff000-7e304000       Deferred        libxxf86vm.so.1
ELF     7e304000-7e31c000       Deferred        libice.so.6
ELF     7e31c000-7e325000       Deferred        libsm.so.6
ELF     7e325000-7e3b5000       Deferred        winex11<elf>
  \-PE  7e330000-7e3b5000       \               winex11
ELF     7e445000-7e465000       Deferred        libexpat.so.1
ELF     7e465000-7e490000       Deferred        libfontconfig.so.1
ELF     7e490000-7e4a4000       Deferred        libz.so.1
ELF     7e4a4000-7e50f000       Deferred        libfreetype.so.6
ELF     7e50f000-7e524000       Deferred        psapi<elf>
  \-PE  7e520000-7e524000       \               psapi
ELF     7e524000-7e56e000       Deferred        dbghelp<elf>
  \-PE  7e530000-7e56e000       \               dbghelp
ELF     7e56e000-7e585000       Deferred        imagehlp<elf>
  \-PE  7e570000-7e585000       \               imagehlp
ELF     7e585000-7e613000       Deferred        winmm<elf>
  \-PE  7e590000-7e613000       \               winmm
ELF     7e613000-7e633000       Deferred        hhctrl<elf>
  \-PE  7e620000-7e633000       \               hhctrl
ELF     7e633000-7e6d4000       Deferred        comdlg32<elf>
  \-PE  7e640000-7e6d4000       \               comdlg32
ELF     7e6d4000-7e72c000       Deferred        shlwapi<elf>
  \-PE  7e6e0000-7e72c000       \               shlwapi
ELF     7e72c000-7e82a000       Deferred        shell32<elf>
  \-PE  7e740000-7e82a000       \               shell32
ELF     7e82a000-7e85d000       Deferred        winspool<elf>
  \-PE  7e830000-7e85d000       \               winspool
ELF     7e85d000-7e87a000       Deferred        imm32<elf>
  \-PE  7e860000-7e87a000       \               imm32
ELF     7e87a000-7e937000       Deferred        comctl32<elf>
  \-PE  7e880000-7e937000       \               comctl32
ELF     7e937000-7e94b000       Deferred        lz32<elf>
  \-PE  7e940000-7e94b000       \               lz32
ELF     7e94b000-7e965000       Deferred        version<elf>
  \-PE  7e950000-7e965000       \               version
ELF     7e965000-7e985000       Deferred        mpr<elf>
  \-PE  7e970000-7e985000       \               mpr
ELF     7e985000-7e998000       Deferred        libresolv.so.2
ELF     7e998000-7e9b6000       Deferred        iphlpapi<elf>
  \-PE  7e9a0000-7e9b6000       \               iphlpapi
ELF     7e9b6000-7ea0e000       Deferred        rpcrt4<elf>
  \-PE  7e9c0000-7ea0e000       \               rpcrt4
ELF     7ea0e000-7eaad000       Deferred        ole32<elf>
  \-PE  7ea20000-7eaad000       \               ole32
ELF     7eaad000-7eb4a000       Deferred        oleaut32<elf>
  \-PE  7eac0000-7eb4a000       \               oleaut32
ELF     7eb4a000-7eb92000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb92000       \               advapi32
ELF     7eb92000-7eb9e000       Deferred        libgcc_s.so.1
ELF     7ec98000-7ed58000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed58000       \               gdi32
ELF     7ed58000-7ee95000       Deferred        user32<elf>
  \-PE  7ed70000-7ee95000       \               user32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb3000-b7cbc000       Deferred        libnss_compat.so.2
ELF     b7cbd000-b7cc1000       Deferred        libdl.so.2
ELF     b7cc1000-b7e02000       Deferred        libc.so.6
ELF     b7e02000-b7e19000       Deferred        libpthread.so.0
ELF     b7e29000-b7f3d000       Deferred        libwine.so.1
ELF     b7f3f000-b7f5a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\ielliott\mtg-workstation\Magic Workstation\MagicWorkstation.exe
        0000000d    0
        00000009    0 <==

Thinking its something changed in the new version of Wine.

---

### Post by cogadh on 2007-07-04
I had similar problems installing and running games after the update to Wine 0.9.40. I did a complete uninstall and purge of Wine, then re-installed a clean (i.e. no DLL overrides, registry edits, etc.) and I was able to run things very well, much better than prior versions. I think some of the legacy modifications I had made to get games running in previous versions didn't sit well with the new version, and the house cleaning I did seems to have fixed it.

---

