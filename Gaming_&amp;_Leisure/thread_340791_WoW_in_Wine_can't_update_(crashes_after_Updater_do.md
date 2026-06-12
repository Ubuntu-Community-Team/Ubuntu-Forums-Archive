---
title: "WoW in Wine can't update (crashes after Updater download)"
date: 2007-01-17
forum: Gaming &amp; Leisure
---

### Post by spydirweb on 2007-01-17
whenever there's an update for WoW now wine crashes after the update downloader finishes.  When I try to run just the patch, this is the console output:

```

$ wine Patches/WoW-2.0.0-to-2.0.3-enUS-Win-patch/BNUpdate.exe 
fixme:powrprof:DllMain (0x7cf70000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf70000, 0, (nil)) not fully implemented
fixme:ole:OleCreate 
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
fixme:shdocvw:PersistStorage_InitNew (0x1bf0d8)->(0x4f6980)
fixme:shdocvw:WebBrowser_QueryInterface (0x1bf0d8)->({0000011e-0000-0000-c000-000000000046} 0x34f238) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x1bf0d8)->(L"My Host Name", (null))
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
wine: Unhandled page fault on read access to 0xa8bdc381 at address 0xa8bdc381 (thread 000b), starting debugger...
spydir@spydir:/spydir/wine/World of Warcraft$ Unhandled exception: page fault on read access to 0xa8bdc381 in 32-bit code (0xa8bdc381).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:a8bdc381 ESP:0034ec70 EBP:0034ec94 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0034f064 EBX:0034f064 ECX:7cd9f25b EDX:0034ecd4
 ESI:0034ecac EDI:0034ecd4
Stack dump:
0x0034ec70:  00381050 0034f064 003bf4b8 0034eca0
0x0034ec80:  0034ecb4 003810de 003bf4b8 0034eca0
0x0034ec90:  0034ece8 0034ecb8 00382467 0034ecac
0x0034eca0:  003bf4b8 019d90c4 019d90c4 0034f064
0x0034ecb0:  0034ecc4 00000000 0034eccc 00381110
0x0034ecc0:  01c8d628 0034ecd4 019d90b0 0034ecf4
Backtrace:
=>1 0xa8bdc381 (0x0034ec94)
  2 0x00382467 in xpcom_core (+0x2467) (0x0034ecb8)
  3 0x00381110 in xpcom_core (+0x1110) (0x0034eccc)
  4 0x01c80000 in docshell (+0x10000) (0x0034ecf4)
  5 0x01ca1fdb in webbrwsr (+0x1fdb) (0x0034ed14)
  6 0x7cd9f876 NSContainer_Create+0x626() in mshtml (0x0034f074)
  7 0x7cd7ecf4 HTMLDocument_Create+0x164() in mshtml (0x0034f0c4)
  8 0x7cd99000 in mshtml (+0x29000) (0x0034f0e4)
  9 0x7e9bcbc4 CoCreateInstance+0x1c4() in ole32 (0x0034f144)
  10 0x7ce2261c in shdocvw (+0x1261c) (0x0034f1e4)
  11 0x7ce22fbb navigate_url+0x23b() in shdocvw (0x0034f224)
  12 0x7ce2b779 in shdocvw (+0x1b779) (0x0034f264)
  13 0x004b4111 in installer (+0xb4111) (0x00000010)
  14 0x00000000 (0x00000000)
0xa8bdc381: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (135 modules)
PE      380000-3e1000   Export          xpcom_core
PE      3f0000-3f7000   Deferred        plc4
PE      400000-50e000   Export          installer
PE      1560000-1566000 Deferred        plds4
PE      1570000-159e000 Deferred        xpc3250
PE      15a0000-15f6000 Deferred        js3250
PE      1600000-1606000 Deferred        lockmodule
PE      1610000-1616000 Deferred        transmgr
PE      1620000-1637000 Deferred        gkgfx
PE      1640000-1654000 Deferred        xpcom_compat
PE      1770000-17a2000 Deferred        nssckbi
PE      17b0000-17ca000 Deferred        smime3
PE      17d0000-1825000 Deferred        nss3
PE      1830000-188a000 Deferred        softokn3
PE      1890000-18a0000 Deferred        mozz
PE      18a0000-18bb000 Deferred        ssl3
PE      18c0000-18c6000 Deferred        mozctlx
PE      18d0000-1903000 Deferred        mozctl
PE      1910000-1918000 Deferred        npnul32
PE      1920000-1996000 Deferred        necko
PE      19a0000-19ad000 Deferred        xppref32
PE      1ac0000-1aed000 Deferred        i18n
PE      1af0000-1b0e000 Deferred        embedcomponents
PE      1b10000-1b1f000 Deferred        caps
PE      1b20000-1b2e000 Deferred        profile
PE      1b30000-1b37000 Deferred        xpcom_compat_c
PE      1b40000-1b50000 Deferred        chrome
PE      1b50000-1b69000 Deferred        rdf
PE      1b70000-1ba4000 Deferred        gkparser
PE      1bb0000-1c6a000 Deferred        uconv
PE      1c70000-1c97000 Export          docshell
PE      1ca0000-1cae000 Export          webbrwsr
PE      1cb0000-1cd2000 Deferred        gkwidget
PE      1ce0000-1d03000 Deferred        gkgfxwin
PE      1d10000-1f59000 Deferred        gklayout
PE      1f60000-1f80000 Deferred        imglib2
PE      1f80000-1f88000 Deferred        pipboot
PE      10000000-10006000       Deferred        xpcom
PE      30000000-30027000       Deferred        nspr4
PE      55900000-55961000       Deferred        msvcp60
ELF     7b800000-7b91b000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c98f000-7c993000       Deferred        libgpg-error.so.0
ELF     7c993000-7c9e1000       Deferred        libgcrypt.so.11
ELF     7c9e1000-7c9f4000       Deferred        libtasn1.so.3
ELF     7c9f4000-7ca22000       Deferred        libcrypt.so.1
ELF     7ca37000-7caa6000       Deferred        libgnutls.so.13
ELF     7caa6000-7cad5000       Deferred        libcups.so.2
ELF     7cad5000-7cb07000       Deferred        winspool<elf>
  \-PE  7cae0000-7cb07000       \               winspool
ELF     7cb07000-7cba6000       Deferred        comdlg32<elf>
  \-PE  7cb10000-7cba6000       \               comdlg32
ELF     7ccb7000-7cd1b000       Deferred        msvcrt<elf>
  \-PE  7ccd0000-7cd1b000       \               msvcrt
ELF     7cd1b000-7cd47000       Deferred        ws2_32<elf>
  \-PE  7cd20000-7cd47000       \               ws2_32
ELF     7cd47000-7cd61000       Deferred        wsock32<elf>
  \-PE  7cd50000-7cd61000       \               wsock32
ELF     7cd61000-7cdd3000       Export          mshtml<elf>
  \-PE  7cd70000-7cdd3000       \               mshtml
ELF     7cdd3000-7ce06000       Deferred        urlmon<elf>
  \-PE  7cde0000-7ce06000       \               urlmon
ELF     7ce06000-7ce42000       Export          shdocvw<elf>
  \-PE  7ce10000-7ce42000       \               shdocvw
ELF     7cf53000-7cf67000       Deferred        lz32<elf>
  \-PE  7cf60000-7cf67000       \               lz32
ELF     7cf67000-7cf80000       Deferred        version<elf>
  \-PE  7cf70000-7cf80000       \               version
ELF     7cf80000-7cfc4000       Deferred        riched20<elf>
  \-PE  7cf90000-7cfc4000       \               riched20
ELF     7cffb000-7d02d000       Deferred        uxtheme<elf>
  \-PE  7d000000-7d02d000       \               uxtheme
ELF     7d2ca000-7d2cf000       Deferred        libxfixes.so.3
ELF     7d2cf000-7d2d8000       Deferred        libxcursor.so.1
ELF     7d2d8000-7d2e0000       Deferred        libxrender.so.1
ELF     7d2e0000-7d2fc000       Deferred        imm32<elf>
  \-PE  7d2f0000-7d2fc000       \               imm32
ELF     7d2fc000-7d31a000       Deferred        ximcp.so.2
ELF     7d31a000-7d31c000       Deferred        xlcutf8load.so.2
ELF     7d31c000-7d31f000       Deferred        libxinerama.so.1
ELF     7db04000-7e475000       Deferred        libglcore.so.1
ELF     7e475000-7e509000       Deferred        libgl.so.1
ELF     7e509000-7e50e000       Deferred        libxdmcp.so.6
ELF     7e50e000-7e5d7000       Deferred        libx11.so.6
ELF     7e5d7000-7e5e4000       Deferred        libxext.so.6
ELF     7e5e4000-7e5e9000       Deferred        libxxf86vm.so.1
ELF     7e5e9000-7e601000       Deferred        libice.so.6
ELF     7e601000-7e68e000       Deferred        winex11<elf>
  \-PE  7e610000-7e68e000       \               winex11
ELF     7e68e000-7e6ac000       Deferred        libexpat.so.1
ELF     7e6ac000-7e6db000       Deferred        libfontconfig.so.1
ELF     7e6db000-7e745000       Deferred        libfreetype.so.6
ELF     7e745000-7e7dc000       Deferred        oleaut32<elf>
  \-PE  7e760000-7e7dc000       \               oleaut32
ELF     7e7dc000-7e7fb000       Deferred        mpr<elf>
  \-PE  7e7e0000-7e7fb000       \               mpr
ELF     7e7fb000-7e842000       Deferred        wininet<elf>
  \-PE  7e810000-7e842000       \               wininet
ELF     7e842000-7e902000       Deferred        comctl32<elf>
  \-PE  7e850000-7e902000       \               comctl32
ELF     7e902000-7e915000       Deferred        libresolv.so.2
ELF     7e915000-7e933000       Deferred        iphlpapi<elf>
  \-PE  7e920000-7e933000       \               iphlpapi
ELF     7e933000-7e987000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e987000       \               rpcrt4
ELF     7e987000-7ea1f000       Export          ole32<elf>
  \-PE  7e9a0000-7ea1f000       \               ole32
ELF     7ea1f000-7ea77000       Deferred        shlwapi<elf>
  \-PE  7ea30000-7ea77000       \               shlwapi
ELF     7ea77000-7eb69000       Deferred        shell32<elf>
  \-PE  7ea90000-7eb69000       \               shell32
ELF     7eb69000-7eb74000       Deferred        libgcc_s.so.1
ELF     7ec53000-7ed09000       Deferred        gdi32<elf>
  \-PE  7ec70000-7ed09000       \               gdi32
ELF     7ed09000-7ee41000       Deferred        user32<elf>
  \-PE  7ed20000-7ee41000       \               user32
ELF     7ee41000-7ee87000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee87000       \               advapi32
ELF     7ee87000-7ee9d000       Deferred        libnsl.so.1
ELF     7ee9d000-7eea6000       Deferred        libnss_compat.so.2
ELF     7eea7000-7eebb000       Deferred        libz.so.1
ELF     7efc5000-7efeb000       Deferred        libm.so.6
ELF     7efec000-7eff5000       Deferred        libsm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7cd1000-b7cd3000       Deferred        libnvidia-tls.so.1
ELF     b7cd3000-b7cdd000       Deferred        libnss_nis.so.2
ELF     b7cde000-b7ce2000       Deferred        libdl.so.2
ELF     b7ce2000-b7e16000       Deferred        libc.so.6
ELF     b7e17000-b7e2a000       Deferred        libpthread.so.0
ELF     b7e2b000-b7e2e000       Deferred        libxau.so.6
ELF     b7e3f000-b7f50000       Deferred        libwine.so.1
ELF     b7f52000-b7f6d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) C:\windows\temp\Blizzard Installer Bootstrap - 0000092c\Installer.exe
        00000011    0
        00000010    0
        0000000f    0
        0000000b    0 <==

```

Is this a known issue?  I tried searching around but I can't figure out the cause, or really find specific things in the crash report to use when searching.

---

### Post by Ferrat on 2007-01-17
what version of wine are you running?

---

### Post by spydirweb on 2007-01-20
I keep it updated to the winehq ubuntu repository, so right now .29 but it was .28 when I had the problem.  Haven't tried it since updating earlier today.

---

### Post by Ferrat on 2007-01-20
Hmm I'm running .29 and had no problems at all 

[COLOR="Red"]wine: Unhandled page fault on read access to 0xa8bdc381 at address 0xa8bdc381 (thread 000b), starting debugger...[/COLOR]

what windows version are you "using" ?
have you installed Mozilla ActiveX?
Have you tried restaring it from the files that wow backsup for these kind of errors? don't remember the namn but check appdb there you got lots of help.

---

### Post by NICU28 on 2007-01-22
I've heard of people having problems like this when there are patches for WoW.  Most patches are available for download from mirrors (instead of using Blizzard's updater).  I would suggest downloading the patches somewhere else and just running (for example)
```
wine WoW-2.0.3.6299-to-2.0.5.6320-enUS-patch.exe
```
I have two computers with WoW installed on each and I just transfer the patch files from one computer to the other and haven't run into any problems yet.

---

### Post by spydirweb on 2007-01-23
I am running the command "wine WoW-<version to version>-patch.exe"  The problem seems to be wine is failing running the patch.  It runs the downloader fine, I get my updates quick, etc etc.  The problem comes up when the downloader tries to load the actual patch.exe, which also when run by itself crashes.  For instance, the patch today came out, it downloaded fine, and here I am.  Patch cannot install.  when I run "wine WoW-2.0.5.6320-to-2.0.6.6337-enUS-patch.exe" it fails with the output:

```

$ wine WoW-2.0.5.6320-to-2.0.6.6337-enUS-patch.exe 
fixme:powrprof:DllMain (0x7cf70000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cf70000, 0, (nil)) not fully implemented
fixme:ole:OleCreate 
        {8856f961-340a-11d0-a96b-00c04fd705a2}
        {00000112-0000-0000-c000-000000000046} semi-stub!
fixme:shdocvw:PersistStorage_InitNew (0x1bf098)->(0x4f6980)
fixme:shdocvw:WebBrowser_QueryInterface (0x1bf098)->({0000011e-0000-0000-c000-000000000046} 0x34f238) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x1bf098)->(L"My Host Name", (null))
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
wine: Unhandled page fault on read access to 0xa8bdc381 at address 0xa8bdc381 (thread 000b), starting debugger...
Unhandled exception: page fault on read access to 0xa8bdc381 in 32-bit code (0xa8bdc381).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:a8bdc381 ESP:0034ec70 EBP:0034ec94 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0034f064 EBX:0034f064 ECX:7cd9325b EDX:0034ecd4
 ESI:0034ecac EDI:0034ecd4
Stack dump:
0x0034ec70:  00381050 0034f064 003bf4b8 0034eca0
0x0034ec80:  0034ecb4 003810de 003bf4b8 0034eca0
0x0034ec90:  0034ece8 0034ecb8 00382467 0034ecac
0x0034eca0:  003bf4b8 016d8f2c 016d8f2c 0034f064
0x0034ecb0:  0034ecc4 00000000 0034eccc 00381110
0x0034ecc0:  0198d628 0034ecd4 016d8f18 0034ecf4
Backtrace:
=>1 0xa8bdc381 (0x0034ec94)
spydir@spydir:/spydir/wine/World of Warcraft$   2 0x00382467 in xpcom_core (+0x2467) (0x0034ecb8)
  3 0x00381110 in xpcom_core (+0x1110) (0x0034eccc)
  4 0x01980000 in docshell (+0x10000) (0x0034ecf4)
  5 0x019a1fdb in webbrwsr (+0x1fdb) (0x0034ed14)
  6 0x7cd93876 NSContainer_Create+0x626() in mshtml (0x0034f074)
  7 0x7cd72cf4 HTMLDocument_Create+0x164() in mshtml (0x0034f0c4)
  8 0x7cd8d000 in mshtml (+0x2d000) (0x0034f0e4)
  9 0x7e9bbda4 CoCreateInstance+0x1c4() in ole32 (0x0034f144)
  10 0x7ce1661c in shdocvw (+0x1661c) (0x0034f1e4)
  11 0x7ce16fbb navigate_url+0x23b() in shdocvw (0x0034f224)
  12 0x7ce1f779 in shdocvw (+0x1f779) (0x0034f264)
  13 0x004b4111 in installer (+0xb4111) (0x00000010)
  14 0x00000000 (0x00000000)
0xa8bdc381: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (135 modules)
PE      380000-3e1000   Export          xpcom_core
PE      3f0000-3f7000   Deferred        plc4
PE      400000-50e000   Export          installer
PE      1360000-1366000 Deferred        plds4
PE      1370000-139e000 Deferred        xpc3250
PE      13a0000-13f6000 Deferred        js3250
PE      1400000-1406000 Deferred        lockmodule
PE      1410000-1416000 Deferred        transmgr
PE      1420000-1437000 Deferred        gkgfx
PE      1440000-1454000 Deferred        xpcom_compat
PE      1460000-1492000 Deferred        nssckbi
PE      14b0000-14ca000 Deferred        smime3
PE      14d0000-1525000 Deferred        nss3
PE      1530000-158a000 Deferred        softokn3
PE      1590000-15a0000 Deferred        mozz
PE      15a0000-15bb000 Deferred        ssl3
PE      15c0000-15c6000 Deferred        mozctlx
PE      15d0000-1603000 Deferred        mozctl
PE      1610000-1618000 Deferred        npnul32
PE      1620000-1696000 Deferred        necko
PE      16a0000-16ad000 Deferred        xppref32
PE      17c0000-17ed000 Deferred        i18n
PE      17f0000-180e000 Deferred        embedcomponents
PE      1810000-181f000 Deferred        caps
PE      1820000-182e000 Deferred        profile
PE      1830000-1837000 Deferred        xpcom_compat_c
PE      1840000-1850000 Deferred        chrome
PE      1850000-1869000 Deferred        rdf
PE      1870000-18a4000 Deferred        gkparser
PE      18b0000-196a000 Deferred        uconv
PE      1970000-1997000 Export          docshell
PE      19a0000-19ae000 Export          webbrwsr
PE      19b0000-19d2000 Deferred        gkwidget
PE      19e0000-1a03000 Deferred        gkgfxwin
PE      1a10000-1c59000 Deferred        gklayout
PE      1c60000-1c80000 Deferred        imglib2
PE      1c80000-1c88000 Deferred        pipboot
PE      10000000-10006000       Deferred        xpcom
PE      30000000-30027000       Deferred        nspr4
PE      55900000-55961000       Deferred        msvcp60
ELF     7b800000-7b91c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c982000-7c986000       Deferred        libgpg-error.so.0
ELF     7c986000-7c9d4000       Deferred        libgcrypt.so.11
ELF     7c9d4000-7c9e7000       Deferred        libtasn1.so.3
ELF     7c9e7000-7ca15000       Deferred        libcrypt.so.1
ELF     7ca2a000-7ca99000       Deferred        libgnutls.so.13
ELF     7ca99000-7cac8000       Deferred        libcups.so.2
ELF     7cac8000-7cafa000       Deferred        winspool<elf>
  \-PE  7cad0000-7cafa000       \               winspool
ELF     7cafa000-7cb9a000       Deferred        comdlg32<elf>
  \-PE  7cb00000-7cb9a000       \               comdlg32
ELF     7ccab000-7cd0f000       Deferred        msvcrt<elf>
  \-PE  7ccc0000-7cd0f000       \               msvcrt
ELF     7cd0f000-7cd3b000       Deferred        ws2_32<elf>
  \-PE  7cd20000-7cd3b000       \               ws2_32
ELF     7cd3b000-7cd55000       Deferred        wsock32<elf>
  \-PE  7cd40000-7cd55000       \               wsock32
ELF     7cd55000-7cdc7000       Export          mshtml<elf>
  \-PE  7cd60000-7cdc7000       \               mshtml
ELF     7cdc7000-7cdfa000       Deferred        urlmon<elf>
  \-PE  7cdd0000-7cdfa000       \               urlmon
ELF     7cdfa000-7ce36000       Export          shdocvw<elf>
  \-PE  7ce00000-7ce36000       \               shdocvw
ELF     7cf47000-7cf5b000       Deferred        lz32<elf>
  \-PE  7cf50000-7cf5b000       \               lz32
ELF     7cf5b000-7cf74000       Deferred        version<elf>
  \-PE  7cf60000-7cf74000       \               version
ELF     7cf74000-7cfb8000       Deferred        riched20<elf>
  \-PE  7cf80000-7cfb8000       \               riched20
ELF     7cfef000-7d021000       Deferred        uxtheme<elf>
  \-PE  7d000000-7d021000       \               uxtheme
ELF     7d2c2000-7d2c7000       Deferred        libxfixes.so.3
ELF     7d2c7000-7d2d0000       Deferred        libxcursor.so.1
ELF     7d2d0000-7d2d8000       Deferred        libxrender.so.1
ELF     7d2d8000-7d2f4000       Deferred        imm32<elf>
  \-PE  7d2e0000-7d2f4000       \               imm32
ELF     7d2f4000-7d312000       Deferred        ximcp.so.2
ELF     7d312000-7d314000       Deferred        xlcutf8load.so.2
ELF     7d314000-7d317000       Deferred        libxinerama.so.1
ELF     7daf9000-7e46a000       Deferred        libglcore.so.1
ELF     7e46a000-7e4fe000       Deferred        libgl.so.1
ELF     7e4fe000-7e503000       Deferred        libxdmcp.so.6
ELF     7e503000-7e5cc000       Deferred        libx11.so.6
ELF     7e5cc000-7e5d9000       Deferred        libxext.so.6
ELF     7e5d9000-7e5de000       Deferred        libxxf86vm.so.1
ELF     7e5de000-7e5f6000       Deferred        libice.so.6
ELF     7e5f6000-7e5ff000       Deferred        libsm.so.6
ELF     7e5ff000-7e68c000       Deferred        winex11<elf>
  \-PE  7e610000-7e68c000       \               winex11
ELF     7e68c000-7e6aa000       Deferred        libexpat.so.1
ELF     7e6aa000-7e6d9000       Deferred        libfontconfig.so.1
ELF     7e6d9000-7e743000       Deferred        libfreetype.so.6
ELF     7e743000-7e7db000       Deferred        oleaut32<elf>
  \-PE  7e750000-7e7db000       \               oleaut32
ELF     7e7db000-7e7fa000       Deferred        mpr<elf>
  \-PE  7e7e0000-7e7fa000       \               mpr
ELF     7e7fa000-7e841000       Deferred        wininet<elf>
  \-PE  7e800000-7e841000       \               wininet
ELF     7e841000-7e901000       Deferred        comctl32<elf>
  \-PE  7e850000-7e901000       \               comctl32
ELF     7e901000-7e914000       Deferred        libresolv.so.2
ELF     7e914000-7e932000       Deferred        iphlpapi<elf>
  \-PE  7e920000-7e932000       \               iphlpapi
ELF     7e932000-7e986000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e986000       \               rpcrt4
ELF     7e986000-7ea1f000       Export          ole32<elf>
  \-PE  7e990000-7ea1f000       \               ole32
ELF     7ea1f000-7ea77000       Deferred        shlwapi<elf>
  \-PE  7ea30000-7ea77000       \               shlwapi
ELF     7ea77000-7eb69000       Deferred        shell32<elf>
  \-PE  7ea90000-7eb69000       \               shell32
ELF     7eb69000-7eb74000       Deferred        libgcc_s.so.1
ELF     7ec53000-7ed09000       Deferred        gdi32<elf>
  \-PE  7ec70000-7ed09000       \               gdi32
ELF     7ed09000-7ee41000       Deferred        user32<elf>
  \-PE  7ed20000-7ee41000       \               user32
ELF     7ee41000-7ee87000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee87000       \               advapi32
ELF     7ee87000-7ee9d000       Deferred        libnsl.so.1
ELF     7ee9d000-7eea6000       Deferred        libnss_compat.so.2
ELF     7eea7000-7eebb000       Deferred        libz.so.1
ELF     7efc5000-7efeb000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cc2000-b7cc4000       Deferred        libnvidia-tls.so.1
ELF     b7cc5000-b7cc9000       Deferred        libdl.so.2
ELF     b7cc9000-b7dfd000       Deferred        libc.so.6
ELF     b7dfe000-b7e11000       Deferred        libpthread.so.0
ELF     b7e12000-b7e15000       Deferred        libxau.so.6
ELF     b7e26000-b7f37000       Deferred        libwine.so.1
ELF     b7f39000-b7f54000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000e    0
        0000000d    0
0000000a (D) C:\windows\temp\Blizzard Installer Bootstrap - 00000846\Installer.exe
        00000011    0
        00000010    0
        0000000f    0
        0000000b    0 <==

```

wine is version 0.9.29, it's set to use windows XP as the windows version.  I've tried installing mozcontrol but it seems to have not worked.

currently my current way to update the patches is install the updates on my windows laptop, then just copy over almost the whole WOW directory (everything except WTF and Interface folders).  This is getting old and i just want to be able to apply the patches on my system without having to deal with all these hassles.

does anyone have any clue what's causing this?

---

### Post by spydirweb on 2007-01-23
I found a fix.I saw it on the appdb:

[http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=6482&iThreadId=17395](http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=6482&iThreadId=17395)

it sounds so simple, why didn't I think of it earlier?  It worked, too.  I guess something in my .wine configs got screwed up between updating versions of wine.  Go figure. If the appdb page gets taken down, basicly what you do is just move your .wine to .wine-backup, run winecfg so it rebuilds your wine configs, then just copy anything over what you need to keep.  Simple enough, I'm an idiot, thanks for any help and hopefully if others have the problem this will work.

---

### Post by Entity` on 2007-01-23
Your not an idiot.  Lots of people miss things like that.  Even experts miss things like that.  Its one of those things where the awnser is so simple its rediculously hard.

---

### Post by Ferrat on 2007-01-24
> **Entity` said:**
> Your not an idiot.  Lots of people miss things like that.  Even experts miss things like that.  Its one of those things where the awnser is so simple its rediculously hard.

/agree

The easy faults are often overlooked, the more you know the more you think all problems must be very complex since you couldn't do anything wrong, you know it all ;D 
Happens on a daily basis for me =D

---

