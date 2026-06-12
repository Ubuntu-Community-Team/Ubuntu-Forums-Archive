---
title: "counterstrike source+wine crash"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by sparkster666 on 2007-05-28
I had dods and css working great with win then it just stopped working. steam runs dods starts up as soon as I enter a map it freezes then im back at the desctop. I cant be positive if it is a sound issue or a motd issue I here a few sounds rt before it crashes. But I do not see the message of the day.

nvidia 7600gt with restricted drivers

here is the console output any help would be grate

```
johnl@johnl-desktop:~$ cd ~/.wine/drive_cjohnl@johnl-desktop:~/.wine/drive_c$ WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen     -width 1024 -height 768 -applaunch 300     -heapsize 512000 -nosound +map_background none "$@"
johnl@johnl-desktop:~/.wine/drive_c$ WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen     -width 1024 -height 768 -applaunch 300     -heapsize 512000 -nosound +map_background none "$@"
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
err:mshtml:set_profile SetCurrentProfile failed: 80520015
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
err:d3d_shader:shader_get_registers_used No texture bound to sampler 4
wine: Unhandled page fault on read access to 0x00000024 at address 0xd2eb413 (thread 0044), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d2eb413).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d2eb413 ESP:0034e5e8 EBP:00000001 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000010 EBX:00000000 ECX:25f339b0 EDX:0724e400
 ESI:0d2fea18 EDI:00000090
Stack dump:
0x0034e5e8:  0d2fea18 00553744 0d2eb442 25f30001
0x0034e5f8:  0d2fea18 00553744 0d2fea18 25f30002
0x0034e608:  0d2eb7c5 25f30002 0d2fea18 25f30002
0x0034e618:  0d2fea3c 00000010 0d2fea18 0d2e98ca
0x0034e628:  25f30001 ffffffff 00000000 00000009
0x0034e638:  0034ff08 0034e67c 1000753b 00000003
Backtrace:
=>1 0x0d2eb413 in datacache (+0xb413) (0x00000001)
  2 0x00000000 (0x00000000)
0x0d2eb413: movl        0x24(%ebx),%eax
Modules:
Module  Address                 Debug info      Name (214 modules)
PE      350000-386000   Deferred        tier0
PE      390000-3ae000   Deferred        vstdlib
PE      3b0000-3fd000   Deferred        filesystem_steam
PE      400000-41c000   Deferred        hl2
PE      d090000-d18e000 Deferred        datamodel
PE      d2a0000-d2dd000 Deferred        dmserializers
PE      d2e0000-d305000 Export          datacache
PE      d310000-d324000 Deferred        inputsystem
PE      d440000-d4f4000 Deferred        materialsystem
PE      d500000-d516000 Deferred        valve_avi
PE      d520000-d64d000 Deferred        vguimatsurface
PE      d650000-d6c5000 Deferred        vgui2
PE      d6d0000-dd48000 Deferred        engine
PE      dd50000-dd63000 Deferred        steam_api
PE      df90000-dfb9000 Deferred        stdshader_dbg
PE      dfc0000-dff5000 Deferred        stdshader_dx6
PE      e000000-e028000 Deferred        stdshader_dx7
PE      e030000-e073000 Deferred        stdshader_dx8
PE      e080000-e08f000 Deferred        unicode
PE      e700000-e736000 Deferred        soundemittersystem
PE      e740000-e75b000 Deferred        scenefilecache
PE      e760000-e8d9000 Deferred        steamclient
PE      e8e0000-e959000 Deferred        vstdlib_s
PE      e960000-e9a0000 Deferred        tier0_s
PE      eac0000-ed45000 Deferred        gameui
PE      ff30000-ff40000 Deferred        vaudio_miles
PE      10000000-10030000       Deferred        launcher
PE      1d6d0000-1d794000       Deferred        friendsui
PE      1d7a0000-1d86b000       Deferred        serverbrowser
PE      20000000-2031d000       Deferred        steam
PE      21100000-21164000       Deferred        mss32
PE      22000000-22608000       Deferred        server
PE      24000000-24511000       Deferred        client
PE      26000000-26138000       Deferred        vphysics
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a0a8000       Deferred        shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      60000000-60021000       Deferred        cserhelper
PE      600a0000-600d9000       Deferred        appcomps
PE      600e0000-600f0000       Deferred        appshell
PE      60120000-6012f000       Deferred        caps
PE      60130000-60140000       Deferred        chrome
PE      60150000-60159000       Deferred        cookie
PE      60160000-6018c000       Deferred        docshell
PE      60200000-6021e000       Deferred        embedcomponents
PE      60230000-60254000       Deferred        gkgfxwin
PE      60260000-6052d000       Deferred        gklayout
PE      60530000-60568000       Deferred        gkparser
PE      605a0000-605c5000       Deferred        gkwidget
PE      605d0000-605fe000       Deferred        i18n
PE      60610000-60635000       Deferred        imglib2
PE      606d0000-606dd000       Deferred        jar50
PE      606e0000-606ef000       Deferred        jsd3250
PE      60940000-609bb000       Deferred        necko
PE      609e0000-609ec000       Deferred        oji
PE      60a00000-60a18000       Deferred        palmsync
PE      60a20000-60a27000       Deferred        perms
PE      60a30000-60a38000       Deferred        pipboot
PE      60a90000-60a9e000       Deferred        profile
PE      60aa0000-60aba000       Deferred        rdf
PE      60b30000-60b37000       Deferred        txmgr
PE      60b40000-60b4c000       Deferred        typeaheadfind
PE      60b50000-60c0b000       Deferred        uconv
PE      60c70000-60c7e000       Deferred        webbrwsr
PE      60cf0000-60d22000       Deferred        xpc3250
PE      60d30000-60d37000       Deferred        xpcom_compat_c
PE      60d70000-60d7c000       Deferred        xppref32
PE      60d80000-60d96000       Deferred        gkgfx
PE      60da0000-60e09000       Deferred        js3250
PE      60e10000-60e23000       Deferred        jsj3250
PE      60ec0000-60ed1000       Deferred        mozz
PE      60ee0000-60f14000       Deferred        msgbsutl
PE      60f60000-60f87000       Deferred        nspr4
PE      60f90000-60fe9000       Deferred        nss3
PE      60ff0000-6102a000       Deferred        nssckbi
PE      61030000-61037000       Deferred        palmsyncproxy
PE      61040000-61047000       Deferred        plc4
PE      61050000-61056000       Deferred        plds4
PE      61060000-61068000       Deferred        npnul32
PE      61070000-6108a000       Deferred        smime3
PE      61090000-610ea000       Deferred        softokn3
PE      610f0000-6110b000       Deferred        ssl3
PE      61110000-61116000       Deferred        xpcom
PE      61120000-61134000       Deferred        xpcom_compat
PE      61140000-611a5000       Deferred        xpcom_core
PE      611b0000-611b6000       Deferred        xpistub
PE      628c0000-628d9000       Deferred        parsifal
ELF     75603000-7564c000       Deferred        dbghelp<elf>
  \-PE  75610000-7564c000       \               dbghelp
ELF     77977000-779c8000       Deferred        libgcrypt.so.11
ELF     779c8000-779dd000       Deferred        libtasn1.so.3
ELF     779dd000-77a0b000       Deferred        libcrypt.so.1
ELF     77a0b000-77a7b000       Deferred        libgnutls.so.13
ELF     77a7b000-77aac000       Deferred        libcups.so.2
ELF     77aac000-77b4c000       Deferred        comdlg32<elf>
  \-PE  77ab0000-77b4c000       \               comdlg32
ELF     77b4c000-77b7f000       Deferred        winspool<elf>
  \-PE  77b50000-77b7f000       \               winspool
ELF     77b7f000-77be6000       Deferred        msvcrt<elf>
  \-PE  77b90000-77be6000       \               msvcrt
ELF     77be6000-77c58000       Deferred        mshtml<elf>
  \-PE  77bf0000-77c58000       \               mshtml
ELF     77c58000-77c8e000       Deferred        urlmon<elf>
  \-PE  77c60000-77c8e000       \               urlmon
ELF     7af52000-7af8c000       Deferred        shdocvw<elf>
  \-PE  7af60000-7af8c000       \               shdocvw
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7b92b000-7b92f000       Deferred        libgpg-error.so.0
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c62a000-7c679000       Deferred        crypt32<elf>
  \-PE  7c630000-7c679000       \               crypt32
ELF     7c679000-7c6ae000       Deferred        rsaenh<elf>
  \-PE  7c680000-7c6ae000       \               rsaenh
ELF     7cc86000-7cc9a000       Deferred        winejoystick<elf>
  \-PE  7cc90000-7cc9a000       \               winejoystick
ELF     7cebc000-7cec2000       Deferred        libnss_dns.so.2
ELF     7cece000-7cf4e000       Deferred        libglu.so.1
ELF     7cf4e000-7d008000       Deferred        wined3d<elf>
  \-PE  7cf60000-7d008000       \               wined3d
ELF     7d008000-7d033000       Deferred        d3d9<elf>
  \-PE  7d010000-7d033000       \               d3d9
ELF     7d033000-7d052000       Deferred        mpr<elf>
  \-PE  7d040000-7d052000       \               mpr
ELF     7d052000-7d09a000       Deferred        wininet<elf>
  \-PE  7d060000-7d09a000       \               wininet
ELF     7d09a000-7d135000       Deferred        oleaut32<elf>
  \-PE  7d0b0000-7d135000       \               oleaut32
ELF     7d135000-7d15c000       Deferred        msvfw32<elf>
  \-PE  7d140000-7d15c000       \               msvfw32
ELF     7d15c000-7d196000       Deferred        avifil32<elf>
  \-PE  7d160000-7d196000       \               avifil32
ELF     7d196000-7d1ab000       Deferred        midimap<elf>
  \-PE  7d1a0000-7d1ab000       \               midimap
ELF     7d1ab000-7d1d1000       Deferred        msacm32<elf>
  \-PE  7d1b0000-7d1d1000       \               msacm32
ELF     7d1d1000-7d1e9000       Deferred        msacm32<elf>
  \-PE  7d1e0000-7d1e9000       \               msacm32
ELF     7d1e9000-7d225000       Deferred        wineoss<elf>
  \-PE  7d1f0000-7d225000       \               wineoss
ELF     7d225000-7d2b4000       Deferred        winmm<elf>
  \-PE  7d230000-7d2b4000       \               winmm
ELF     7d442000-7d474000       Deferred        uxtheme<elf>
  \-PE  7d450000-7d474000       \               uxtheme
ELF     7d474000-7d488000       Deferred        mswsock<elf>
  \-PE  7d480000-7d488000       \               mswsock
ELF     7d488000-7d49c000       Deferred        lz32<elf>
  \-PE  7d490000-7d49c000       \               lz32
ELF     7d49c000-7d4b5000       Deferred        version<elf>
  \-PE  7d4a0000-7d4b5000       \               version
ELF     7d4b5000-7d571000       Deferred        comctl32<elf>
  \-PE  7d4c0000-7d571000       \               comctl32
ELF     7d571000-7d5ca000       Deferred        shlwapi<elf>
  \-PE  7d580000-7d5ca000       \               shlwapi
ELF     7d5ca000-7d6bf000       Deferred        shell32<elf>
  \-PE  7d5e0000-7d6bf000       \               shell32
ELF     7d6bf000-7d714000       Deferred        rpcrt4<elf>
  \-PE  7d6d0000-7d714000       \               rpcrt4
ELF     7d714000-7d7ae000       Deferred        ole32<elf>
  \-PE  7d720000-7d7ae000       \               ole32
ELF     7d7ae000-7d7c1000       Deferred        libresolv.so.2
ELF     7d7c1000-7d7df000       Deferred        iphlpapi<elf>
  \-PE  7d7d0000-7d7df000       \               iphlpapi
ELF     7d7df000-7d80c000       Deferred        ws2_32<elf>
  \-PE  7d7f0000-7d80c000       \               ws2_32
ELF     7d83b000-7d850000       Deferred        psapi<elf>
  \-PE  7d840000-7d850000       \               psapi
ELF     7daa2000-7daa5000       Deferred        libnss_mdns4.so.2
ELF     7daa5000-7daa8000       Deferred        libnss_mdns4_minimal.so.2
ELF     7dab0000-7daca000       Deferred        wsock32<elf>
  \-PE  7dac0000-7daca000       \               wsock32
ELF     7dacc000-7dad1000       Deferred        libxfixes.so.3
ELF     7dad1000-7dada000       Deferred        libxcursor.so.1
ELF     7dada000-7daf7000       Deferred        imm32<elf>
  \-PE  7dae0000-7daf7000       \               imm32
ELF     7daf7000-7dafd000       Deferred        libxrandr.so.2
ELF     7dafd000-7db05000       Deferred        libxrender.so.1
ELF     7db05000-7db08000       Deferred        libxinerama.so.1
ELF     7de35000-7de37000       Deferred        libnvidia-tls.so.1
ELF     7de37000-7e7a9000       Deferred        libglcore.so.1
ELF     7e7a9000-7e83d000       Deferred        libgl.so.1
ELF     7e83d000-7e842000       Deferred        libxdmcp.so.6
ELF     7e842000-7e933000       Deferred        libx11.so.6
ELF     7e933000-7e941000       Deferred        libxext.so.6
ELF     7e941000-7e946000       Deferred        libxxf86vm.so.1
ELF     7e946000-7e95e000       Deferred        libice.so.6
ELF     7e95e000-7e967000       Deferred        libsm.so.6
ELF     7e967000-7e9f5000       Deferred        winex11<elf>
  \-PE  7e980000-7e9f5000       \               winex11
ELF     7ea85000-7eaa5000       Deferred        libexpat.so.1
ELF     7eaa5000-7ead0000       Deferred        libfontconfig.so.1
ELF     7ead0000-7eae4000       Deferred        libz.so.1
ELF     7eae4000-7eb4f000       Deferred        libfreetype.so.6
ELF     7eb4f000-7eb95000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb95000       \               advapi32
ELF     7eb95000-7eba1000       Deferred        libgcc_s.so.1
ELF     7ec8b000-7ed48000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed48000       \               gdi32
ELF     7ed48000-7ee84000       Deferred        user32<elf>
  \-PE  7ed60000-7ee84000       \               user32
ELF     7ee84000-7ee8f000       Deferred        libnss_files.so.2
ELF     7ee8f000-7eea6000       Deferred        libnsl.so.1
ELF     7eea6000-7eeaf000       Deferred        libnss_compat.so.2
ELF     7eeb0000-7eeb3000       Deferred        libxau.so.6
ELF     7efcd000-7eff4000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d46000-b7d4a000       Deferred        libdl.so.2
ELF     b7d4a000-b7e8b000       Deferred        libc.so.6
ELF     b7e8c000-b7ea3000       Deferred        libpthread.so.0
ELF     b7eaf000-b7fc0000       Deferred        libwine.so.1
ELF     b7fc2000-b7fdd000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000043 (D) C:\Program Files\Steam\steamapps\mvp78@optonline.net\day of defeat source\hl2.exe
        00000030    0
        0000002f    0
        0000002a    0
        0000002c    0
        00000029    0
        0000003e    0
        00000022    0
        0000001b    0
        00000018    0
        00000046    0
        00000045    2
        00000044    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        0000002e    1
        00000047    1
        00000042    0
        00000041    0
        00000040    0
        0000003f    1
        0000003d    0
        0000003c    0
        0000003b    1
        0000003a    0
        00000039    1
        00000038    0
        00000037    1
        00000036    0
        00000035    1
        00000034    0
        00000033    1
        00000032    0
        00000031    1
        0000002b    0
        00000028    0
        00000027    0
        00000026    0
        00000025    0
        00000024    0
        00000020    0
        0000001f    0
        0000001d    0
        0000001c    1
        0000001a    0
        00000019    0
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

I have also tried this


These crashes happens cause of sound (yes...), so :

1) In winecfg :

Tick OSS (only)

Tick "Emulate"

use "Basic" "8000Hz" "8 Bit"

---

