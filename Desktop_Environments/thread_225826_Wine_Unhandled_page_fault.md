---
title: "Wine Unhandled page fault"
date: 2006-07-30
forum: Desktop Environments
---

### Post by FurryNemesis on 2006-07-30
when I try to add a game under the add applications box with winecfg, I get the following error: (Apologies for bloat but I thought I'd better post the lot)

wine: Unhandled page fault on read access to 0x00000000 at address 0xb7e247b8 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7e247b8).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:b7e247b8 ESP:7fb4c878 EBP:7fb4c888 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000056 EBX:b7ee3adc ECX:7fbbbc68 EDX:00000076
 ESI:00000000 EDI:7fb8452a
Stack dump:
0x7fb4c878:  56b4c8b8 7fb89c34 7fd4f7a0 7fd49e60
0x7fb4c888:  7fb4c8f8 7fb82276 7fb8452a 00000000
0x7fb4c898:  00000017 7fb850b1 7fb4c8b8 b7dfc76b
0x7fb4c8a8:  7fd54530 7fb862f7 7fb4c803 7fb89c34
0x7fb4c8b8:  7fb4c8f8 7fb81a82 7fd54530 7fb862f7
0x7fb4c8c8:  00000000 7fb76630 0001002e 000003f4
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0xb7e247b8 __strcasecmp+0x38 in libc.so.6 (0xb7e247b8)
  2 0x7fb82276 get_reg_key+0x121 in winecfg (0x7fb82276)
  3 0x7fb76bd7 AppDlgProc+0x469 in winecfg (0x7fb76bd7)
  4 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  5 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  6 0x7f740634 CallWindowProcW+0x1c8 in user32 (0x7f740634)
  7 0x7f6d2b94 DefDlgProcW+0x91 in user32 (0x7f6d2b94)
  8 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  9 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  10 0x7f7408e7 CallWindowProcW+0x47b in user32 (0x7f7408e7)
  11 0x7f70885c in user32 (+0x6885c) (0x7f70885c)
  12 0x7f70c6c1 SendMessageTimeoutW+0x186 in user32 (0x7f70c6c1)
  13 0x7f70c71e SendMessageW+0x50 in user32 (0x7f70c71e)
  14 0x7f406517 in comctl32 (+0x26517) (0x7f406517)
  15 0x7f414ff5 in comctl32 (+0x34ff5) (0x7f414ff5)
  16 0x7f413c6a in comctl32 (+0x33c6a) (0x7f413c6a)
  17 0x7f4146b5 in comctl32 (+0x346b5) (0x7f4146b5)
  18 0x7f414f8a in comctl32 (+0x34f8a) (0x7f414f8a)
  19 0x7f413c6a in comctl32 (+0x33c6a) (0x7f413c6a)
  20 0x7f4146b5 in comctl32 (+0x346b5) (0x7f4146b5)
  21 0x7f4194e7 in comctl32 (+0x394e7) (0x7f4194e7)
  22 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  23 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  24 0x7f73e15d CallWindowProcA+0x1d5 in user32 (0x7f73e15d)
  25 0x7f7087cd in user32 (+0x687cd) (0x7f7087cd)
  26 0x7f70c473 SendMessageTimeoutA+0x226 in user32 (0x7f70c473)
  27 0x7f70c52e SendMessageA+0x50 in user32 (0x7f70c52e)
  28 0x7fb773f8 AppDlgProc+0xc8a in winecfg (0x7fb773f8)
  29 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  30 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  31 0x7f740634 CallWindowProcW+0x1c8 in user32 (0x7f740634)
  32 0x7f6d2b94 DefDlgProcW+0x91 in user32 (0x7f6d2b94)
  33 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  34 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  35 0x7f7408e7 CallWindowProcW+0x47b in user32 (0x7f7408e7)
  36 0x7f70885c in user32 (+0x6885c) (0x7f70885c)
  37 0x7f70c6c1 SendMessageTimeoutW+0x186 in user32 (0x7f70c6c1)
  38 0x7f70c71e SendMessageW+0x50 in user32 (0x7f70c71e)
  39 0x7f6ba73b in user32 (+0x1a73b) (0x7f6ba73b)
  40 0x7f6bb1eb in user32 (+0x1b1eb) (0x7f6bb1eb)
  41 0x7f739d3a WINPROC_wrapper+0x1a in user32 (0x7f739d3a)
  42 0x7f73a842 in user32 (+0x9a842) (0x7f73a842)
  43 0x7f740634 CallWindowProcW+0x1c8 in user32 (0x7f740634)
  44 0x7f70905e DispatchMessageW+0x169 in user32 (0x7f70905e)
  45 0x7f6d75fb IsDialogMessageW+0xfb in user32 (0x7f6d75fb)
  46 0x7f4268d5 in comctl32 (+0x468d5) (0x7f4268d5)
  47 0x7f428905 PropertySheetW+0x259 in comctl32 (0x7f428905)
  48 0x7fb7f2df WinMain+0x354 in winecfg (0x7fb7f2df)
  49 0x7fb84257 main+0xa7 in winecfg (0x7fb84257)
  50 0x7fb84193 in winecfg (+0x14193) (0x7fb84193)
  51 0x7fc5b311 in kernel32 (+0x4b311) (0x7fc5b311)
  52 0xb7f0bddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f0bddb)
0xb7e247b8 __strcasecmp+0x38 in libc.so.6: movzbl       0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (81 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e51b000-7e530000     Deferred        midimap<elf>
  \-PE  0x7e520000-7e530000     \               midimap
ELF     0x7e643000-7e669000     Deferred        msacm32<elf>
  \-PE  0x7e650000-7e669000     \               msacm32
ELF     0x7e669000-7e681000     Deferred        msacm<elf>
  \-PE  0x7e670000-7e681000     \               msacm
ELF     0x7e681000-7e6c5000     Deferred        wineoss<elf>
  \-PE  0x7e690000-7e6c5000     \               wineoss
ELF     0x7e6c5000-7e711000     Deferred        libgcrypt.so.11
ELF     0x7e711000-7e721000     Deferred        libtasn1.so.2
ELF     0x7e721000-7e74e000     Deferred        libcrypt.so.1
ELF     0x7e75a000-7e7c3000     Deferred        libgnutls.so.12
ELF     0x7e7c3000-7e7f0000     Deferred        libcups.so.2
ELF     0x7e834000-7e838000     Deferred        libgpg-error.so.0
ELF     0x7e8a3000-7e8a8000     Deferred        libxfixes.so.3
ELF     0x7e8a8000-7e8b1000     Deferred        libxcursor.so.1
ELF     0x7e8b1000-7e8cd000     Deferred        imm32<elf>
  \-PE  0x7e8c0000-7e8cd000     \               imm32
ELF     0x7e8cd000-7e8d0000     Deferred        libxrandr.so.2
ELF     0x7e8d0000-7e8d8000     Deferred        libxrender.so.1
ELF     0x7e8d8000-7f029000     Deferred        libglcore.so.1
ELF     0x7f029000-7f0a1000     Deferred        libgl.so.1
ELF     0x7f0a1000-7f187000     Deferred        libx11.so.6
ELF     0x7f187000-7f19f000     Deferred        libice.so.6
ELF     0x7f19f000-7f222000     Deferred        winex11<elf>
  \-PE  0x7f1b0000-7f222000     \               winex11
ELF     0x7f222000-7f241000     Deferred        libexpat.so.1
ELF     0x7f241000-7f26f000     Deferred        libfontconfig.so.1
ELF     0x7f26f000-7f283000     Deferred        libz.so.1
ELF     0x7f283000-7f2ec000     Deferred        libfreetype.so.6
ELF     0x7f2ec000-7f31d000     Deferred        uxtheme<elf>
  \-PE  0x7f2f0000-7f31d000     \               uxtheme
ELF     0x7f31d000-7f3a5000     Deferred        winmm<elf>
  \-PE  0x7f330000-7f3a5000     \               winmm
ELF     0x7f3a5000-7f3d1000     Deferred        winspool<elf>
  \-PE  0x7f3b0000-7f3d1000     \               winspool
ELF     0x7f3d1000-7f491000     Export          comctl32<elf>
  \-PE  0x7f3e0000-7f491000     \               comctl32
ELF     0x7f491000-7f4b0000     Deferred        iphlpapi<elf>
  \-PE  0x7f4a0000-7f4b0000     \               iphlpapi
ELF     0x7f4b0000-7f4f9000     Deferred        rpcrt4<elf>
  \-PE  0x7f4c0000-7f4f9000     \               rpcrt4
ELF     0x7f5ce000-7f67f000     Deferred        gdi32<elf>
  \-PE  0x7f5e0000-7f67f000     \               gdi32
ELF     0x7f67f000-7f7ab000     Export          user32<elf>
  \-PE  0x7f6a0000-7f7ab000     \               user32
ELF     0x7f7ab000-7f7eb000     Deferred        advapi32<elf>
  \-PE  0x7f7c0000-7f7eb000     \               advapi32
ELF     0x7f7eb000-7f87c000     Deferred        ole32<elf>
  \-PE  0x7f800000-7f87c000     \               ole32
ELF     0x7f87c000-7f8d7000     Deferred        shlwapi<elf>
  \-PE  0x7f890000-7f8d7000     \               shlwapi
ELF     0x7f8d7000-7f9a3000     Deferred        shell32<elf>
  \-PE  0x7f8f0000-7f9a3000     \               shell32
ELF     0x7f9a3000-7fa40000     Deferred        comdlg32<elf>
  \-PE  0x7f9b0000-7fa40000     \               comdlg32
ELF     0x7fb50000-7fb5d000     Deferred        libxext.so.6
ELF     0x7fb5d000-7fbb0000     Export          winecfg<elf>
  \-PE  0x7fb70000-7fbb0000     \               winecfg
ELF     0x7fbb1000-7fbb6000     Deferred        libxxf86vm.so.1
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86dga.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe03000-7fe0d000     Deferred        libgcc_s.so.1
ELF     0x7fe0d000-7fe17000     Deferred        libnss_files.so.2
ELF     0x7fe17000-7fe20000     Deferred        libnss_nis.so.2
ELF     0x7fe20000-7fe35000     Deferred        libnsl.so.1
ELF     0x7fe35000-7fe3e000     Deferred        libnss_compat.so.2
ELF     0x7fe3f000-7fe42000     Deferred        libxau.so.6
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4c000-7fe4e000     Deferred        libnvidia-tls.so.1
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7db6000-b7db9000     Deferred        libdl.so.2
ELF     0xb7db9000-b7ee8000     Export          libc.so.6
ELF     0xb7ee8000-b7efa000     Deferred        libpthread.so.0
ELF     0xb7f07000-b7f21000     Export          libwine.so.1
ELF     0xb7f24000-b7f3a000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==

Does anyone know how to fix this or is a full re-install/compile from source in order?

Thanks in advance.

---

### Post by hobong on 2008-06-13
Same Problem here ....
I'm using Hardy Heron 8.04
and wine-1.0-rc4 

Does anyone can solved the problem ?

---

### Post by Joeb454 on 2008-06-13
I'd suggest creating a new thread outside the forum archive for this, and referencing the wine version, and what program you're trying to use in wine, rather than reviving a ~2 year old thread :)

---

### Post by PmDematagoda on 2008-06-13
This thread is closed.

---

