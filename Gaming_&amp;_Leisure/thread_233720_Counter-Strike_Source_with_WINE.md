---
title: "Counter-Strike: Source with WINE"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by Stickittotheman on 2006-08-10
I finally got STEAM to work through WINE, and installed all my games. But now when I try to launch CSS, it gives me the little box saying "Preparing to launch Counter-Strike: Source...", and then it goes away, and nothing happens. According to someone on my friends list, it says that I'm "now playing Counter-Strike:Source", but theres not even a hl2.exe process in my task manager! I'm running xubuntu 6.06, btw. If it's any help, the console spits this out:

```
fixme:shdocvw:ViewObject_SetAdvise (0xd886e80)->(1 00000002 0x1164d88)
fixme:shdocvw:PersistStreamInit_InitNew (0xd886e80)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd886e80)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd886e80)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd886e80)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd886e80)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd886e80)
fixme:shdocvw:OleObject_Close (0xd886e80)->(1)
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
wine: Unhandled page fault on read access to 0x800000ec at address 0x7efb5950 (thread 0035), starting debugger...
WineDbg starting on pid 0xe
Unhandled exception: page fault on read access to 0x800000ec in 32-bit code (0x7efb5950).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7efb5950 ESP:0034e264 EBP:0034e28c EFLAGS:00010286(   - 00      -RISP1)
 EAX:80000000 EBX:7eff5288 ECX:65faf1f0 EDX:65f22392
 ESI:80000000 EDI:0df60154
Stack dump:
0x0034e264:  00000000 7eb3c4b4 0034e27c 7eb23122
0x0034e274:  00000000 0df60018 0034e334 65f24247
0x0034e284:  7eff5288 00000000 0034e2ec 7efb765c
0x0034e294:  0034e254 00000000 00110000 7efa9c27
0x0034e2a4:  001a4dc8 00000030 0034e33c 7efa9619
0x0034e2b4:  00110000 7eff5288 0034e2fc 00000008
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7efb5950 in ntdll (+0x25950) (0x7efb5950)
  2 0x7efb765c RtlAllocateHeap+0x1c in ntdll (0x7efb765c)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file ole32.dbg ("")
  3 0x65f01b9b in ole32 (+0x1b9b) (0x65f01b9b)
  4 0x65f2389d in ole32 (+0x2389d) (0x65f2389d)
  5 0x65f2376c in ole32 (+0x2376c) (0x65f2376c)
  6 0x65f235cd in ole32 (+0x235cd) (0x65f235cd)
  7 0x65f2354d in ole32 (+0x2354d) (0x65f2354d)
  8 0x65f018b4 in ole32 (+0x18b4) (0x65f018b4)
  9 0x65f63f00 in ole32 (+0x63f00) (0x65f63f00)
  10 0x2a02de00 in shaderapidx9 (+0x2de00) (0x2a02de00)
  11 0x00000000 (0x00000000)
  12 0x00000000 (0x00000000)
0x7efb5950: cmpl        $0x50414548,0xec(%eax)
Modules:
Module  Address                 Debug info      Name (114 modules)
PE      360000-37e000   Deferred        vstdlib
PE      380000-3b6000   Deferred        tier0
PE      3f0000-400000   Deferred        steam_api
PE      400000-41c000   Deferred        hl2
PE      ce40000-ce8d000 Deferred        filesystem_steam
PE      d0b0000-d1ae000 Deferred        datamodel
PE      d2c0000-d2fd000 Deferred        dmserializers
PE      d300000-d325000 Deferred        datacache
PE      d330000-d344000 Deferred        inputsystem
PE      d460000-d50f000 Deferred        materialsystem
PE      d510000-d526000 Deferred        valve_avi
PE      d530000-d5fe000 Deferred        vguimatsurface
PE      d600000-d675000 Deferred        vgui2
PE      d680000-dcb2000 Deferred        engine
PE      dee0000-df09000 Deferred        stdshader_dbg
PE      df10000-df45000 Deferred        stdshader_dx6
PE      10000000-10030000       Deferred        launcher
PE      20000000-2030a000       Deferred        steam
PE      26000000-26138000       Deferred        vphysics
PE      2a000000-2a0a6000       Export          shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      628c0000-628d9000       Deferred        parsifal
PE      65f00000-65fc2000       Export          ole32
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dd1a000-7dd2e000       Deferred        joystick<elf>
  \-PE  7dd20000-7dd2e000       \               joystick
ELF     7df50000-7df63000       Deferred        libresolv.so.2
ELF     7df63000-7df68000       Deferred        libnss_dns.so.2
ELF     7df70000-7dfe6000       Deferred        libglu.so.1
ELF     7dfe6000-7e08e000       Deferred        wined3d<elf>
  \-PE  7dff0000-7e08e000       \               wined3d
ELF     7e08e000-7e0b7000       Deferred        d3d9<elf>
  \-PE  7e0a0000-7e0b7000       \               d3d9
ELF     7e0b7000-7e0d6000       Deferred        mpr<elf>
  \-PE  7e0c0000-7e0d6000       \               mpr
ELF     7e0d6000-7e11d000       Deferred        wininet<elf>
  \-PE  7e0e0000-7e11d000       \               wininet
ELF     7e11d000-7e1ae000       Deferred        oleaut32<elf>
  \-PE  7e130000-7e1ae000       \               oleaut32
ELF     7e1ae000-7e1d5000       Deferred        msvfw32<elf>
  \-PE  7e1c0000-7e1d5000       \               msvfw32
ELF     7e1d5000-7e20e000       Deferred        avifil32<elf>
  \-PE  7e1e0000-7e20e000       \               avifil32
ELF     7e20e000-7e223000       Deferred        midimap<elf>
  \-PE  7e210000-7e223000       \               midimap
ELF     7e249000-7e261000       Deferred        msacm32<elf>
  \-PE  7e250000-7e261000       \               msacm32
ELF     7e261000-7e29d000       Deferred        wineoss<elf>
  \-PE  7e270000-7e29d000       \               wineoss
ELF     7e29d000-7e325000       Deferred        winmm<elf>
  \-PE  7e2b0000-7e325000       \               winmm
ELF     7e325000-7e374000       Deferred        rpcrt4<elf>
  \-PE  7e330000-7e374000       \               rpcrt4
ELF     7e52e000-7e55f000       Deferred        uxtheme<elf>
  \-PE  7e540000-7e55f000       \               uxtheme
ELF     7e55f000-7e573000       Deferred        mswsock<elf>
  \-PE  7e570000-7e573000       \               mswsock
ELF     7e573000-7e587000       Deferred        lz32<elf>
  \-PE  7e580000-7e587000       \               lz32
ELF     7e587000-7e5a0000       Deferred        version<elf>
  \-PE  7e590000-7e5a0000       \               version
ELF     7e5a0000-7e662000       Deferred        comctl32<elf>
  \-PE  7e5b0000-7e662000       \               comctl32
ELF     7e662000-7e6b8000       Deferred        shlwapi<elf>
  \-PE  7e670000-7e6b8000       \               shlwapi
ELF     7e6b8000-7e796000       Deferred        shell32<elf>
  \-PE  7e6d0000-7e796000       \               shell32
ELF     7e796000-7e7b5000       Deferred        iphlpapi<elf>
  \-PE  7e7a0000-7e7b5000       \               iphlpapi
ELF     7e7b5000-7e7df000       Deferred        ws2_32<elf>
  \-PE  7e7c0000-7e7df000       \               ws2_32
ELF     7e7df000-7e7f9000       Deferred        wsock32<elf>
  \-PE  7e7f0000-7e7f9000       \               wsock32
ELF     7e7fb000-7e7ff000       Deferred        libxfixes.so.3
ELF     7e7ff000-7e808000       Deferred        libxcursor.so.1
ELF     7e808000-7e810000       Deferred        libxrender.so.1
ELF     7e810000-7e82c000       Deferred        imm32<elf>
  \-PE  7e820000-7e82c000       \               imm32
ELF     7e82c000-7e833000       Deferred        libdrm.so.2
ELF     7e833000-7e899000       Deferred        libgl.so.1
ELF     7e899000-7e89c000       Deferred        libxau.so.6
ELF     7e89c000-7e982000       Deferred        libx11.so.6
ELF     7e982000-7e98f000       Deferred        libxext.so.6
ELF     7e98f000-7e994000       Deferred        libxxf86vm.so.1
ELF     7e994000-7e999000       Deferred        libxxf86dga.so.1
ELF     7e999000-7e9b1000       Deferred        libice.so.6
ELF     7e9b1000-7ea34000       Deferred        winex11<elf>
  \-PE  7e9c0000-7ea34000       \               winex11
ELF     7ea34000-7ea53000       Deferred        libexpat.so.1
ELF     7ea53000-7ea81000       Deferred        libfontconfig.so.1
ELF     7ea81000-7ea95000       Deferred        libz.so.1
ELF     7ea95000-7eafe000       Deferred        libfreetype.so.6
ELF     7eafe000-7eb41000       Deferred        advapi32<elf>
  \-PE  7eb10000-7eb41000       \               advapi32
ELF     7eb41000-7eb4b000       Deferred        libgcc_s.so.1
ELF     7ec20000-7ecd2000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecd2000       \               gdi32
ELF     7ecd2000-7ee04000       Deferred        user32<elf>
  \-PE  7ecf0000-7ee04000       \               user32
ELF     7ee04000-7ee0e000       Deferred        libnss_files.so.2
ELF     7ee0e000-7ee17000       Deferred        libnss_nis.so.2
ELF     7ee17000-7ee2c000       Deferred        libnsl.so.1
ELF     7ee5f000-7ef60000       Deferred        kernel32<elf>
  \-PE  7ee80000-7ef60000       \               kernel32
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Export          ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7cd0000-b7cd9000       Deferred        libnss_compat.so.2
ELF     b7cda000-b7cdd000       Deferred        libdl.so.2
ELF     b7cdd000-b7e0c000       Deferred        libc.so.6
ELF     b7e0c000-b7e1e000       Deferred        libpthread.so.0
ELF     b7e1f000-b7e27000       Deferred        libsm.so.6
ELF     b7e27000-b7f37000       Deferred        libwine.so.1
ELF     b7f3a000-b7f50000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e (D) C:\Program Files\Steam\steamapps\moltovcocktail88\counter-strike source\hl2.exe
        0000001a    0
        0000003e    0
        00000033    2
        00000035    0 <==
0000000a
        0000000b    0
00000008
        00000022    1
        0000003c    0
        00000034    0
        00000047    0
        00000046    0
        00000045    1
        00000044    0
        00000043    1
        00000042    0
        00000041    1
        00000040    0
        0000003f    1
        00000032    0
        00000030    0
        0000002f    1
        0000002e    0
        0000002d    0
        0000002c    0
        0000002b    1
        0000002a    0
        00000029    1
        00000028    0
        00000027    1
        00000026    0
        00000025    1
        00000024    0
        00000023    1
        0000001f    0
        0000001e    0
        0000001c    0
        0000001b    1
        00000019    0
        00000016    0
        00000015    0
        00000014    1
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000d    0
        0000000c    0
        00000009    0

```

Any ideas?

---

### Post by Stickittotheman on 2006-08-10
Can someone help me? I don't want to go back to windows D:

---

### Post by Brain Juice on 2006-08-11
1. Edit out your Steam Account name from your post.

2. Check your video drivers.

---

### Post by jc87 on 2006-08-17
Try the following :

Open steam » right click at CS:Source » properties » lauch options » introduce the following command: ```
mat_dxlevel 81
```

That will launch the game in directx 8.1 mode which has better support than directx 9 under Wine.

If that doesn´t work you can use Cedega to run the game (is paid) or dual-boot and go to Windows when you want to play CS:Source (is what i do).

---

