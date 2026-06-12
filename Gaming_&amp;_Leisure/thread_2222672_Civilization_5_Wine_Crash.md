---
title: "Civilization 5 Wine Crash"
date: 2014-05-07
forum: Gaming &amp; Leisure
---

### Post by toreygrant on 2014-05-07
Hey can anyone make sense of this? My Civ 5 is crashing when attempting to start a new match. 


Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x05f56999).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:05f56999 ESP:0033cd7c EBP:00000000 EFLAGS:00210202(  R- --  I   - - - )
 EAX:00000001 EBX:00000001 ECX:00000000 EDX:00000001
 ESI:0e8d3188 EDI:00000008
Stack dump:
0x0033cd7c:  00000001 05f5baba 00000001 00000001
0x0033cd8c:  0e8d3188 0e8d3188 0033d0f0 00000190
0x0033cd9c:  656c6573 2a207463 6f726620 7542206d
0x0033cdac:  73646c69 65687720 53206572 49776f68
0x0033cdbc:  6365546e 65725468 203d2065 6e61203f
0x0033cdcc:  72502064 71657265 68636554 3f203d20
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x05f56999 in cvgamedatabasewin32final releaseC:\Program Files (x86)\Steam\SteamApps\common\Sid Meier's Civilization V\CvGameDatabaseWin32Final Release.dll (+0x6999) (0x00000000)
0x05f56999: movl    0x8(%ecx),%eax
Modules:
Module    Address            Debug info    Name (214 modules)
PE      340000-  353000    Deferred        zlib1
PE      360000-  388000    Deferred        lua51_win32
PE      390000-  3fb000    Deferred        mss32
PE      400000- 5e73000    Deferred        civilizationv
PE     5e80000- 5f4f000    Deferred        cvlocalizationwin32final releaseC:\Program Files (x86)\Steam\SteamApps\common\Sid Meier's Civilization V\CvLocalizationWin32Final Release.dll
PE     5f50000- 6574000    Export          cvgamedatabasewin32final releaseC:\Program Files (x86)\Steam\SteamApps\common\Sid Meier's Civilization V\CvGameDatabaseWin32Final Release.dll
PE     f8e0000- f9ac000    Deferred        steam
PE     fd60000- fd67000    Deferred        mssds3d.flt
PE     ff80000- ff91000    Deferred        binkawin.asi
PE     ffa0000- ffb7000    Deferred        mssmp3.asi
PE     ffc0000- ffc6000    Deferred        mssdolby.flt
PE    10000000-101e5000    Deferred        d3dx9_42
PE    216e0000-21d28000    Deferred        cvgamecore_expansion1
PE    22300000-22311000    Deferred        msseax.flt
PE    23000000-23007000    Deferred        msssrs.flt
PE    24100000-24111000    Deferred        mssdsp.flt
PE    26400000-2642a000    Deferred        mssvoice.asi
PE    26f00000-26f0d000    Deferred        mssogg.asi
PE    30000000-302c1000    Deferred        steam2
PE    38000000-388a5000    Deferred        steamclient
PE    3b400000-3b41e000    Deferred        steam_api
PE    3f000000-3f0ac000    Deferred        tier0_s
PE    3f600000-3f64b000    Deferred        vstdlib_s
PE    60000000-60021000    Deferred        cserhelper
PE    78aa0000-78b5f000    Deferred        msvcr100
ELF    7b800000-7ba5b000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d19f000-7d1a8000    Deferred        librt.so.1
ELF    7d1a8000-7d1af000    Deferred        libffi.so.6
ELF    7d1af000-7d1b4000    Deferred        libgpg-error.so.0
ELF    7d1b4000-7d1cc000    Deferred        libresolv.so.2
ELF    7d1cc000-7d217000    Deferred        libdbus-1.so.3
ELF    7d217000-7d253000    Deferred        libp11-kit.so.0
ELF    7d253000-7d267000    Deferred        libtasn1.so.6
ELF    7d267000-7d2ed000    Deferred        libgcrypt.so.11
ELF    7d2ed000-7d2f9000    Deferred        libkrb5support.so.0
ELF    7d2f9000-7d329000    Deferred        libk5crypto.so.3
ELF    7d329000-7d3e7000    Deferred        libkrb5.so.3
ELF    7d3e7000-7d3f9000    Deferred        libavahi-client.so.3
ELF    7d3f9000-7d4bf000    Deferred        libgnutls.so.26
ELF    7d4bf000-7d504000    Deferred        libgssapi_krb5.so.2
ELF    7d504000-7d571000    Deferred        libcups.so.2
ELF    7d58d000-7d5c4000    Deferred        uxtheme<elf>
  \-PE    7d590000-7d5c4000    \               uxtheme
ELF    7d5c4000-7d5ca000    Deferred        libxfixes.so.3
ELF    7d5ca000-7d5d5000    Deferred        libxcursor.so.1
ELF    7d5d5000-7d5e6000    Deferred        libxi.so.6
ELF    7d5e6000-7d5ea000    Deferred        libxcomposite.so.1
ELF    7d5ea000-7d5f5000    Deferred        libxrandr.so.2
ELF    7d5f5000-7d600000    Deferred        libxrender.so.1
ELF    7d600000-7d606000    Deferred        libxxf86vm.so.1
ELF    7d606000-7d60a000    Deferred        libxinerama.so.1
ELF    7d60a000-7d611000    Deferred        libxdmcp.so.6
ELF    7d611000-7d615000    Deferred        libxau.so.6
ELF    7d615000-7d637000    Deferred        libxcb.so.1
ELF    7d637000-7d76b000    Deferred        libx11.so.6
ELF    7d76b000-7d77e000    Deferred        libxext.so.6
ELF    7d781000-7d785000    Deferred        libkeyutils.so.1
ELF    7d785000-7d78a000    Deferred        libcom_err.so.2
ELF    7d78a000-7d798000    Deferred        libavahi-common.so.3
ELF    7d79a000-7d82c000    Deferred        winex11<elf>
  \-PE    7d7a0000-7d82c000    \               winex11
ELF    7d9b2000-7d9db000    Deferred        libexpat.so.1
ELF    7d9db000-7da16000    Deferred        libfontconfig.so.1
ELF    7da16000-7da3e000    Deferred        libpng12.so.0
ELF    7da3e000-7dadd000    Deferred        libfreetype.so.6
ELF    7dadd000-7dbec000    Deferred        opengl32<elf>
  \-PE    7db00000-7dbec000    \               opengl32
ELF    7dbec000-7dd2c000    Deferred        wined3d<elf>
  \-PE    7dc00000-7dd2c000    \               wined3d
ELF    7dd2c000-7dd69000    Deferred        d3d9<elf>
  \-PE    7dd30000-7dd69000    \               d3d9
ELF    7dd69000-7dd83000    Deferred        libz.so.1
ELF    7dd83000-7ddeb000    Deferred        dbghelp<elf>
  \-PE    7dd90000-7ddeb000    \               dbghelp
ELF    7ddeb000-7ded6000    Deferred        comdlg32<elf>
  \-PE    7ddf0000-7ded6000    \               comdlg32
ELF    7ded6000-7e00c000    Deferred        oleaut32<elf>
  \-PE    7def0000-7e00c000    \               oleaut32
ELF    7e00c000-7e096000    Deferred        gdiplus<elf>
  \-PE    7e020000-7e096000    \               gdiplus
ELF    7e096000-7e2c9000    Deferred        shell32<elf>
  \-PE    7e0a0000-7e2c9000    \               shell32
ELF    7e309000-7e349000    Deferred        winspool<elf>
  \-PE    7e310000-7e349000    \               winspool
ELF    7e349000-7e35d000    Deferred        msimg32<elf>
  \-PE    7e350000-7e35d000    \               msimg32
ELF    7e35d000-7e464000    Deferred        comctl32<elf>
  \-PE    7e360000-7e464000    \               comctl32
ELF    7e464000-7e4de000    Deferred        shlwapi<elf>
  \-PE    7e470000-7e4de000    \               shlwapi
ELF    7e4de000-7e61b000    Deferred        msvcp90<elf>
  \-PE    7e520000-7e61b000    \               msvcp90
ELF    7e61b000-7e648000    Deferred        msvcr90<elf>
  \-PE    7e620000-7e648000    \               msvcr90
ELF    7e648000-7e66d000    Deferred        imm32<elf>
  \-PE    7e650000-7e66d000    \               imm32
ELF    7e66d000-7e6aa000    Deferred        winhttp<elf>
  \-PE    7e670000-7e6aa000    \               winhttp
ELF    7e6aa000-7e752000    Deferred        msvcrt<elf>
  \-PE    7e6c0000-7e752000    \               msvcrt
ELF    7e752000-7e77d000    Deferred        msacm32<elf>
  \-PE    7e760000-7e77d000    \               msacm32
ELF    7e77d000-7e7fe000    Deferred        rpcrt4<elf>
  \-PE    7e790000-7e7fe000    \               rpcrt4
ELF    7e7fe000-7e93a000    Deferred        ole32<elf>
  \-PE    7e810000-7e93a000    \               ole32
ELF    7e93a000-7e954000    Deferred        version<elf>
  \-PE    7e940000-7e954000    \               version
ELF    7e954000-7e9c6000    Deferred        advapi32<elf>
  \-PE    7e960000-7e9c6000    \               advapi32
ELF    7e9c6000-7eae3000    Deferred        gdi32<elf>
  \-PE    7e9d0000-7eae3000    \               gdi32
ELF    7eae3000-7ec3d000    Deferred        user32<elf>
  \-PE    7eb00000-7ec3d000    \               user32
ELF    7ec3d000-7ecf7000    Deferred        winmm<elf>
  \-PE    7ec40000-7ecf7000    \               winmm
ELF    7ecf7000-7ed2d000    Deferred        ws2_32<elf>
  \-PE    7ed00000-7ed2d000    \               ws2_32
ELF    7ed2d000-7ed3a000    Deferred        libnss_files.so.2
ELF    7ed3a000-7ed46000    Deferred        libnss_nis.so.2
ELF    7ed46000-7ed5f000    Deferred        libnsl.so.1
ELF    7ef9e000-7efe4000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        psapi<elf>
  \-PE    7eff0000-7f000000    \               psapi
ELF    f5cd6000-f5d06000    Deferred        p11-kit-trust.so
ELF    f5d06000-f5d33000    Deferred        netapi32<elf>
  \-PE    f5d10000-f5d33000    \               netapi32
ELF    f5d33000-f5e02000    Deferred        crypt32<elf>
  \-PE    f5d40000-f5e02000    \               crypt32
ELF    f5e54000-f5e80000    Deferred        msvfw32<elf>
  \-PE    f5e60000-f5e80000    \               msvfw32
ELF    f5e80000-f5f71000    Deferred        quartz<elf>
  \-PE    f5e90000-f5f71000    \               quartz
ELF    f620a000-f6300000    Deferred        libasound.so.2
ELF    f640d000-f6440000    Deferred        secur32<elf>
  \-PE    f6410000-f6440000    \               secur32
ELF    f6440000-f6456000    Deferred        midimap<elf>
  \-PE    f6450000-f6456000    \               midimap
ELF    f6456000-f6486000    Deferred        winealsa<elf>
  \-PE    f6460000-f6486000    \               winealsa
ELF    f6486000-f64b2000    Deferred        libvorbis.so.0
ELF    f64b2000-f662a000    Deferred        libvorbisenc.so.2
ELF    f662a000-f665e000    Deferred        libflac.so.8
ELF    f665e000-f66d0000    Deferred        libsndfile.so.1
ELF    f66d0000-f673f000    Deferred        libpulsecommon-4.0.so
ELF    f6746000-f675f000    Deferred        msacm32<elf>
  \-PE    f6750000-f675f000    \               msacm32
ELF    f675f000-f6768000    Deferred        libogg.so.0
ELF    f6768000-f676f000    Deferred        libasyncns.so.0
ELF    f676f000-f6779000    Deferred        libwrap.so.0
ELF    f6779000-f6784000    Deferred        libjson-c.so.2
ELF    f6784000-f67d3000    Deferred        libpulse.so.0
ELF    f67ef000-f6817000    Deferred        winepulse<elf>
  \-PE    f6800000-f6817000    \               winepulse
ELF    f6817000-f6839000    Deferred        mmdevapi<elf>
  \-PE    f6820000-f6839000    \               mmdevapi
ELF    f6865000-f68ae000    Deferred        dsound<elf>
  \-PE    f6870000-f68ae000    \               dsound
ELF    f68c2000-f68d5000    Deferred        gnome-keyring-pkcs11.so
ELF    f68d5000-f6946000    Deferred        setupapi<elf>
  \-PE    f68e0000-f6946000    \               setupapi
ELF    f6946000-f6960000    Deferred        imagehlp<elf>
  \-PE    f6950000-f6960000    \               imagehlp
ELF    f6960000-f6978000    Deferred        wtsapi32<elf>
  \-PE    f6970000-f6978000    \               wtsapi32
ELF    f6978000-f699c000    Deferred        gameux<elf>
  \-PE    f6980000-f699c000    \               gameux
ELF    f699f000-f69b4000    Deferred        avicap32<elf>
  \-PE    f69a0000-f69b4000    \               avicap32
ELF    f69b4000-f69db000    Deferred        devenum<elf>
  \-PE    f69c0000-f69db000    \               devenum
ELF    f69f3000-f6a2a000    Deferred        libtxc_dxtn.so
ELF    f6a2a000-f6a35000    Deferred        libpciaccess.so.0
ELF    f6a35000-f6a52000    Deferred        libgcc_s.so.1
ELF    f6b3b000-f6b4a000    Deferred        libdrm_radeon.so.1
ELF    f6b4a000-f6b52000    Deferred        libdrm_nouveau.so.2
ELF    f6b52000-f6b74000    Deferred        libdrm_intel.so.1
ELF    f6b74000-f70e5000    Deferred        i965_dri.so
ELF    f70e5000-f70ef000    Deferred        libnih-dbus.so.1
ELF    f70ef000-f7108000    Deferred        libnih.so.1
ELF    f7108000-f7125000    Deferred        libcgmanager.so.0
ELF    f7125000-f7138000    Deferred        libudev.so.1
ELF    f7138000-f7145000    Deferred        libdrm.so.2
ELF    f7145000-f714c000    Deferred        libxcb-sync.so.1
ELF    f714c000-f7150000    Deferred        libxcb-present.so.0
ELF    f7150000-f7154000    Deferred        libxcb-dri3.so.0
ELF    f7154000-f716c000    Deferred        libxcb-glx.so.0
ELF    f716c000-f7184000    Deferred        libglapi.so.0
ELF    f7184000-f71e4000    Deferred        libgl.so.1
ELF    f7200000-f7227000    Deferred        dxgi<elf>
  \-PE    f7210000-f7227000    \               dxgi
ELF    f7227000-f724d000    Deferred        iphlpapi<elf>
  \-PE    f7230000-f724d000    \               iphlpapi
ELF    f724d000-f727f000    Deferred        wbemprox<elf>
  \-PE    f7250000-f727f000    \               wbemprox
ELF    f727f000-f72f4000    Deferred        ddraw<elf>
  \-PE    f7290000-f72f4000    \               ddraw
ELF    f72f4000-f731a000    Deferred        dxdiagn<elf>
  \-PE    f7300000-f731a000    \               dxdiagn
ELF    f7362000-f736b000    Deferred        libnss_compat.so.2
ELF    f736c000-f751b000    Deferred        libc.so.6
ELF    f751b000-f7520000    Deferred        libdl.so.2
ELF    f7521000-f753d000    Deferred        libpthread.so.0
ELF    f7540000-f7543000    Deferred        libxshmfence.so.1
ELF    f7543000-f7549000    Deferred        libxcb-dri2.so.0
ELF    f7549000-f754c000    Deferred        libx11-xcb.so.1
ELF    f754c000-f7550000    Deferred        libxdamage.so.1
ELF    f7559000-f770e000    Dwarf           libwine.so.1
ELF    f7710000-f7732000    Deferred        ld-linux.so.2
ELF    f7732000-f7733000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    000000be    0
    0000008c    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
00000024 Steam.exe
    000000ce    0
    000000cd    0
    00000063    0
    00000060    0
    0000005d    0
    00000058    0
    00000052    0
    00000026    0
    00000027    0
    00000028    0
    0000000d    0
    0000000b    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d   15
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000025    0
0000008a svchost.exe
    000000ac    0
    00000094    0
    00000093    0
    00000091    0
    00000090    0
    0000008f    0
    0000008b    0
000000ec (D) C:\Program Files (x86)\Steam\SteamApps\common\Sid Meier's Civilization V\CivilizationV.exe
    0000008d    0
    000000b1    0
    000000b2    0
    000000d5    0
    00000078    0
    0000007a    0
    0000007b    0
    0000007d    0
    0000007c    0
    00000084    0
    00000095    0
    00000069    0
    0000006d    0
    0000006e    0
    00000071    0
    00000099    0
    00000098    0
    0000006c    0
    00000088    0
    0000006b    0
    000000de    0
    00000081    0
    000000d8    0
    000000a7    0
    00000086    0
    000000d0    0
    000000eb    0
    000000e2    0
    0000014b    0
    0000014a    0
    00000149    0
    00000148    0
    00000147    0
    00000146    0
    00000145    0
    00000144    0
    00000143    0
    00000142    0
    00000141    0
    00000140    0
    0000013f    0
    0000013e    0
    0000013d    0
    0000013c    0
    0000013b    0
    0000013a    0
    00000139    0
    00000138    0
    00000137    0
    00000136    0
    00000135    0
    00000134    0
    00000133    0
    00000132    0
    00000131    0
    00000130    0
    0000012f    0
    0000012e    0
    0000012d    0
    0000012c    0
    0000012b    0
    0000012a    0
    00000129    0
    00000128    0
    00000127    0
    00000126    0
    00000125    0
    00000124    0
    00000123    0
    00000122    0
    00000121    0
    00000120    0
    0000011f    0
    0000011e    0
    0000011d    0
    0000011c    0
    0000011b    0
    0000011a    0
    00000119    0
    00000118    0
    00000117    0
    00000116    0
    00000115    0
    00000114    0
    00000113    0
    00000112    0
    00000111    0
    00000110    0
    0000010f    0
    0000010e    0
    0000010d    0
    0000010c    0
    0000010b    0
    0000010a    0
    00000109    0
    00000108    0
    00000107    0
    00000106    0
    00000105   15
    00000104   15
    00000102    0
    000000f5    0
    000000f4    0
    000000f3    0
    000000f2    0
    000000f1    0
    000000f0    0
    000000ef    0
    000000ee   15
    000000ed    0 <==
000000f6 Launcher.exe
    000000f7    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-24-generic

---

### Post by hoover67 on 2014-08-10
I'm having a similar issue, in my case civ 5 (steam version) fails to launch on 14.04 32 bit edition: 

$ steam steam://rungameid/8930
Running Steam on ubuntu 14.04 32-bit
STEAM_RUNTIME is enabled automatically

A window appears briefly and closes again, no other errors are displayed. System is up to date AFAIK, also Civ5 lists no patches in the game library. 

Any idea how to debug this further? 

All the best, hoover

---

### Post by oldrocker99 on 2014-08-10
You **are** aware that a nearly flawless native port of CIV V (which works on a variety of distributions, not just Ubuntu) and works without wine, is available on Steam for Linux? That's how **I** play CIV V.  You probably will be able to download it without paying again; this **is** Steam, whose policy is "Buy it once, play on Windows, Mac or Linux."

---

