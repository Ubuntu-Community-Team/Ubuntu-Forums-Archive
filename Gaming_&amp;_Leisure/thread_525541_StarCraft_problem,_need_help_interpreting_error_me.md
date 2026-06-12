---
title: "StarCraft problem, need help interpreting error message"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by DiceMan on 2007-08-14
I'm trying to run StarCraft using wine. Supposedly this should work fine but I can't seem to get it to work. I can start a single player game (although my mouse lags a bit - solution?) but when I try and start a multiplayer game, StarCraft crashes and I get the following message (see below). Unfortunately it's pretty much greek to me, does anyone know what it means and how to solve the problem? Thanks a lot :)
//DM

> wine .wine/drive_c/spel/starcraft/StarCraft.exe 
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17dcb8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17d438)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 16 to 8
wine: Unhandled page fault on write access to 0x0105c000 at address 0x3e0594 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x0105c000 in 32-bit code (0x003e0594).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:003e0594 ESP:0033eda0 EBP:0033ee50 EFLAGS:00010206(   - 00      - RIP1)
 EAX:c7c7c76f EBX:003e018c ECX:00000000 EDX:00000013
 ESI:025f1014 EDI:0105c000
Stack dump:
0x0033eda0:  00000000 0105b000 0105b000 00000000
0x0033edb0:  025f0010 7be4bda0 001cae00 0033edec
0x0033edc0:  00000000 00000001 00000002 7e4f5b2c
0x0033edd0:  0033edf0 7e44e64f 000016fa 7c04e3d8
0x0033ede0:  001cad44 7b8ad908 00000002 00000280
0x0033edf0:  01010000 0033ef6c 15029530 1505ec98
Backtrace:
=>1 0x003e0594 (0x0033ee50)
  2 0x15029789 in storm (+0x29789) (0x0033ee9c)
  3 0x150322cb in storm (+0x322cb) (0x0033eefc)
  4 0x15033ac4 in storm (+0x33ac4) (0x0033efb8)
  5 0x15034f19 in storm (+0x34f19) (0x0033f014)
  6 0x7ee152ea WINPROC_wrapper+0x1a() in user32 (0x0033f044)
  7 0x7ee15a1e in user32 (+0xa5a1e) (0x0033f084)
  8 0x7ee1a057 in user32 (+0xaa057) (0x0033f724)
  9 0x7ee1ab2a CallWindowProcW+0xaa() in user32 (0x0033f764)
  10 0x7ede28ab DispatchMessageW+0x15b() in user32 (0x0033f7a4)
  11 0x7edb173b IsDialogMessageW+0xfb() in user32 (0x0033f904)
  12 0x7ede2569 IsDialogMessageA+0x59() in user32 (0x0033f944)
  13 0x19020a9b in battle.snp (+0x20a9b) (0x0033f97c)
  14 0x1902c299 in battle.snp (+0x2c299) (0x0033fb90)
  15 0x1501f0c8 in storm (+0x1f0c8) (0x0033fbb4)
  16 0x1501f2f5 in storm (+0x1f2f5) (0x0033fc8c)
  17 0x004d3947 in starcraft (+0xd3947) (0x0033fd80)
  18 0x00452a54 in starcraft (+0x52a54) (0x0033fda4)
  19 0x004de0b6 in starcraft (+0xde0b6) (0x0033fdbc)
  20 0x004e05f7 in starcraft (+0xe05f7) (0x0033fdd4)
  21 0x004e06c0 in starcraft (+0xe06c0) (0x0033fde0)
  22 0x00404da5 in starcraft (+0x4da5) (0x0033ff08)
  23 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  24 0xb7ea8897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x003e0594: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (100 modules)
PE      400000-6eb000   Export          starcraft
PE      2000000-2011000 Deferred        local
PE      10000000-1001a000       Deferred        smackw32
PE      15000000-15069000       Export          storm
PE      19000000-19089000       Export          battle.snp
ELF     75c5c000-75c89000       Deferred        ws2_32<elf>
  \-PE  75c70000-75c89000       \               ws2_32
ELF     75c89000-75ca3000       Deferred        wsock32<elf>
  \-PE  75c90000-75ca3000       \               wsock32
ELF     760e7000-7610d000       Deferred        msacm32<elf>
  \-PE  760f0000-7610d000       \               msacm32
ELF     7610d000-76149000       Deferred        wineoss<elf>
  \-PE  76110000-76149000       \               wineoss
ELF     76149000-761d8000       Deferred        winmm<elf>
  \-PE  76160000-761d8000       \               winmm
ELF     7646f000-764ef000       Deferred        libglu.so.1
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7b931000-7b946000       Deferred        midimap<elf>
  \-PE  7b940000-7b946000       \               midimap
ELF     7b946000-7ba00000       Deferred        wined3d<elf>
  \-PE  7b960000-7ba00000       \               wined3d
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bdb7000-7bdcf000       Deferred        msacm32<elf>
  \-PE  7bdc0000-7bdcf000       \               msacm32
ELF     7bdcf000-7be18000       Deferred        dsound<elf>
  \-PE  7bde0000-7be18000       \               dsound
ELF     7be18000-7be68000       Deferred        ddraw<elf>
  \-PE  7be20000-7be68000       \               ddraw
ELF     7be68000-7be6c000       Deferred        libgpg-error.so.0
ELF     7be6c000-7bebd000       Deferred        libgcrypt.so.11
ELF     7bebd000-7bed2000       Deferred        libtasn1.so.3
ELF     7bed2000-7bf00000       Deferred        libcrypt.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf12000-7bf82000       Deferred        libgnutls.so.13
ELF     7bf82000-7bfb3000       Deferred        libcups.so.2
ELF     7bfcc000-7bffe000       Deferred        uxtheme<elf>
  \-PE  7bfd0000-7bffe000       \               uxtheme
ELF     7c231000-7c236000       Deferred        libxfixes.so.3
ELF     7c236000-7c23f000       Deferred        libxcursor.so.1
ELF     7c23f000-7c245000       Deferred        libxrandr.so.2
ELF     7c245000-7c24d000       Deferred        libxrender.so.1
ELF     7c24d000-7c250000       Deferred        libxinerama.so.1
ELF     7e152000-7e39a000       Deferred        savage_dri.so
ELF     7e39a000-7e3a3000       Deferred        libdrm.so.2
ELF     7e3a3000-7e403000       Deferred        libgl.so.1
ELF     7e403000-7e408000       Deferred        libxdmcp.so.6
ELF     7e408000-7e4f9000       Deferred        libx11.so.6
ELF     7e4f9000-7e507000       Deferred        libxext.so.6
ELF     7e507000-7e50c000       Deferred        libxxf86vm.so.1
ELF     7e50c000-7e524000       Deferred        libice.so.6
ELF     7e524000-7e52d000       Deferred        libsm.so.6
ELF     7e52d000-7e5bb000       Deferred        winex11<elf>
  \-PE  7e540000-7e5bb000       \               winex11
ELF     7e63d000-7e65d000       Deferred        libexpat.so.1
ELF     7e65d000-7e688000       Deferred        libfontconfig.so.1
ELF     7e688000-7e69c000       Deferred        libz.so.1
ELF     7e69c000-7e707000       Deferred        libfreetype.so.6
ELF     7e707000-7e73a000       Deferred        winspool<elf>
  \-PE  7e710000-7e73a000       \               winspool
ELF     7e73a000-7e7da000       Deferred        comdlg32<elf>
  \-PE  7e740000-7e7da000       \               comdlg32
ELF     7e7da000-7e896000       Deferred        comctl32<elf>
  \-PE  7e7e0000-7e896000       \               comctl32
ELF     7e896000-7e8a9000       Deferred        libresolv.so.2
ELF     7e8a9000-7e8c7000       Deferred        iphlpapi<elf>
  \-PE  7e8b0000-7e8c7000       \               iphlpapi
ELF     7e8c7000-7e91c000       Deferred        rpcrt4<elf>
  \-PE  7e8d0000-7e91c000       \               rpcrt4
ELF     7e91c000-7e9b6000       Deferred        ole32<elf>
  \-PE  7e930000-7e9b6000       \               ole32
ELF     7e9b6000-7ea0f000       Deferred        shlwapi<elf>
  \-PE  7e9d0000-7ea0f000       \               shlwapi
ELF     7ea0f000-7eb04000       Deferred        shell32<elf>
  \-PE  7ea20000-7eb04000       \               shell32
ELF     7eb04000-7eb18000       Deferred        lz32<elf>
  \-PE  7eb10000-7eb18000       \               lz32
ELF     7eb18000-7eb31000       Deferred        version<elf>
  \-PE  7eb20000-7eb31000       \               version
ELF     7eb31000-7eb4e000       Deferred        imm32<elf>
  \-PE  7eb40000-7eb4e000       \               imm32
ELF     7eb4e000-7eb94000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb94000       \               advapi32
ELF     7eb94000-7eba0000       Deferred        libgcc_s.so.1
ELF     7ec96000-7ed53000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed53000       \               gdi32
ELF     7ed53000-7ee8f000       Export          user32<elf>
  \-PE  7ed70000-7ee8f000       \               user32
ELF     7efa1000-7efac000       Deferred        libnss_files.so.2
ELF     7efac000-7efb6000       Deferred        libnss_nis.so.2
ELF     7efb6000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff4000-7eff7000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d39000-b7d3d000       Deferred        libdl.so.2
ELF     b7d3d000-b7e7e000       Deferred        libc.so.6
ELF     b7e7e000-b7e95000       Deferred        libpthread.so.0
ELF     b7ea1000-b7fb2000       Export          libwine.so.1
ELF     b7fb4000-b7fcf000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b 
        0000000d    0
        0000000c    0
00000008 (D) H:\.wine\drive_c\spel\starcraft\StarCraft.exe
        00000019   15
        00000018    2
        00000011    0
        0000000f   15
        0000000a    1
        00000009    0 <==


---

### Post by DiceMan on 2007-08-15
Hmm... bump.

---

