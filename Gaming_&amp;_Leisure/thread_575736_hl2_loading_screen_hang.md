---
title: "hl2 loading screen hang"
date: 2007-10-14
forum: Gaming &amp; Leisure
---

### Post by navaburo on 2007-10-14
I followed the various Half Life 2 on Wine guides, however I ran into a problem I did not find mentioned on any guide. Steam works fine (well, the mouse is kind-of glitchy), but when I load HL2 it gets as far as the Loading... screen where it hangs with the following output:

```
cmerck@alderan:~/.wine/drive_c/Program Files/Steam$ cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 220 -dxlevel 70
dir: C:\Program Files\Steam\ *.mix
dir: C:\Program Files\Steam\ *.asi
dir: C:\Program Files\Steam\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
wine: Unhandled page fault on write access to 0x00000022 at address 0xe068a37 (thread 0041), starting debugger...
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x0e068a37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0e068a37 ESP:0034e574 EBP:00000004 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:07ed0070 ECX:0e07a9d0 EDX:0e0767b8
 ESI:00000700 EDI:0e07a9d0
Stack dump:
0x0034e574:  00000090 0e07a9d0 00000004 0121fc6c
0x0034e584:  0e069d32 07ed0070 00000730 20f50074
0x0034e594:  0e07a9d0 0121fc6c 0e06a084 20f50074
0x0034e5a4:  00000730 20f50074 0e07a9f0 0e07a9d0
0x0034e5b4:  0e0686ca 20f50074 ffffffff 0034e60c
0x0034e5c4:  00000008 0034ff08 00000000 003d70bb
Backtrace:
=>1 0x0e068a37 in datacache (+0x8a37) (0x00000004)
  2 0x00000000 (0x00000000)
0x0e068a37: addw        $0xffff,0x22(%eax)
Modules:
Module  Address                 Debug info      Name (147 modules)
PE        3d0000-  3fe000       Deferred        launcher
PE        400000-  41c000       Deferred        hl2
PE       1160000- 1194000       Deferred        tier0
PE       11a0000- 11c0000       Deferred        vstdlib
PE       dad0000- db06000       Deferred        filesystem_steam
PE       db10000- db25000       Deferred        valve_avi
PE       dd90000- de68000       Deferred        datamodel
PE       df80000- dfa9000       Deferred        dmserializers
PE       dfb0000- e055000       Deferred        materialsystem
PE       e060000- e081000       Export          datacache
PE       e1a0000- e264000       Deferred        vguimatsurface
PE       e270000- e2d7000       Deferred        vgui2
PE       e2e0000- e30f000       Deferred        soundemittersystem
PE       e310000- e320000       Deferred        steam_api
PE       e650000- e678000       Deferred        stdshader_dbg
PE       e680000- e6b3000       Deferred        stdshader_dx6
PE       e6c0000- e6e7000       Deferred        stdshader_dx7
PE       e6f0000- e72f000       Deferred        stdshader_dx8
PE       e730000- e73e000       Deferred        unicode
PE       f2e0000- f49d000       Deferred        steamclient
PE       f4a0000- f4dd000       Deferred        vstdlib_s
PE       f4e0000- f51f000       Deferred        tier0_s
PE       f650000- f67e000       Deferred        nattypeprobe
PE       f680000- f91c000       Deferred        p2pcore
PE       f920000- fa7a000       Deferred        p2pvoice
PE       fb90000- fd4d000       Deferred        gameui
PE      10000000-10031000       Deferred        gameoverlayrenderer
PE      1d6f0000-1d700000       Deferred        vaudio_miles
PE      1d700000-1d764000       Deferred        mss32
PE      1edc0000-1eed4000       Deferred        serverbrowser
PE      20000000-2064b000       Deferred        engine
PE      21100000-211ad000       Deferred        mss32_s
PE      22000000-2263d000       Deferred        server
PE      24000000-24388000       Deferred        client
PE      26000000-26126000       Deferred        vphysics
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a09f000       Deferred        shaderapidx9
PE      2c000000-2c2d8000       Deferred        studiorender
PE      30000000-30320000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
PE      628c0000-628d9000       Deferred        parsifal
ELF     7af83000-7afcd000       Deferred        dbghelp<elf>
  \-PE  7af90000-7afcd000       \               dbghelp
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b9f6000-7ba02000       Deferred        libgcc_s.so.1
ELF     7bb12000-7bb5c000       Deferred        dsound<elf>
  \-PE  7bb20000-7bb5c000       \               dsound
ELF     7bb5c000-7bb70000       Deferred        winejoystick<elf>
  \-PE  7bb60000-7bb70000       \               winejoystick
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c95b000-7c980000       Deferred        netapi32<elf>
  \-PE  7c960000-7c980000       \               netapi32
ELF     7ce9a000-7cec1000       Deferred        secur32<elf>
  \-PE  7cea0000-7cec1000       \               secur32
ELF     7cec1000-7ced6000       Deferred        psapi<elf>
  \-PE  7ced0000-7ced6000       \               psapi
ELF     7d15d000-7d23d000       Deferred        wined3d<elf>
  \-PE  7d170000-7d23d000       \               wined3d
ELF     7d23d000-7d26c000       Deferred        d3d9<elf>
  \-PE  7d250000-7d26c000       \               d3d9
ELF     7d26c000-7d28c000       Deferred        mpr<elf>
  \-PE  7d270000-7d28c000       \               mpr
ELF     7d28c000-7d2d6000       Deferred        wininet<elf>
  \-PE  7d2a0000-7d2d6000       \               wininet
ELF     7d2d6000-7d374000       Deferred        oleaut32<elf>
  \-PE  7d2f0000-7d374000       \               oleaut32
ELF     7d374000-7d389000       Deferred        midimap<elf>
  \-PE  7d380000-7d389000       \               midimap
ELF     7d389000-7d3a1000       Deferred        msacm32<elf>
  \-PE  7d390000-7d3a1000       \               msacm32
ELF     7d3a1000-7d3db000       Deferred        wineoss<elf>
  \-PE  7d3b0000-7d3db000       \               wineoss
ELF     7d3db000-7d402000       Deferred        msvfw32<elf>
  \-PE  7d3e0000-7d402000       \               msvfw32
ELF     7d402000-7d490000       Deferred        winmm<elf>
  \-PE  7d410000-7d490000       \               winmm
ELF     7d490000-7d4b6000       Deferred        msacm32<elf>
  \-PE  7d4a0000-7d4b6000       \               msacm32
ELF     7d4b6000-7d4f0000       Deferred        avifil32<elf>
  \-PE  7d4c0000-7d4f0000       \               avifil32
ELF     7d625000-7d67e000       Deferred        rpcrt4<elf>
  \-PE  7d630000-7d67e000       \               rpcrt4
ELF     7d67e000-7d71f000       Deferred        ole32<elf>
  \-PE  7d690000-7d71f000       \               ole32
ELF     7d75c000-7d78e000       Deferred        uxtheme<elf>
  \-PE  7d760000-7d78e000       \               uxtheme
ELF     7d78e000-7d84c000       Deferred        comctl32<elf>
  \-PE  7d7a0000-7d84c000       \               comctl32
ELF     7d84c000-7d94f000       Deferred        shell32<elf>
  \-PE  7d860000-7d94f000       \               shell32
ELF     7d94f000-7d9a8000       Deferred        shlwapi<elf>
  \-PE  7d960000-7d9a8000       \               shlwapi
ELF     7d9a8000-7d9bc000       Deferred        mswsock<elf>
  \-PE  7d9b0000-7d9bc000       \               mswsock
ELF     7d9bc000-7d9d0000       Deferred        lz32<elf>
  \-PE  7d9c0000-7d9d0000       \               lz32
ELF     7d9d0000-7d9ea000       Deferred        version<elf>
  \-PE  7d9e0000-7d9ea000       \               version
ELF     7d9ea000-7d9fd000       Deferred        libresolv.so.2
ELF     7da0d000-7da2b000       Deferred        iphlpapi<elf>
  \-PE  7da10000-7da2b000       \               iphlpapi
ELF     7da2b000-7da58000       Deferred        ws2_32<elf>
  \-PE  7da30000-7da58000       \               ws2_32
ELF     7dca4000-7dcbe000       Deferred        wsock32<elf>
  \-PE  7dcb0000-7dcbe000       \               wsock32
ELF     7dcbe000-7dcc7000       Deferred        libxcursor.so.1
ELF     7dcc7000-7dce4000       Deferred        imm32<elf>
  \-PE  7dcd0000-7dce4000       \               imm32
ELF     7dce4000-7dcea000       Deferred        libxrandr.so.2
ELF     7dcea000-7dcf2000       Deferred        libxrender.so.1
ELF     7e028000-7e02a000       Deferred        libnvidia-tls.so.1
ELF     7e02a000-7e8b0000       Deferred        libglcore.so.1
ELF     7e8b0000-7e93c000       Deferred        libgl.so.1
ELF     7e93c000-7e941000       Deferred        libxdmcp.so.6
ELF     7e941000-7e944000       Deferred        libxau.so.6
ELF     7e944000-7ea35000       Deferred        libx11.so.6
ELF     7ea35000-7ea43000       Deferred        libxext.so.6
ELF     7ea43000-7ea48000       Deferred        libxxf86vm.so.1
ELF     7ea48000-7ea60000       Deferred        libice.so.6
ELF     7ea60000-7ea69000       Deferred        libsm.so.6
ELF     7ea69000-7ea6e000       Deferred        libxfixes.so.3
ELF     7ea79000-7eb04000       Deferred        winex11<elf>
  \-PE  7ea90000-7eb04000       \               winex11
ELF     7eb90000-7ebb0000       Deferred        libexpat.so.1
ELF     7ebb0000-7ebdb000       Deferred        libfontconfig.so.1
ELF     7ebdb000-7ebef000       Deferred        libz.so.1
ELF     7ebef000-7ec5a000       Deferred        libfreetype.so.6
ELF     7ec5a000-7eca3000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca3000       \               advapi32
ELF     7eca3000-7ed3e000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed3e000       \               gdi32
ELF     7ed3e000-7ee7c000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7c000       \               user32
ELF     7ee7c000-7ee87000       Deferred        libnss_files.so.2
ELF     7ee87000-7ee9e000       Deferred        libnsl.so.1
ELF     7ee9e000-7eea7000       Deferred        libnss_compat.so.2
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb9000-b7cbd000       Deferred        libdl.so.2
ELF     b7cbd000-b7dfe000       Deferred        libc.so.6
ELF     b7dff000-b7e16000       Deferred        libpthread.so.0
ELF     b7e26000-b7f3a000       Deferred        libwine.so.1
ELF     b7f3c000-b7f57000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000040 (D) C:\Program Files\Steam\steamapps\navaburohl2\half-life 2\hl2.exe
        00000026    0
        00000047    0
        00000046    0
        00000045    0
        00000043    0
        00000042    2
        00000041    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000025    1
        00000044    1
        0000003e    0
        0000003d    0
        0000003c    1
        0000003b    0
        0000003a    1
        00000039    0
        00000037    0
        00000036    0
        00000035    1
        00000034    0
        00000033    1
        00000032    0
        00000031    1
        00000030    0
        0000002f    1
        0000002e    0
        0000002d    1
        0000002c    0
        0000002b    1
        0000002a    0
        00000029    1
        00000028    0
        00000027    1
        00000023    0
        00000022    0
        00000020    0
        0000001f    1
        0000001d    0
        0000001b    0
        0000001a    0
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0

```

changing rendering settings or audio settings seem to have no effect...

Any ideas on how to get around this problem?

Thanks in advance.

---

### Post by navaburo on 2007-10-29
I also tried both the steam (purchased) version of portal and the unleashed release and had the following error on this Gusty box and It did not work, with a similar error to the above (pasted below).

Note that I did NOT any error on another Feisty machine (also has nVidia) with the unleashed release.

```

fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:ViewObject_SetAdvise (0x12439aa8)->(1 00000002 0x79c520)
fixme:shdocvw:PersistStreamInit_InitNew (0x12439aa8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x12439aa8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x12439aa8)->(ffffffff)
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x136a78) : stub
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x136a78) : Only 1 render targets are supported.
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1ba9b8) : pBox=0x33e1e0 stub
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12439aa8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x12439aa8)
fixme:shdocvw:OleObject_Close (0x12439aa8)->(1)
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
wine: Unhandled page fault on read access to 0x00000009 at address 0x9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000009 in 32-bit code (0x00000009).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000009 ESP:0033e6f4 EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000009 EBX:0eb35e80 ECX:08f902c0 EDX:08f90b00
 ESI:0eb35b50 EDI:00000000
Stack dump:
0x0033e6f4:  0eaa14a8 00000001 0000000a 0033e7c0
0x0033e704:  00400000 ffffffff ffffffff 0eb7ebe1
0x0033e714:  0000000f 100084be 00000003 0033e7c0
0x0033e724:  10008747 00110858 0033e764 1000873e
0x0033e734:  00110858 00341a40 10004f45 00000001
0x0033e744:  00531c05 00000002 00000000 00000000
Backtrace:
=>1 0x00000009 (0x00000000)
0x00000009: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (134 modules)
PE        340000-  37b000       Deferred        tier0
PE        380000-  3d5000       Deferred        vstdlib
PE        400000-  41a000       Deferred        hl2
PE       b390000- b3c1000       Deferred        gameoverlayrenderer
PE       bf40000- bf89000       Deferred        filesystem_steam
PE       d150000- d733000       Deferred        engine
PE       d740000- d754000       Deferred        steam_api
PE       dde0000- de00000       Deferred        inputsystem
PE       de00000- df21000       Deferred        materialsystem
PE       e330000- e36c000       Deferred        datacache
PE       e370000- e75c000       Deferred        studiorender
PE       e980000- ea70000       Deferred        vphysics
PE       ea70000- ea8f000       Deferred        valve_avi
PE       ea90000- eb58000       Deferred        vguimatsurface
PE       eb60000- ebbd000       Deferred        vgui2
PE       ebc0000- ed48000       Deferred        shaderapidx9
PE       ffa0000- ffb4000       Deferred        xinput1_3
PE       ffc0000- fff1000       Deferred        stdshader_dbg
PE      10000000-1002d000       Deferred        launcher
PE      10a80000-10ac6000       Deferred        stdshader_dx6
PE      10ad0000-10b05000       Deferred        stdshader_dx7
PE      10b10000-10b74000       Deferred        stdshader_dx8
PE      10b80000-10b95000       Deferred        unicode
PE      11510000-11533000       Deferred        soundemittersystem
PE      11540000-11557000       Deferred        scenefilecache
PE      11560000-115d2000       Deferred        vstdlib_s
PE      11b40000-12079000       Deferred        client
PE      12440000-12bda000       Deferred        server
PE      18000000-18033000       Deferred        binkw32
PE      18040000-181fd000       Deferred        steamclient
PE      18200000-1823f000       Deferred        tier0_s
PE      24b50000-24d19000       Deferred        gameui
PE      30000000-300a1000       Deferred        steam
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bd07000-7bd41000       Deferred        shdocvw<elf>
  \-PE  7bd10000-7bd41000       \               shdocvw
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c97e000-7c9c8000       Deferred        dsound<elf>
  \-PE  7c990000-7c9c8000       \               dsound
ELF     7c9c8000-7c9dc000       Deferred        winejoystick<elf>
  \-PE  7c9d0000-7c9dc000       \               winejoystick
ELF     7c9dc000-7c9f0000       Deferred        lz32<elf>
  \-PE  7c9e0000-7c9f0000       \               lz32
ELF     7c9f0000-7ca0a000       Deferred        version<elf>
  \-PE  7ca00000-7ca0a000       \               version
ELF     7ca0a000-7ca6e000       Deferred        setupapi<elf>
  \-PE  7ca20000-7ca6e000       \               setupapi
ELF     7ca6e000-7cb4e000       Deferred        wined3d<elf>
  \-PE  7ca80000-7cb4e000       \               wined3d
ELF     7cb4e000-7cb7d000       Deferred        d3d9<elf>
  \-PE  7cb60000-7cb7d000       \               d3d9
ELF     7cb7d000-7cc1b000       Deferred        oleaut32<elf>
  \-PE  7cb90000-7cc1b000       \               oleaut32
ELF     7cc1b000-7cc42000       Deferred        msvfw32<elf>
  \-PE  7cc20000-7cc42000       \               msvfw32
ELF     7cc42000-7cc7c000       Deferred        avifil32<elf>
  \-PE  7cc50000-7cc7c000       \               avifil32
ELF     7cc7c000-7cc91000       Deferred        midimap<elf>
  \-PE  7cc80000-7cc91000       \               midimap
ELF     7cc91000-7ccb8000       Deferred        msacm32<elf>
  \-PE  7cca0000-7ccb8000       \               msacm32
ELF     7ccb8000-7ccd0000       Deferred        msacm32<elf>
  \-PE  7ccc0000-7ccd0000       \               msacm32
ELF     7ccd0000-7cd0a000       Deferred        wineoss<elf>
  \-PE  7cce0000-7cd0a000       \               wineoss
ELF     7cd0a000-7cd2a000       Deferred        mpr<elf>
  \-PE  7cd10000-7cd2a000       \               mpr
ELF     7cd2a000-7cd74000       Deferred        wininet<elf>
  \-PE  7cd40000-7cd74000       \               wininet
ELF     7cd74000-7ce02000       Deferred        winmm<elf>
  \-PE  7cd80000-7ce02000       \               winmm
ELF     7d2a7000-7d2d9000       Deferred        uxtheme<elf>
  \-PE  7d2b0000-7d2d9000       \               uxtheme
ELF     7d2d9000-7d332000       Deferred        rpcrt4<elf>
  \-PE  7d2f0000-7d332000       \               rpcrt4
ELF     7d332000-7d3d3000       Deferred        ole32<elf>
  \-PE  7d340000-7d3d3000       \               ole32
ELF     7d3d3000-7d491000       Deferred        comctl32<elf>
  \-PE  7d3e0000-7d491000       \               comctl32
ELF     7d491000-7d4ea000       Deferred        shlwapi<elf>
  \-PE  7d4a0000-7d4ea000       \               shlwapi
ELF     7d4ea000-7d5ed000       Deferred        shell32<elf>
  \-PE  7d500000-7d5ed000       \               shell32
ELF     7d5ed000-7d600000       Deferred        libresolv.so.2
ELF     7d600000-7d61e000       Deferred        iphlpapi<elf>
  \-PE  7d610000-7d61e000       \               iphlpapi
ELF     7d8d0000-7d8db000       Deferred        libgcc_s.so.1
ELF     7d8e9000-7d916000       Deferred        ws2_32<elf>
  \-PE  7d8f0000-7d916000       \               ws2_32
ELF     7d916000-7d930000       Deferred        wsock32<elf>
  \-PE  7d920000-7d930000       \               wsock32
ELF     7d932000-7d937000       Deferred        libxfixes.so.3
ELF     7d937000-7d940000       Deferred        libxcursor.so.1
ELF     7d940000-7d95d000       Deferred        imm32<elf>
  \-PE  7d950000-7d95d000       \               imm32
ELF     7d95d000-7d963000       Deferred        libxrandr.so.2
ELF     7d963000-7d96b000       Deferred        libxrender.so.1
ELF     7d9ca000-7d9df000       Deferred        psapi<elf>
  \-PE  7d9d0000-7d9df000       \               psapi
ELF     7df08000-7df0a000       Deferred        libnvidia-tls.so.1
ELF     7df0a000-7e8a2000       Deferred        libglcore.so.1
ELF     7e8a2000-7e938000       Deferred        libgl.so.1
ELF     7e938000-7e93d000       Deferred        libxdmcp.so.6
ELF     7e93d000-7ea2e000       Deferred        libx11.so.6
ELF     7ea2e000-7ea3c000       Deferred        libxext.so.6
ELF     7ea3c000-7ea41000       Deferred        libxxf86vm.so.1
ELF     7ea41000-7ea59000       Deferred        libice.so.6
ELF     7ea59000-7ea61000       Deferred        libsm.so.6
ELF     7ea61000-7eaec000       Deferred        winex11<elf>
  \-PE  7ea70000-7eaec000       \               winex11
ELF     7eb8c000-7ebac000       Deferred        libexpat.so.1
ELF     7ebac000-7ebd7000       Deferred        libfontconfig.so.1
ELF     7ebd7000-7ebec000       Deferred        libz.so.1
ELF     7ebec000-7ec5c000       Deferred        libfreetype.so.6
ELF     7ec5c000-7eca5000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca5000       \               advapi32
ELF     7eca5000-7ed40000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed40000       \               gdi32
ELF     7ed40000-7ee7e000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7e000       \               user32
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff2000       Deferred        libxau.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d22000-b7d26000       Deferred        libdl.so.2
ELF     b7d26000-b7e70000       Deferred        libc.so.6
ELF     b7e71000-b7e89000       Deferred        libpthread.so.0
ELF     b7e9a000-b7fae000       Deferred        libwine.so.1
ELF     b7fb0000-b7fcc000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        00000010    0
        0000000f    0
00000008 (D) Z:\home\cmerck\usr\unl-prtl\portal\hl2.exe
        00000016    2
        00000015    0
        00000014    0
        00000013    0
        00000012    0
        0000000d    0
        0000000c    0
        0000000b    0
        0000000a    0
        00000009    0 <==


```

---

### Post by Sockerdrickan on 2007-10-29
winedebug=-all have you tried putting this in when you start?

---

### Post by aoanla on 2007-10-29
> **navaburo said:**
> I followed the various Half Life 2 on Wine guides, however I ran into a problem I did not find mentioned on any guide. Steam works fine (well, the mouse is kind-of glitchy), but when I load HL2 it gets as far as the Loading... screen where it hangs with the following output

What's your hardware and software configuration (specifically graphics card hardware and driver version)?

---

### Post by n3utrino on 2007-10-29
hi all.

i get the same error. i think its related to a new bug
[http://bugs.winehq.com/show_bug.cgi?id=9878](http://bugs.winehq.com/show_bug.cgi?id=9878)
have you tried to downgrade wine to 0.9.44?

i just found out and had no time to try it. please post your results

cheerio n3utrino


<edit> it says 
> I have this bug to but you need to set the detail for the model to low, if not
game will crash when joining a team.

maybe  it helps too
</edit>

---

### Post by navaburo on 2007-10-29
> have you tried to downgrade wine to 0.9.44?

I have tried 0.9.47 and 0.9.33 (which works on my friends machine with hl2).

> What's your hardware and software configuration (specifically graphics card hardware and driver version)? 

Core2Quad (using 32-bit OS)
Gusty 7.10 (after upgrading from Feisty)
Wine 0.9.47 and 0.9.33
VCard: EGA GeForce 7600GT
Driver: Latest from nVidia's website (also tried ubuntu's restricted driver).

Output of GLXINFO
```
cmerck@alderan:~/usr/unl-prtl/portal$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
cmerck@alderan:~/usr/unl-prtl/portal$ 

```

Thanks for helping me out!

---

### Post by snkmad on 2007-10-29
On winecfg, select hl2.exe and set it to win98 mode. Worked here for hl2 and hl2dm on wine 0.9.47.
Ive heard wine 0.9.48 should fix some troubles with steam/source games, but not all problems. Waiting for an updated binary....

---

### Post by n3utrino on 2007-10-29
nice. the 98 trick worked for me. :guitar:

i can even set all the graphics to high and it runs fine.

thanx

---

### Post by navaburo on 2007-10-29
Still no go.

I tried changing to win98 mode, but I still get errors, although they are different than before:

(I tried both 0.9.47 and 0.9.33, same errors):

```
wine: Unhandled page fault on read access to 0x00000009 at address 0x7b852266 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000009 in 32-bit code (0x7b852266).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b852266 ESP:0033e238 EBP:0033e2a0 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000001 EBX:7b8b0888 ECX:ffffffff EDX:00000009
 ESI:00000000 EDI:00000073
Stack dump:
0x0033e238:  00000073 7bc598e4 7ffdcc00 00110852
0x0033e248:  7ffdcc00 7bc8443c 7ffdc000 7ffdcc00
0x0033e258:  0033e338 00000000 00000000 00000001
0x0033e268:  00000001 0033e27c 128a7528 001107b8
0x0033e278:  7ee283a4 0033e29c 7ee283a4 7bc32761
0x0033e288:  00000000 0033e394 128a7528 7b8b0888
Backtrace:
=>1 0x7b852266 __wine_emulate_instruction+0x66() in kernel32 (0x0033e2a0)
  2 0x7b853594 INSTR_vectored_handler+0x64() in kernel32 (0x0033e2c0)
  3 0x7bc39693 in ntdll (+0x29693) (0x0033e330)
  4 0x7bc39b29 __regs_RtlRaiseException+0x29() in ntdll (0x0033e3a0)
  5 0x7bc62a1c in ntdll (+0x52a1c) (0x0033e3c0)
  6 0xdeadbabe (0x00000000)
0x7b852266 __wine_emulate_instruction+0x66 in kernel32: movzbl  0x0(%esi,%edx,1),%eax
Modules:
Module  Address                 Debug info      Name (134 modules)
PE        340000-  37b000       Deferred        tier0
PE        380000-  3d5000       Deferred        vstdlib
PE        400000-  41a000       Deferred        hl2
PE       b590000- b5c1000       Deferred        gameoverlayrenderer
PE       c240000- c289000       Deferred        filesystem_steam
PE       d450000- da33000       Deferred        engine
PE       da40000- da54000       Deferred        steam_api
PE       e1e0000- e200000       Deferred        inputsystem
PE       e200000- e321000       Deferred        materialsystem
PE       e730000- e76c000       Deferred        datacache
PE       e770000- eb5c000       Deferred        studiorender
PE       ed80000- ee70000       Deferred        vphysics
PE       ee70000- ee8f000       Deferred        valve_avi
PE       ee90000- ef58000       Deferred        vguimatsurface
PE       ef60000- efbd000       Deferred        vgui2
PE       efc0000- f148000       Deferred        shaderapidx9
PE       ffe0000- fff4000       Deferred        xinput1_3
PE      10000000-1002d000       Deferred        launcher
PE      10f40000-10f71000       Deferred        stdshader_dbg
PE      10f80000-10fc6000       Deferred        stdshader_dx6
PE      10fd0000-11005000       Deferred        stdshader_dx7
PE      11010000-11074000       Deferred        stdshader_dx8
PE      11080000-11095000       Deferred        unicode
PE      11a10000-11a33000       Deferred        soundemittersystem
PE      11a40000-11a57000       Deferred        scenefilecache
PE      11a60000-11ad2000       Deferred        vstdlib_s
PE      12040000-12579000       Deferred        client
PE      12940000-130da000       Deferred        server
PE      16500000-166bd000       Deferred        steamclient
PE      166c0000-166ff000       Deferred        tier0_s
PE      16910000-16ad9000       Deferred        gameui
PE      18000000-18033000       Deferred        binkw32
PE      30000000-300a1000       Deferred        steam
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bb79000-7bbb3000       Deferred        shdocvw<elf>
  \-PE  7bb80000-7bbb3000       \               shdocvw
ELF     7bc00000-7bca0000       Export          ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bdda000-7bdef000       Deferred        psapi<elf>
  \-PE  7bde0000-7bdef000       \               psapi
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ca57000-7ca62000       Deferred        libgcc_s.so.1
ELF     7cb73000-7cbbc000       Deferred        dsound<elf>
  \-PE  7cb80000-7cbbc000       \               dsound
ELF     7cbbc000-7cbd0000       Deferred        winejoystick<elf>
  \-PE  7cbc0000-7cbd0000       \               winejoystick
ELF     7cbd0000-7cbe4000       Deferred        lz32<elf>
  \-PE  7cbe0000-7cbe4000       \               lz32
ELF     7cbe4000-7cbfe000       Deferred        version<elf>
  \-PE  7cbf0000-7cbfe000       \               version
ELF     7cbfe000-7cc62000       Deferred        setupapi<elf>
  \-PE  7cc10000-7cc62000       \               setupapi
ELF     7cc62000-7cd43000       Deferred        wined3d<elf>
  \-PE  7cc80000-7cd43000       \               wined3d
ELF     7cd43000-7cd72000       Deferred        d3d9<elf>
  \-PE  7cd50000-7cd72000       \               d3d9
ELF     7cd72000-7ce10000       Deferred        oleaut32<elf>
  \-PE  7cd80000-7ce10000       \               oleaut32
ELF     7ce10000-7ce37000       Deferred        msvfw32<elf>
  \-PE  7ce20000-7ce37000       \               msvfw32
ELF     7ce37000-7ce71000       Deferred        avifil32<elf>
  \-PE  7ce40000-7ce71000       \               avifil32
ELF     7ce71000-7ce86000       Deferred        midimap<elf>
  \-PE  7ce80000-7ce86000       \               midimap
ELF     7ce86000-7cead000       Deferred        msacm32<elf>
  \-PE  7ce90000-7cead000       \               msacm32
ELF     7cead000-7cec5000       Deferred        msacm32<elf>
  \-PE  7ceb0000-7cec5000       \               msacm32
ELF     7cec5000-7cf01000       Deferred        wineoss<elf>
  \-PE  7ced0000-7cf01000       \               wineoss
ELF     7cf01000-7cf21000       Deferred        mpr<elf>
  \-PE  7cf10000-7cf21000       \               mpr
ELF     7cf21000-7cf6b000       Deferred        wininet<elf>
  \-PE  7cf30000-7cf6b000       \               wininet
ELF     7cf6b000-7cff9000       Deferred        winmm<elf>
  \-PE  7cf80000-7cff9000       \               winmm
ELF     7d4a7000-7d4d9000       Deferred        uxtheme<elf>
  \-PE  7d4b0000-7d4d9000       \               uxtheme
ELF     7d4d9000-7d532000       Deferred        rpcrt4<elf>
  \-PE  7d4f0000-7d532000       \               rpcrt4
ELF     7d532000-7d5d3000       Deferred        ole32<elf>
  \-PE  7d540000-7d5d3000       \               ole32
ELF     7d5d3000-7d691000       Deferred        comctl32<elf>
  \-PE  7d5e0000-7d691000       \               comctl32
ELF     7d691000-7d6ea000       Deferred        shlwapi<elf>
  \-PE  7d6a0000-7d6ea000       \               shlwapi
ELF     7d6ea000-7d7ed000       Deferred        shell32<elf>
  \-PE  7d700000-7d7ed000       \               shell32
ELF     7d7ed000-7d800000       Deferred        libresolv.so.2
ELF     7d800000-7d81e000       Deferred        iphlpapi<elf>
  \-PE  7d810000-7d81e000       \               iphlpapi
ELF     7dae8000-7db15000       Deferred        ws2_32<elf>
  \-PE  7daf0000-7db15000       \               ws2_32
ELF     7db15000-7db2f000       Deferred        wsock32<elf>
  \-PE  7db20000-7db2f000       \               wsock32
ELF     7db31000-7db36000       Deferred        libxfixes.so.3
ELF     7db36000-7db3f000       Deferred        libxcursor.so.1
ELF     7db3f000-7db5c000       Deferred        imm32<elf>
  \-PE  7db50000-7db5c000       \               imm32
ELF     7db5c000-7db62000       Deferred        libxrandr.so.2
ELF     7db62000-7db6a000       Deferred        libxrender.so.1
ELF     7df08000-7df0a000       Deferred        libnvidia-tls.so.1
ELF     7df0a000-7e8a2000       Deferred        libglcore.so.1
ELF     7e8a2000-7e938000       Deferred        libgl.so.1
ELF     7e938000-7e93d000       Deferred        libxdmcp.so.6
ELF     7e93d000-7e940000       Deferred        libxau.so.6
ELF     7e940000-7ea31000       Deferred        libx11.so.6
ELF     7ea31000-7ea3f000       Deferred        libxext.so.6
ELF     7ea3f000-7ea44000       Deferred        libxxf86vm.so.1
ELF     7ea44000-7ea5c000       Deferred        libice.so.6
ELF     7ea5c000-7ea64000       Deferred        libsm.so.6
ELF     7ea64000-7eaf0000       Deferred        winex11<elf>
  \-PE  7ea70000-7eaf0000       \               winex11
ELF     7eb8b000-7ebab000       Deferred        libexpat.so.1
ELF     7ebab000-7ebd6000       Deferred        libfontconfig.so.1
ELF     7ebd6000-7ebeb000       Deferred        libz.so.1
ELF     7ebeb000-7ec5b000       Deferred        libfreetype.so.6
ELF     7ec5b000-7eca4000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca4000       \               advapi32
ELF     7eca4000-7ed3f000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed3f000       \               gdi32
ELF     7ed3f000-7ee7d000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7d000       \               user32
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ce1000-b7ce5000       Deferred        libdl.so.2
ELF     b7ce5000-b7e2f000       Deferred        libc.so.6
ELF     b7e30000-b7e48000       Deferred        libpthread.so.0
ELF     b7e5a000-b7f6e000       Deferred        libwine.so.1
ELF     b7f70000-b7f8c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        00000010    0
        0000000f    0
00000008 (D) Z:\home\cmerck\usr\unl-prtl\portal\hl2.exe
        0000001b    2
        0000001a    0
        00000019    0
        00000018    0
        00000017    0
        00000012   15
        0000000d    0
        0000000c    0
        0000000b    0
        0000000a    0
        00000009    0 <==

```


Then I tried deleting the registry and reconfiguring, but I got a still different error:
```
wine: Unhandled page fault on read access to 0xffffffff at address 0x110036 (thread 0021), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x00110036).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00110036 ESP:0033fc7c EBP:0033fcc8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0399092f EBX:117a79f4 ECX:03990a28 EDX:00010081
 ESI:117a7a1c EDI:00000001
Stack dump:
0x0033fc7c:  115aa919 117a7a1c 11529bda ef5cdd78
0x0033fc8c:  0e4cf7bc 00000001 115ff755 5000c96a
0x0033fc9c:  00000000 00000000 11380000 0e4cf7bc
0x0033fcac:  0e4ce380 0033fc98 0033f7f4 0033fd20
0x0033fcbc:  11602f10 41400382 00000000 0033fcf0
0x0033fccc:  115ff7d3 00000000 00000000 00000001
Backtrace:
=>1 0x00110036 (0x0033fcc8)
  2 0x115ff7d3 in client (+0x27f7d3) (0x0033fcf0)
  3 0x115fe856 in client (+0x27e856) (0x0033fd30)
  4 0x115fe8c0 in client (+0x27e8c0) (0x0033fd58)
  5 0x7bc4392d in ntdll (+0x3392d) (0x0033fde8)
  6 0x7bc43d6f in ntdll (+0x33d6f) (0x0033fe08)
  7 0x7b87228f ExitProcess+0x1f() in kernel32 (0x0033fe28)
  8 0x00401dd0 in hl2 (+0x1dd0) (0x0033fe6c)
  9 0x0040200f in hl2 (+0x200f) (0x0033ff08)
  10 0x7b874dfe in kernel32 (+0x54dfe) (0x0033ffe8)
  11 0xb7e159d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00110036: ljmp        0x0000340c
Modules:
Module  Address                 Debug info      Name (98 modules)
PE        340000-  37b000       Deferred        tier0
PE        380000-  3d5000       Deferred        vstdlib
PE        3e0000-  3f4000       Deferred        steam_api
PE        400000-  41a000       Export          hl2
PE       c7a0000- cd83000       Deferred        engine
PE      10000000-1002d000       Deferred        launcher
PE      103c0000-103d5000       Deferred        unicode
PE      10d50000-10d73000       Deferred        soundemittersystem
PE      10d80000-10d97000       Deferred        scenefilecache
PE      11380000-118b9000       Export          client
PE      11c80000-1241a000       Deferred        server
PE      17840000-17a09000       Deferred        gameui
PE      18000000-18033000       Deferred        binkw32
PE      30000000-300a1000       Deferred        steam
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Export          ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ca9a000-7caa5000       Deferred        libgcc_s.so.1
ELF     7cab7000-7cb00000       Deferred        dsound<elf>
  \-PE  7cac0000-7cb00000       \               dsound
ELF     7cb00000-7cb14000       Deferred        winejoystick<elf>
  \-PE  7cb10000-7cb14000       \               winejoystick
ELF     7cd55000-7cdb5000       Deferred        winedos<elf>
  \-PE  7cd60000-7cdb5000       \               winedos
ELF     7cdb5000-7cdca000       Deferred        midimap<elf>
  \-PE  7cdc0000-7cdca000       \               midimap
ELF     7cdca000-7cdf1000       Deferred        msacm32<elf>
  \-PE  7cdd0000-7cdf1000       \               msacm32
ELF     7cdf1000-7ce09000       Deferred        msacm32<elf>
  \-PE  7ce00000-7ce09000       \               msacm32
ELF     7ce09000-7cecf000       Deferred        libasound.so.2
ELF     7cecf000-7cf05000       Deferred        winealsa<elf>
  \-PE  7cee0000-7cf05000       \               winealsa
ELF     7cf05000-7cf25000       Deferred        mpr<elf>
  \-PE  7cf10000-7cf25000       \               mpr
ELF     7cf25000-7cf6f000       Deferred        wininet<elf>
  \-PE  7cf30000-7cf6f000       \               wininet
ELF     7cf6f000-7cffd000       Deferred        winmm<elf>
  \-PE  7cf80000-7cffd000       \               winmm
ELF     7d4ab000-7d4dd000       Deferred        uxtheme<elf>
  \-PE  7d4b0000-7d4dd000       \               uxtheme
ELF     7d4dd000-7d536000       Deferred        rpcrt4<elf>
  \-PE  7d4f0000-7d536000       \               rpcrt4
ELF     7d536000-7d5d7000       Deferred        ole32<elf>
  \-PE  7d550000-7d5d7000       \               ole32
ELF     7d5d7000-7d695000       Deferred        comctl32<elf>
  \-PE  7d5e0000-7d695000       \               comctl32
ELF     7d695000-7d6ee000       Deferred        shlwapi<elf>
  \-PE  7d6a0000-7d6ee000       \               shlwapi
ELF     7d6ee000-7d7f1000       Deferred        shell32<elf>
  \-PE  7d700000-7d7f1000       \               shell32
ELF     7d7f1000-7d804000       Deferred        libresolv.so.2
ELF     7d804000-7d822000       Deferred        iphlpapi<elf>
  \-PE  7d810000-7d822000       \               iphlpapi
ELF     7daec000-7db19000       Deferred        ws2_32<elf>
  \-PE  7db00000-7db19000       \               ws2_32
ELF     7db19000-7db33000       Deferred        wsock32<elf>
  \-PE  7db20000-7db33000       \               wsock32
ELF     7db35000-7db3a000       Deferred        libxfixes.so.3
ELF     7db3a000-7db43000       Deferred        libxcursor.so.1
ELF     7db43000-7db60000       Deferred        imm32<elf>
  \-PE  7db50000-7db60000       \               imm32
ELF     7db60000-7db66000       Deferred        libxrandr.so.2
ELF     7db66000-7db6e000       Deferred        libxrender.so.1
ELF     7df0c000-7df0e000       Deferred        libnvidia-tls.so.1
ELF     7df0e000-7e8a6000       Deferred        libglcore.so.1
ELF     7e8a6000-7e93c000       Deferred        libgl.so.1
ELF     7e93c000-7e941000       Deferred        libxdmcp.so.6
ELF     7e941000-7e944000       Deferred        libxau.so.6
ELF     7e944000-7ea35000       Deferred        libx11.so.6
ELF     7ea35000-7ea43000       Deferred        libxext.so.6
ELF     7ea43000-7ea48000       Deferred        libxxf86vm.so.1
ELF     7ea48000-7ea60000       Deferred        libice.so.6
ELF     7ea60000-7ea68000       Deferred        libsm.so.6
ELF     7ea68000-7eaf4000       Deferred        winex11<elf>
  \-PE  7ea80000-7eaf4000       \               winex11
ELF     7eb8b000-7ebab000       Deferred        libexpat.so.1
ELF     7ebab000-7ebd6000       Deferred        libfontconfig.so.1
ELF     7ebd6000-7ebeb000       Deferred        libz.so.1
ELF     7ebeb000-7ec5b000       Deferred        libfreetype.so.6
ELF     7ec5b000-7eca4000       Deferred        advapi32<elf>
  \-PE  7ec70000-7eca4000       \               advapi32
ELF     7eca4000-7ed3f000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed3f000       \               gdi32
ELF     7ed3f000-7ee7d000       Deferred        user32<elf>
  \-PE  7ed60000-7ee7d000       \               user32
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c95000-b7c99000       Deferred        libdl.so.2
ELF     b7c99000-b7de3000       Deferred        libc.so.6
ELF     b7de4000-b7dfc000       Deferred        libpthread.so.0
ELF     b7e0e000-b7f22000       Export          libwine.so.1
ELF     b7f24000-b7f40000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000026 
        00000028    0
        00000027    0
00000020 (D) Z:\home\cmerck\usr\unl-prtl\portal\hl2.exe
        00000030    2
        0000002f    0
        0000002e    0
        0000002d    0
        0000002c    0
        00000029   15
        00000025    0
        00000024    0
        00000023    0
        00000022    0
        00000021    0 <==

```

Well, back to neverball for now... :(

---

### Post by Jorenko on 2007-10-31
> **snkmad said:**
> On winecfg, select hl2.exe and set it to win98 mode. Worked here for hl2 and hl2dm on wine 0.9.47.
Ive heard wine 0.9.48 should fix some troubles with steam/source games, but not all problems. Waiting for an updated binary....

Huzzah! I'm another happy user after trying this solution. I still had this problem on 0.9.48, and win98 mode fixes it. Thanks!

---

### Post by snkmad on 2007-11-01
Well, for me wine 0.9.48 works like a charm. Dont even need the win98 mode trick anymore.
But theres still the problem with Steam Friends. Cant send or receive messages.
Ive heard 0.9.38 works fine, maybe its a regression?

---

