---
title: "HL2:Deathmatch crashes when regular HL2 doesn't"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by SBFC on 2007-04-21
Hey everybody. Has any one had any problems playing HL2 Deathmatch? 

What bothers me is that I can play regular HL2 no problems. Even passed the game. However, when trying to play HL2 Deathmatch after a few minutes in the game it just craps out.

Get the following in the terminal:

```
C:\Program Files\Valve\Steam\SteamApps\morbidconcept\half-life 2 de    athmatch\hl2.exe
        00000049    0
        00000048    0
        00000023    0
        0000002a    0
        00000022   15
        0000003c    0
        0000001e    0
        0000001b   15
        00000047    0
        00000046    0
        00000044    0
        00000043    2
        00000042    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        0000002e    1
        00000045    1
        00000040    0
        0000003f    0
        0000003e    0
        0000003d    1
        0000003b    0
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
        00000030    0
        0000002f    1
        00000029    0
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

And sometimes this:

```
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d30b413).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d30b413 ESP:0034e5e8 EBP:00000002 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000570 EBX:00000000 ECX:26b361a0 EDX:0724dc80
 ESI:0d31ea18 EDI:00000090
Stack dump:
0x0034e5e8:  0d31ea18 00554b2c 0d30b442 26b30057
0x0034e5f8:  0d31ea18 00554b2c 0d31ea18 26b30058
0x0034e608:  0d30b7c5 26b30058 0d31ea18 26b30058
0x0034e618:  0d31ea3c 00000570 0d31ea18 0d3098ca

0x0034e628:  26b30001 ffffffff 00000000 00000009
0x0034e638:  0034ff08 0034e67c 1000753b 00000003
Backtrace:
=>1 0x0d30b413 in datacache (+0xb413) (0x00000002)
  2 0x00000000 (0x00000000)
0x0d30b413: movl        0x24(%ebx),%eax
Modules:
Module  Address                 Debug info      Name (226 modules)
PE        350000-  386000       Deferred        tier0
PE        390000-  3ae000       Deferred        vstdlib
PE        3e0000-  3f4000       Deferred        inputsystem
PE        400000-  41c000       Deferred        hl2
PE       ce40000- ce8d000       Deferred        filesystem_steam
PE       d0b0000- d1ae000       Deferred        datamodel
PE       d2c0000- d2fd000       Deferred        dmserializers
PE       d300000- d325000       Export          datacache
PE       d440000- d4f4000       Deferred        materialsystem
PE       d500000- d516000       Deferred        valve_avi
PE       d520000- d64d000       Deferred        vguimatsurface
PE       d650000- d6c5000       Deferred        vgui2
PE       d6d0000- dd48000       Deferred        engine
PE       dd50000- dd63000       Deferred        steam_api
PE       df90000- dfb9000       Deferred        stdshader_dbg
PE       dfc0000- dff5000       Deferred        stdshader_dx6
PE       e000000- e028000       Deferred        stdshader_dx7
PE       e030000- e073000       Deferred        stdshader_dx8
PE       e080000- e08f000       Deferred        unicode
PE       e700000- e736000       Deferred        soundemittersystem
PE       e740000- e75b000       Deferred        scenefilecache
PE       e870000- e9e9000       Deferred        steamclient
PE       e9f0000- ea69000       Deferred        vstdlib_s
PE       ea70000- eab0000       Deferred        tier0_s
PE       ebd0000- ee55000       Deferred        gameui
PE      10000000-10030000       Deferred        launcher
PE      1c870000-1c880000       Deferred        vaudio_miles
PE      1e280000-1e344000       Deferred        friendsui
PE      1e350000-1e41b000       Deferred        serverbrowser
PE      1edb0000-1edd7000       Deferred        vaudio_speex
PE      20000000-2031d000       Deferred        steam
PE      21100000-21164000       Deferred        mss32
PE      22000000-2285f000       Deferred        server
PE      24000000-244f0000       Deferred        client
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
ELF     728b1000-728fa000       Deferred        dbghelp<elf>
  \-PE  728c0000-728fa000       \               dbghelp
ELF     76c8c000-76cbd000       Deferred        libcups.so.2
ELF     76cbd000-76d5d000       Deferred        comdlg32<elf>
  \-PE  76cd0000-76d5d000       \               comdlg32
ELF     76d5d000-76d90000       Deferred        winspool<elf>
  \-PE  76d70000-76d90000       \               winspool
ELF     76d90000-76df7000       Deferred        msvcrt<elf>
  \-PE  76da0000-76df7000       \               msvcrt
ELF     76df7000-76e6a000       Deferred        mshtml<elf>
  \-PE  76e00000-76e6a000       \               mshtml
ELF     798b0000-798f9000       Deferred        dsound<elf>
  \-PE  798c0000-798f9000       \               dsound
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7b931000-7b967000       Deferred        urlmon<elf>
  \-PE  7b940000-7b967000       \               urlmon
ELF     7bac6000-7bb00000       Deferred        shdocvw<elf>
  \-PE  7bad0000-7bb00000       \               shdocvw
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c600000-7c64f000       Deferred        crypt32<elf>
  \-PE  7c610000-7c64f000       \               crypt32
ELF     7c64f000-7c684000       Deferred        rsaenh<elf>
  \-PE  7c660000-7c684000       \               rsaenh
ELF     7c684000-7c699000       Deferred        psapi<elf>
  \-PE  7c690000-7c699000       \               psapi
ELF     7c80f000-7c823000       Deferred        winejoystick<elf>
  \-PE  7c820000-7c823000       \               winejoystick
ELF     7ca95000-7ca99000       Deferred        libgpg-error.so.0
ELF     7ca99000-7caea000       Deferred        libgcrypt.so.11
ELF     7caea000-7caff000       Deferred        libtasn1.so.3
ELF     7caff000-7cb6f000       Deferred        libgnutls.so.13
ELF     7cb6f000-7cb86000       Deferred        libsasl2.so.2
ELF     7cb86000-7cbb4000       Deferred        libcrypt.so.1
ELF     7cbb4000-7cbb8000       Deferred        libkrb5support.so.0
ELF     7cbb8000-7cbbb000       Deferred        libcom_err.so.2
ELF     7cbbb000-7cbe0000       Deferred        libk5crypto.so.3
ELF     7cbe0000-7cc5d000       Deferred        libkrb5.so.3
ELF     7cc5d000-7cc79000       Deferred        libgssapi_krb5.so.2
ELF     7cc79000-7cc86000       Deferred        liblber.so.2
ELF     7cc86000-7ccbc000       Deferred        libldap_r.so.2
ELF     7ccbc000-7cd9b000       Deferred        libnss_wins.so.2
ELF     7cd9b000-7cd9e000       Deferred        libnss_mdns4.so.2
ELF     7cd9e000-7cda4000       Deferred        libnss_dns.so.2
ELF     7cda4000-7cda7000       Deferred        libnss_mdns4_minimal.so.2
ELF     7cdaa000-7cdae000       Deferred        ibm850.so
ELF     7cdae000-7cdb2000       Deferred        utf-16.so
ELF     7cdb2000-7ce32000       Deferred        libglu.so.1
ELF     7ce32000-7ceef000       Deferred        wined3d<elf>
  \-PE  7ce40000-7ceef000       \               wined3d
ELF     7ceef000-7cf1a000       Deferred        d3d9<elf>
  \-PE  7cf00000-7cf1a000       \               d3d9
ELF     7cf1a000-7cf39000       Deferred        mpr<elf>
  \-PE  7cf20000-7cf39000       \               mpr
ELF     7cf39000-7cf81000       Deferred        wininet<elf>
  \-PE  7cf40000-7cf81000       \               wininet
ELF     7cf81000-7d01c000       Deferred        oleaut32<elf>
  \-PE  7cf90000-7d01c000       \               oleaut32
ELF     7d01c000-7d043000       Deferred        msvfw32<elf>
  \-PE  7d020000-7d043000       \               msvfw32
ELF     7d043000-7d07d000       Deferred        avifil32<elf>
  \-PE  7d050000-7d07d000       \               avifil32
ELF     7d07d000-7d092000       Deferred        midimap<elf>
  \-PE  7d080000-7d092000       \               midimap
ELF     7d092000-7d0b8000       Deferred        msacm32<elf>
  \-PE  7d0a0000-7d0b8000       \               msacm32
ELF     7d0b8000-7d0d0000       Deferred        msacm32<elf>
  \-PE  7d0c0000-7d0d0000       \               msacm32
ELF     7d0d0000-7d10c000       Deferred        wineoss<elf>
  \-PE  7d0e0000-7d10c000       \               wineoss
ELF     7d10c000-7d19b000       Deferred        winmm<elf>
  \-PE  7d120000-7d19b000       \               winmm
ELF     7d389000-7d3bb000       Deferred        uxtheme<elf>
  \-PE  7d390000-7d3bb000       \               uxtheme
ELF     7d3bb000-7d3cf000       Deferred        mswsock<elf>
  \-PE  7d3c0000-7d3cf000       \               mswsock
ELF     7d3cf000-7d3e8000       Deferred        version<elf>
  \-PE  7d3e0000-7d3e8000       \               version
ELF     7d3e8000-7d4a4000       Deferred        comctl32<elf>
  \-PE  7d3f0000-7d4a4000       \               comctl32
ELF     7d4a4000-7d4fc000       Deferred        shlwapi<elf>
  \-PE  7d4b0000-7d4fc000       \               shlwapi
ELF     7d4fc000-7d5f7000       Deferred        shell32<elf>
  \-PE  7d510000-7d5f7000       \               shell32
ELF     7d5f7000-7d64c000       Deferred        rpcrt4<elf>
  \-PE  7d600000-7d64c000       \               rpcrt4
ELF     7d64c000-7d6e9000       Deferred        ole32<elf>
  \-PE  7d660000-7d6e9000       \               ole32
ELF     7d6e9000-7d6fc000       Deferred        libresolv.so.2
ELF     7d6fc000-7d71a000       Deferred        iphlpapi<elf>
  \-PE  7d700000-7d71a000       \               iphlpapi
ELF     7d71a000-7d747000       Deferred        ws2_32<elf>
  \-PE  7d720000-7d747000       \               ws2_32
ELF     7d993000-7d9a7000       Deferred        lz32<elf>
  \-PE  7d9a0000-7d9a7000       \               lz32
ELF     7d9a7000-7d9c1000       Deferred        wsock32<elf>
  \-PE  7d9b0000-7d9c1000       \               wsock32
ELF     7d9c3000-7d9c8000       Deferred        libxfixes.so.3
ELF     7d9c8000-7d9d1000       Deferred        libxcursor.so.1
ELF     7d9d1000-7d9d9000       Deferred        libxrender.so.1
ELF     7d9d9000-7d9f6000       Deferred        imm32<elf>
  \-PE  7d9e0000-7d9f6000       \               imm32
ELF     7df1f000-7e7a5000       Deferred        libglcore.so.1
ELF     7e7a5000-7e831000       Deferred        libgl.so.1
ELF     7e831000-7e836000       Deferred        libxdmcp.so.6
ELF     7e836000-7e927000       Deferred        libx11.so.6
ELF     7e927000-7e935000       Deferred        libxext.so.6
ELF     7e935000-7e93a000       Deferred        libxxf86vm.so.1
ELF     7e93a000-7e952000       Deferred        libice.so.6
ELF     7e952000-7e95b000       Deferred        libsm.so.6
ELF     7e95b000-7e9e8000       Deferred        winex11<elf>
  \-PE  7e970000-7e9e8000       \               winex11
ELF     7ea86000-7eaa6000       Deferred        libexpat.so.1
ELF     7eaa6000-7ead1000       Deferred        libfontconfig.so.1
ELF     7ead1000-7eae5000       Deferred        libz.so.1
ELF     7eae5000-7eb50000       Deferred        libfreetype.so.6
ELF     7eb50000-7eb96000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb96000       \               advapi32
ELF     7eb96000-7eba2000       Deferred        libgcc_s.so.1
ELF     7ec8c000-7ed4a000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed4a000       \               gdi32
ELF     7ed4a000-7ee86000       Deferred        user32<elf>
  \-PE  7ed70000-7ee86000       \               user32
ELF     7ee86000-7ee91000       Deferred        libnss_files.so.2
ELF     7ee91000-7eea8000       Deferred        libnsl.so.1
ELF     7eea8000-7eeb1000       Deferred        libnss_compat.so.2
ELF     7eeb2000-7eeb4000       Deferred        libnvidia-tls.so.1
ELF     7efce000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca0000-b7ca3000       Deferred        libxau.so.6
ELF     b7cad000-b7cb1000       Deferred        libdl.so.2
ELF     b7cb1000-b7df2000       Deferred        libc.so.6
ELF     b7df3000-b7e0a000       Deferred        libpthread.so.0
ELF     b7e15000-b7f26000       Deferred        libwine.so.1
ELF     b7f28000-b7f43000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000041
```

Like I said though, HL2 runs perfectly fine. Deathmatch craps out.

On WineHQ I found a crash bug and there was a post that said setting Audo Driver to Emulation fixed it...but not in this case. But that was for reg HL2 and not Deathmatch I believe.

Messed with various video options in Wine, but it's a no go.

If anyone has had similar experiences and managed to fix it that'd be great if you posted the solution.

---

### Post by Azakus on 2007-05-18
I'm getting this too, but on every steam game. I've looked for answers, but can't find any. I was playing fine yesterday, but it just decided to start crashing now.

---

### Post by Azakus on 2007-05-18
I think I fixed it.
In Winecfg, is your audio on OSS with sample at 44100 and 16 bits? If not, put it there.

---

