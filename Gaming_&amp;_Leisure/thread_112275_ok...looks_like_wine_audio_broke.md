---
title: "ok...looks like wine audio broke"
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Nrvnqsr on 2006-01-04
well, to make it short, I upgraded to 0.9.4
and tried running some games but none are giving sound I type "winecfg" to see whats wrong and clicked on the audio tab and then in the terminal this was posted.

> 
wine: Unhandled page fault on write access to 0x6c43bbd8 at address 0x7ecaa3b1 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x6c43bbd8 in 32-bit code (0x7ecaa3b1).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ecaa3b1 ESP:7fadc6f4 EBP:7fadc71c EFLAGS:00210202(   - 00      - -RI1)
 EAX:7c0d5684 EBX:7ed46cd0 ECX:7c017848 EDX:7c0e61c8
 ESI:00000004 EDI:7c0d6148
Stack dump:
0x7fadc6f4:  7c1fddb8 7c0f6fe0 00000001 7d8a81a0
0x7fadc704:  00001388 7c0d5740 7fadc73c 7d8a81a0
0x7fadc714:  7c017850 7d8aa9d0 7fadc73c 7d8a382c
0x7fadc724:  7d8aa9e0 7c017848 00000004 7d57d504
0x7fadc734:  7c200094 7c20009c 7fadc76c 7d56ca34
0x7fadc744:  7c20009c 7c017850 00000001 7d50df38
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ecaa3b1 (0x7ecaa3b1)
  2 0x7d8a382c _ZN9__gnu_cxx10__mt_allocISsNS_20__common_pool_policyINS_6__poolELb1EEEE10deallocateEPSsj+0x5e in libartscbackend.so.0 (0x7d8a382c)
  3 0x7d56ca34 _ZN4Arts12InterfaceDefD1Ev+0x1a4 in libmcop.so.1 (0x7d56ca34)
  4 0x7d533759 _ZSt8_DestroyIN9__gnu_cxx17__normal_iteratorIPN4Arts12InterfaceDefESt6vectorIS3_SaIS3_EEEES6_EvT_S9_T0_+0x1f in libmcop.so.1 (0x7d533759)
  5 0x7d564350 _ZNSt6vectorIN4Arts12InterfaceDefESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_+0x6d0 in libmcop.so.1 (0x7d564350)
  6 0x7d564bdd _ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x64d in libmcop.so.1 (0x7d564bdd)
  7 0x7d5188ec _ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x56 in libmcop.so.1 (0x7d5188ec)
  8 0x7d51af5e _ZN4Arts9ModuleDefC1ERNS_6BufferE+0x136 in libmcop.so.1 (0x7d51af5e)
  9 0x7d51b658 _ZN4Arts10IDLFileReg7startupEv+0xe2 in libmcop.so.1 (0x7d51b658 )
  10 0x7d4b448c _ZN4Arts14StartupManager7startupEv+0x46 in libmcop.so.1 (0x7d4b448c)
  11 0x7d5257d6 _ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x3de in libmcop.so.1 (0x7d5257d6)
  12 0x7d8a1a37 arts_backend_init+0x8f in libartscbackend.so.0 (0x7d8a1a37)
  13 0x7dccb293 arts_init+0x3b in libartsc.so.0 (0x7dccb293)
  14 0x7da02f37 ARTS_WaveInit+0x27 in winearts (0x7da02f37)
  15 0x7d9ff1a2 ARTS_DriverProc+0x52 in winearts (0x7d9ff1a2)
  16 0x7ead567f in winmm (+0x1567f) (0x7ead567f)
  17 0x7ead5ca9 DRIVER_TryOpenDriver32+0xc9 in winmm (0x7ead5ca9)
  18 0x7ead5fa9 OpenDriver+0x169 in winmm (0x7ead5fa9)
  19 0x7ead607e OpenDriverA+0x3e in winmm (0x7ead607e)
  20 0x7fafbc02 in winecfg (+0xbc02) (0x7fafbc02)
  21 0x7fafcbb8 AudioDlgProc+0x298 in winecfg (0x7fafcbb8 )
  22 0x7f6f86ba WINPROC_wrapper+0x1a in user32 (0x7f6f86ba)
  23 0x7f6f9260 in user32 (+0x89260) (0x7f6f9260)
  24 0x7f6fe2de CallWindowProcW+0x1ae in user32 (0x7f6fe2de)
  25 0x7f69f1f7 DefDlgProcW+0x57 in user32 (0x7f69f1f7)
  26 0x7f6f86ba WINPROC_wrapper+0x1a in user32 (0x7f6f86ba)
  27 0x7f6f9260 in user32 (+0x89260) (0x7f6f9260)
  28 0x7f6fe526 CallWindowProcW+0x3f6 in user32 (0x7f6fe526)
  29 0x7f6cd83f in user32 (+0x5d83f) (0x7f6cd83f)
  30 0x7f6d0f56 SendMessageTimeoutW+0x156 in user32 (0x7f6d0f56)
  31 0x7f6d0fa5 SendMessageW+0x35 in user32 (0x7f6d0fa5)
  32 0x7f6a4382 in user32 (+0x34382) (0x7f6a4382)
  33 0x7f6a4d1d CreateDialogIndirectParamAorW+0x2d in user32 (0x7f6a4d1d)
  34 0x7f6a4d5b CreateDialogIndirectParamW+0x2b in user32 (0x7f6a4d5b)
  35 0x7eba7653 in comctl32 (+0x47653) (0x7eba7653)
  36 0x7eba8991 in comctl32 (+0x48991) (0x7eba8991)
  37 0x7ebaa56a PROPSHEET_DialogProc+0x95a in comctl32 (0x7ebaa56a)
  38 0x7f6f86ba WINPROC_wrapper+0x1a in user32 (0x7f6f86ba)
  39 0x7f6f9260 in user32 (+0x89260) (0x7f6f9260)
  40 0x7f6fe2de CallWindowProcW+0x1ae in user32 (0x7f6fe2de)
  41 0x7f69f1f7 DefDlgProcW+0x57 in user32 (0x7f69f1f7)
  42 0x7f6f86ba WINPROC_wrapper+0x1a in user32 (0x7f6f86ba)
  43 0x7f6f9260 in user32 (+0x89260) (0x7f6f9260)
  44 0x7f6fe526 CallWindowProcW+0x3f6 in user32 (0x7f6fe526)
  45 0x7f6cd83f in user32 (+0x5d83f) (0x7f6cd83f)
  46 0x7f6d0f56 SendMessageTimeoutW+0x156 in user32 (0x7f6d0f56)
  47 0x7f6d0fa5 SendMessageW+0x35 in user32 (0x7f6d0fa5)
  48 0x7ebbc31c in comctl32 (+0x5c31c) (0x7ebbc31c)
  49 0x7ebc03a6 in comctl32 (+0x603a6) (0x7ebc03a6)
  50 0x7f6f86ba WINPROC_wrapper+0x1a in user32 (0x7f6f86ba)
  51 0x7f6f9260 in user32 (+0x89260) (0x7f6f9260)
  52 0x7f6fe2de CallWindowProcW+0x1ae in user32 (0x7f6fe2de)
  53 0x7f6ce03c DispatchMessageW+0x16c in user32 (0x7f6ce03c)
  54 0x7f6a2e42 IsDialogMessageW+0xe2 in user32 (0x7f6a2e42)
  55 0x7eba64ab in comctl32 (+0x464ab) (0x7eba64ab)
  56 0x7eba80d6 PropertySheetW+0x246 in comctl32 (0x7eba80d6)
  57 0x7fb010f5 WinMain+0x335 in winecfg (0x7fb010f5)
  58 0x7fb0485e main+0x8e in winecfg (0x7fb0485e)
  59 0x7fb047aa in winecfg (+0x147aa) (0x7fb047aa)
  60 0x7fcddce7 in kernel32 (+0x4dce7) (0x7fcddce7)
  61 0xb7ee2c17 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7ee2c17)
0x7ecaa3b1: decl        0x0(%edx,%eax,4)
Modules:
Module  Address                 Debug info      Name (104 modules)
ELF     0x799b6000-799be000     Deferred        libxrender.so.1
ELF     0x7be8c000-7bf00000     Deferred        ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7d308000-7d34e000     Deferred        libkmedia2_idl.so.1
ELF     0x7d34e000-7d375000     Deferred        libvorbis.so.0
ELF     0x7d375000-7d474000     Deferred        libvorbisenc.so.2
ELF     0x7d474000-7d58c000     Export          libmcop.so.1
ELF     0x7d58c000-7d5da000     Deferred        libxt.so.6
ELF     0x7d5da000-7d5ee000     Deferred        libaudio.so.2
ELF     0x7d5ee000-7d60f000     Deferred        libaudiofile.so.0
ELF     0x7d60f000-7d6cc000     Deferred        libartsflow_idl.so.1
ELF     0x7d6cc000-7d734000     Deferred        libsoundserver_idl.so.1
ELF     0x7d734000-7d898000     Deferred        libartsflow.so.1
ELF     0x7d898000-7d8ab000     Export          libartscbackend.so.0
ELF     0x7d8ab000-7d92c000     Deferred        libglib-2.0.so.0
ELF     0x7d92c000-7d9df000     Deferred        libasound.so.2
ELF     0x7d9e5000-7d9ed000     Deferred        libvorbisfile.so.3
ELF     0x7d9ed000-7da07000     Export          winearts<elf>
  \-PE  0x7d9f0000-7da07000     \               winearts
ELF     0x7da4b000-7da60000     Deferred        midimap<elf>
  \-PE  0x7da50000-7da60000     \               midimap
ELF     0x7db71000-7db7b000     Deferred        libesd.so.0
ELF     0x7db7b000-7db9d000     Deferred        msacm32<elf>
  \-PE  0x7db80000-7db9d000     \               msacm32
ELF     0x7db9d000-7dbb4000     Deferred        msacm<elf>
  \-PE  0x7dba0000-7dbb4000     \               msacm
ELF     0x7dbb4000-7dbf6000     Deferred        wineoss<elf>
  \-PE  0x7dbc0000-7dbf6000     \               wineoss
ELF     0x7dbf6000-7dc42000     Deferred        libgcrypt.so.11
ELF     0x7dc42000-7dca4000     Deferred        libgnutls.so.11
ELF     0x7dca4000-7dcc1000     Deferred        libcups.so.2
ELF     0x7dcc1000-7dcc6000     Deferred        libogg.so.0
ELF     0x7dcc6000-7dcca000     Deferred        libgthread-2.0.so.0
ELF     0x7dcca000-7dcd0000     Export          libartsc.so.0
ELF     0x7dd10000-7dd20000     Deferred        libtasn1.so.2
ELF     0x7dd28000-7dd2b000     Deferred        libgmodule-2.0.so.0
ELF     0x7de01000-7de0a000     Deferred        libxcursor.so.1
ELF     0x7de19000-7de34000     Deferred        imm32<elf>
  \-PE  0x7de20000-7de34000     \               imm32
ELF     0x7de34000-7de50000     Deferred        ximcp.so.2
ELF     0x7de50000-7de58000     Deferred        librt.so.1
ELF     0x7df12000-7e7a9000     Deferred        fglrx_dri.so
ELF     0x7e7a9000-7e848000     Deferred        libgl.so.1
ELF     0x7e848000-7e908000     Deferred        libx11.so.6
ELF     0x7e908000-7e915000     Deferred        libxext.so.6
ELF     0x7e915000-7e91a000     Deferred        libxxf86vm.so.1
ELF     0x7e91a000-7e91f000     Deferred        libxxf86dga.so.1
ELF     0x7e91f000-7e938000     Deferred        libice.so.6
ELF     0x7e938000-7e9b5000     Deferred        winex11<elf>
  \-PE  0x7e950000-7e9b5000     \               winex11
ELF     0x7e9b5000-7e9d4000     Deferred        libexpat.so.1
ELF     0x7e9d4000-7ea02000     Deferred        libfontconfig.so.1
ELF     0x7ea02000-7ea16000     Deferred        libz.so.1
ELF     0x7ea16000-7ea80000     Deferred        libfreetype.so.6
ELF     0x7ea80000-7eab0000     Deferred        uxtheme<elf>
  \-PE  0x7ea90000-7eab0000     \               uxtheme
ELF     0x7eab0000-7eb31000     Export          winmm<elf>
  \-PE  0x7eac0000-7eb31000     \               winmm
ELF     0x7eb31000-7eb59000     Deferred        winspool<elf>
  \-PE  0x7eb40000-7eb59000     \               winspool
ELF     0x7eb59000-7ec08000     Export          comctl32<elf>
  \-PE  0x7eb60000-7ec08000     \               comctl32
ELF     0x7ec08000-7ec26000     Deferred        iphlpapi<elf>
  \-PE  0x7ec10000-7ec26000     \               iphlpapi
ELF     0x7ec26000-7ec6a000     Deferred        rpcrt4<elf>
  \-PE  0x7ec40000-7ec6a000     \               rpcrt4
ELF     0x7ed50000-7f650000     Deferred        gdi32<elf>
  \-PE  0x7ed90000-7f650000     \               gdi32
ELF     0x7f650000-7f769000     Export          user32<elf>
  \-PE  0x7f670000-7f769000     \               user32
ELF     0x7f769000-7f7a5000     Deferred        advapi32<elf>
  \-PE  0x7f770000-7f7a5000     \               advapi32
ELF     0x7f7a5000-7f82b000     Deferred        ole32<elf>
  \-PE  0x7f7c0000-7f82b000     \               ole32
ELF     0x7f82b000-7f880000     Deferred        shlwapi<elf>
  \-PE  0x7f840000-7f880000     \               shlwapi
ELF     0x7f880000-7f93e000     Deferred        shell32<elf>
  \-PE  0x7f8a0000-7f93e000     \               shell32
ELF     0x7f93e000-7f9d0000     Deferred        comdlg32<elf>
  \-PE  0x7f950000-7f9d0000     \               comdlg32
ELF     0x7fae0000-7fae7000     Deferred        libsm.so.6
ELF     0x7fae7000-7fb20000     Export          winecfg<elf>
  \-PE  0x7faf0000-7fb20000     \               winecfg
ELF     0x7fb21000-7fb2c000     Deferred        libgcc_s.so.1
ELF     0x7fc74000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe84000     Deferred        libxdmcp.so.6
ELF     0x7fe84000-7fe8e000     Deferred        libnss_files.so.2
ELF     0x7fe8e000-7fe97000     Deferred        libnss_nis.so.2
ELF     0x7fe97000-7feac000     Deferred        libnsl.so.1
ELF     0x7feac000-7feb5000     Deferred        libnss_compat.so.2
ELF     0x7feb7000-7febb000     Deferred        libgpg-error.so.0
ELF     0x7febb000-7febf000     Deferred        libxfixes.so.3
ELF     0x7febf000-7fec1000     Deferred        xlcutf8load.so.2
ELF     0x7fec1000-7fec4000     Deferred        libxrandr.so.2
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7d9a000-b7d9d000     Deferred        libdl.so.2
ELF     0xb7d9d000-b7ecb000     Deferred        libc.so.6
ELF     0xb7ecc000-b7ede000     Deferred        libpthread.so.0
ELF     0xb7ede000-b7ef8000     Export          libwine.so.1
ELF     0xb7ef8000-b7efb000     Deferred        libxau.so.6
ELF     0xb7f0a000-b7f20000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==
WineDbg terminated on pid 0x8


in 0.9.3 audio run very well, and I tried downgrading to see if its just the new version but no, I'm still a noobish in this stuff so anyone gotten any ideas? appreciate the help.

---

