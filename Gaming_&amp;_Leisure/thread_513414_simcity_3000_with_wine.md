---
title: "simcity 3000 with wine"
date: 2007-07-30
forum: Gaming &amp; Leisure
---

### Post by antiemptyv on 2007-07-30
i'm trying to run smicity 3000 in wine.  it has installed fine and shows up in wine's programs menu.  when running it from the menu or from a terminal, the maxis splash screen comes up, then disappears as it should, but nothing else happens.  i get the following output when trying to run 
```
wine .wine/drive_c/Program\ Files/Maxis/SimCity\ 3000\ Unlimited/Apps/sc3U.exe 
```
in a terminal.  
```
err:x11drv:X11DRV_CreateWindow invalid window width -948620
err:x11drv:X11DRV_CreateWindow invalid window height -49211
wine: Unhandled page fault on read access to 0x00a300f9 at address 0x7bc3cf17 (thread 0014), starting debugger...
Unhandled exception: page fault on read access to 0x00a300f9 in 32-bit code (0x7bc3cf17).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc3cf17 ESP:0034fdb0 EBP:0034fea8 EFLAGS:00210206(   - 00      - RIP1)
 EAX:006300f9 EBX:7bc7b498 ECX:00a300fb EDX:004cf050
 ESI:00a300f9 EDI:004cf054
Stack dump:
0x0034fdb0:  7b820000 00000001 00000000 0034fe90
0x0034fdc0:  0034fe84 00000000 00000000 00000000
0x0034fdd0:  00000000 00000000 0034fe8c 0034fe88
0x0034fde0:  00a300fb 7bc71a27 00000000 18000004
0x0034fdf0:  001104a0 001107f0 00110654 00000005
0x0034fe00:  0000000d 00000000 00000000 004f27fa
Backtrace:
=>1 0x7bc3cf17 in ntdll (+0x2cf17) (0x0034fea8)
  2 0x7bc3d5f4 LdrInitializeThunk+0x114() in ntdll (0x0034ff08)
  3 0x7b874e4a in kernel32 (+0x54e4a) (0x0034ffe8)
  4 0xb7e7faf7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc3cf17: movzwl      0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (62 modules)
PE        400000-  51b000       Deferred        sc3u.icd
PE        8e0000-  910000       Deferred        dplayerx
PE      10000000-10027000       Deferred        uv
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc97000       Export          ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2ae000-7d2c2000       Deferred        lz32<elf>
  \-PE  7d2b0000-7d2c2000       \               lz32
ELF     7d2c2000-7d2dc000       Deferred        version<elf>
  \-PE  7d2d0000-7d2dc000       \               version
ELF     7d2dc000-7d2ef000       Deferred        libresolv.so.2
ELF     7d2fc000-7d355000       Deferred        rpcrt4<elf>
  \-PE  7d310000-7d355000       \               rpcrt4
ELF     7d355000-7d3f4000       Deferred        ole32<elf>
  \-PE  7d360000-7d3f4000       \               ole32
ELF     7d3f4000-7d43c000       Deferred        dsound<elf>
  \-PE  7d400000-7d43c000       \               dsound
ELF     7d43c000-7d4ca000       Deferred        winmm<elf>
  \-PE  7d450000-7d4ca000       \               winmm
ELF     7d727000-7d745000       Deferred        iphlpapi<elf>
  \-PE  7d730000-7d745000       \               iphlpapi
ELF     7d747000-7d74c000       Deferred        libxfixes.so.3
ELF     7d74c000-7d755000       Deferred        libxcursor.so.1
ELF     7d755000-7d772000       Deferred        imm32<elf>
  \-PE  7d760000-7d772000       \               imm32
ELF     7d772000-7d778000       Deferred        libxrandr.so.2
ELF     7d778000-7d780000       Deferred        libxrender.so.1
ELF     7df18000-7df1a000       Deferred        libnvidia-tls.so.1
ELF     7df1a000-7e7a0000       Deferred        libglcore.so.1
ELF     7e7a0000-7e82c000       Deferred        libgl.so.1
ELF     7e82c000-7e831000       Deferred        libxdmcp.so.6
ELF     7e831000-7e834000       Deferred        libxau.so.6
ELF     7e834000-7e925000       Deferred        libx11.so.6
ELF     7e925000-7e933000       Deferred        libxext.so.6
ELF     7e933000-7e938000       Deferred        libxxf86vm.so.1
ELF     7e938000-7e950000       Deferred        libice.so.6
ELF     7e950000-7e959000       Deferred        libsm.so.6
ELF     7e959000-7e9e2000       Deferred        winex11<elf>
  \-PE  7e970000-7e9e2000       \               winex11
ELF     7ea7d000-7ea9d000       Deferred        libexpat.so.1
ELF     7ea9d000-7eac8000       Deferred        libfontconfig.so.1
ELF     7eac8000-7eadc000       Deferred        libz.so.1
ELF     7eadc000-7eb47000       Deferred        libfreetype.so.6
ELF     7eb47000-7eb8f000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb8f000       \               advapi32
ELF     7eb8f000-7eb9b000       Deferred        libgcc_s.so.1
ELF     7ec85000-7ed45000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed45000       \               gdi32
ELF     7ed45000-7ee82000       Deferred        user32<elf>
  \-PE  7ed60000-7ee82000       \               user32
ELF     7ee82000-7ee8d000       Deferred        libnss_files.so.2
ELF     7ee8d000-7eea4000       Deferred        libnsl.so.1
ELF     7eea4000-7eead000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d0e000-b7d12000       Deferred        libdl.so.2
ELF     b7d12000-b7e53000       Deferred        libc.so.6
ELF     b7e54000-b7e6b000       Deferred        libpthread.so.0
ELF     b7e78000-b7f8c000       Export          libwine.so.1
ELF     b7f8e000-b7fa9000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000013 (D) Z:\home\matt\.wine\drive_c\Program Files\Maxis\SimCity 3000 Unlimited\Apps\SC3U.ICD
        00000014    0 <==
0000000d 
        00000010    0
        0000000f    0
        0000000e    0
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
```

i would love to get this game working.  since it's installed, it seems like it should be doable.  thanks in advance.

---

