---
title: "AMD Radeon GPU only uses 384MB VRAM instead of +2GB dedicated video-memory"
date: 2013-03-24
forum: Gaming &amp; Leisure
---

### Post by Raklodder on 2013-03-24
Dear people,

for some reason a majority if not all games are limited to only 384MBs of video memory (VRAM) instead of it's full 2048MB dedicated memory. I read somewhere that disabling "Sych with VBlank" in the OpenGL-menu would resolve this, but it sure as hell did not. Now what could be the cause of this?[I] Take note that all mentioned 3D-applications have been run with **Wine 1.5.26, PlayOnLinux 4.0.14** with **AMD** **Catalyst 13.1, 13.2 and 13.3-beta3 **will crash at random stating that there's not enough video memory, vram which in the end make everything extremely unplayable if not beyond that.
[/I]
**Error:**
> Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x018aeb5c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:018aeb5c ESP:0033f0f8 EBP:00000000 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00007fff EBX:00000000 ECX:0000001c EDX:063f3d36
 ESI:2eb88004 EDI:00000001
Stack dump:
0x0033f0f8:  0033f4d4 0072e3f0 0033f304 31a70348
0x0033f108:  02ff0010 c38bf9ec 42934a0d 063f3d36
0x0033f118:  063f3d36 ff3f3d36 ff3f3d36 43dfdec1
0x0033f128:  2eb88054 c38c3821 43dedec1 428f68be
0x0033f138:  063f3d36 000000a8 ff3f3d36 063f3d36
0x0033f148:  000000a8 41f00000 bf7e55f9 bdce5ea0
000c: sel=0067 base=00000000 limit=00000000 16-bit rw-
Backtrace:
=>0 0x018aeb5c in gameclient (+0x14eb5c) (0x00000000)
0x018aeb5c: fsts    0xffffffe4(%ecx)
Modules:
Module    Address            Debug info    Name (144 modules)
PE      340000-  355000    Deferred        gamedatabase
PE      360000-  368000    Deferred        ltmemory
PE      370000-  377000    Deferred        x3daudio1_5
PE      3a0000-  3a7000    Deferred        stringeditruntime
PE      400000-  7c6000    Deferred        fear2
PE      7d0000-  c1a000    Deferred        d3dx9_40
PE      fe0000- 1028000    Deferred        steamclient
PE     1140000- 118b000    Deferred        steam
PE     1760000- 1992000    Export          gameclient
PE     1aa0000- 1ae3000    Deferred        clientfx.fxd
PE     1ed0000- 1f5b000    Deferred        xaudio2_3
PE    10000000-10015000    Deferred        steam_api
PE    18000000-18033000    Deferred        binkw32
ELF    7939e000-79400000    Deferred        libatiadlxx.so
ELF    7943f000-7b800000    Deferred        fglrx_dri.so
ELF    7b800000-7ba45000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba45000    \               kernel32
ELF    7bc00000-7bcd9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcd9000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c4bf000-7c522000    Deferred        libmpg123.so.0
ELF    7c522000-7c53a000    Deferred        libresolv.so.2
ELF    7c53a000-7c542000    Deferred        libogg.so.0
ELF    7c542000-7c56d000    Deferred        libvorbis.so.0
ELF    7c56d000-7c6e5000    Deferred        libvorbisenc.so.2
ELF    7cd4a000-7cd92000    Deferred        dsound<elf>
  \-PE    7cd50000-7cd92000    \               dsound
ELF    7cd92000-7cde0000    Deferred        libflac.so.8
ELF    7cde0000-7ce52000    Deferred        libsndfile.so.1
ELF    7ce52000-7ce9b000    Deferred        libdbus-1.so.3
ELF    7ce9b000-7cf00000    Deferred        libpulsecommon-1.1.so
ELF    7d013000-7d029000    Deferred        winemp3<elf>
  \-PE    7d020000-7d029000    \               winemp3
ELF    7d029000-7d040000    Deferred        imaadp32<elf>
  \-PE    7d030000-7d040000    \               imaadp32
ELF    7d040000-7d08e000    Deferred        libpulse.so.0
ELF    7d08e000-7d095000    Deferred        libnss_dns.so.2
ELF    7d095000-7d0aa000    Deferred        avrt<elf>
  \-PE    7d0a0000-7d0aa000    \               avrt
ELF    7d0aa000-7d0d2000    Deferred        winepulse<elf>
  \-PE    7d0b0000-7d0d2000    \               winepulse
ELF    7d0d2000-7d0f4000    Deferred        mmdevapi<elf>
  \-PE    7d0e0000-7d0f4000    \               mmdevapi
ELF    7d434000-7d452000    Deferred        libgcc_s.so.1
ELF    7d452000-7d46b000    Deferred        libatiuki.so.1
ELF    7d46b000-7d557000    Deferred        libgl.so.1
ELF    7d562000-7d569000    Deferred        libasyncns.so.0
ELF    7d569000-7d573000    Deferred        libwrap.so.0
ELF    7d573000-7d63c000    Deferred        crypt32<elf>
  \-PE    7d580000-7d63c000    \               crypt32
ELF    7d63c000-7d672000    Deferred        wintrust<elf>
  \-PE    7d640000-7d672000    \               wintrust
ELF    7d672000-7d686000    Deferred        psapi<elf>
  \-PE    7d680000-7d686000    \               psapi
ELF    7d686000-7d6ee000    Deferred        dbghelp<elf>
  \-PE    7d690000-7d6ee000    \               dbghelp
ELF    7d72d000-7d735000    Deferred        libjson.so.0
ELF    7d74c000-7d782000    Deferred        uxtheme<elf>
  \-PE    7d750000-7d782000    \               uxtheme
ELF    7d782000-7d7a6000    Deferred        imm32<elf>
  \-PE    7d790000-7d7a6000    \               imm32
ELF    7d7a6000-7d7ac000    Deferred        libxfixes.so.3
ELF    7d7ac000-7d7b7000    Deferred        libxcursor.so.1
ELF    7d7b7000-7d7c7000    Deferred        libxi.so.6
ELF    7d7c7000-7d7cb000    Deferred        libxcomposite.so.1
ELF    7d7cb000-7d7d4000    Deferred        libxrandr.so.2
ELF    7d7d4000-7d7de000    Deferred        libxrender.so.1
ELF    7d7de000-7d7e4000    Deferred        libxxf86vm.so.1
ELF    7d7e4000-7d7e8000    Deferred        libxinerama.so.1
ELF    7d7e8000-7d7ef000    Deferred        libxdmcp.so.6
ELF    7d7ef000-7d7f3000    Deferred        libxau.so.6
ELF    7d7f3000-7d814000    Deferred        libxcb.so.1
ELF    7d814000-7d81a000    Deferred        libuuid.so.1
ELF    7d81a000-7d834000    Deferred        libice.so.6
ELF    7d834000-7d968000    Deferred        libx11.so.6
ELF    7d968000-7d97a000    Deferred        libxext.so.6
ELF    7d97a000-7d983000    Deferred        libsm.so.6
ELF    7d99f000-7da32000    Deferred        winex11<elf>
  \-PE    7d9b0000-7da32000    \               winex11
ELF    7da81000-7daab000    Deferred        libexpat.so.1
ELF    7daab000-7dadf000    Deferred        libfontconfig.so.1
ELF    7dadf000-7daf5000    Deferred        libz.so.1
ELF    7daf5000-7db8f000    Deferred        libfreetype.so.6
ELF    7dbab000-7dce5000    Deferred        oleaut32<elf>
  \-PE    7dbc0000-7dce5000    \               oleaut32
ELF    7dce5000-7dded000    Deferred        comctl32<elf>
  \-PE    7dcf0000-7dded000    \               comctl32
ELF    7dded000-7de65000    Deferred        shlwapi<elf>
  \-PE    7de00000-7de65000    \               shlwapi
ELF    7de65000-7e093000    Deferred        shell32<elf>
  \-PE    7de70000-7e093000    \               shell32
ELF    7e093000-7e1a1000    Deferred        opengl32<elf>
  \-PE    7e0b0000-7e1a1000    \               opengl32
ELF    7e1a1000-7e2da000    Deferred        wined3d<elf>
  \-PE    7e1b0000-7e2da000    \               wined3d
ELF    7e2da000-7e317000    Deferred        d3d9<elf>
  \-PE    7e2e0000-7e317000    \               d3d9
ELF    7e317000-7e33d000    Deferred        iphlpapi<elf>
  \-PE    7e320000-7e33d000    \               iphlpapi
ELF    7e33d000-7e373000    Deferred        ws2_32<elf>
  \-PE    7e340000-7e373000    \               ws2_32
ELF    7e373000-7e38f000    Deferred        wsock32<elf>
  \-PE    7e380000-7e38f000    \               wsock32
ELF    7e38f000-7e3ba000    Deferred        msacm32<elf>
  \-PE    7e390000-7e3ba000    \               msacm32
ELF    7e3ba000-7e470000    Deferred        winmm<elf>
  \-PE    7e3c0000-7e470000    \               winmm
ELF    7e470000-7e5ae000    Deferred        msvcp90<elf>
  \-PE    7e4b0000-7e5ae000    \               msvcp90
ELF    7e5ae000-7e650000    Deferred        msvcp80<elf>
  \-PE    7e5c0000-7e650000    \               msvcp80
ELF    7e650000-7e689000    Deferred        msvcr100<elf>
  \-PE    7e660000-7e689000    \               msvcr100
ELF    7e689000-7e72f000    Deferred        msvcrt<elf>
  \-PE    7e6a0000-7e72f000    \               msvcrt
ELF    7e72f000-7e75d000    Deferred        msvcr80<elf>
  \-PE    7e740000-7e75d000    \               msvcr80
ELF    7e75d000-7e7de000    Deferred        rpcrt4<elf>
  \-PE    7e770000-7e7de000    \               rpcrt4
ELF    7e7de000-7e919000    Deferred        ole32<elf>
  \-PE    7e7f0000-7e919000    \               ole32
ELF    7e942000-7e95a000    Deferred        wtsapi32<elf>
  \-PE    7e950000-7e95a000    \               wtsapi32
ELF    7e95a000-7e9c9000    Deferred        advapi32<elf>
  \-PE    7e970000-7e9c9000    \               advapi32
ELF    7e9c9000-7eae4000    Deferred        gdi32<elf>
  \-PE    7e9e0000-7eae4000    \               gdi32
ELF    7eae4000-7ec3e000    Deferred        user32<elf>
  \-PE    7eb00000-7ec3e000    \               user32
ELF    7ec3e000-7ec58000    Deferred        libnsl.so.1
ELF    7ec58000-7ec61000    Deferred        libnss_compat.so.2
ELF    7ec63000-7ec7d000    Deferred        version<elf>
  \-PE    7ec70000-7ec7d000    \               version
ELF    7efaf000-7efdb000    Deferred        libm.so.6
ELF    7efdb000-7efe4000    Deferred        librt.so.1
ELF    7efe7000-7eff4000    Deferred        libnss_files.so.2
ELF    7eff4000-7f000000    Deferred        libnss_nis.so.2
PE    7f4a0000-7f81e000    Deferred        gameserver
ELF    f7473000-f7478000    Deferred        libdl.so.2
ELF    f7478000-f7622000    Deferred        libc.so.6
ELF    f7623000-f763e000    Deferred        libpthread.so.0
ELF    f765a000-f779e000    Dwarf           libwine.so.1
ELF    f77a0000-f77c2000    Deferred        ld-linux.so.2
ELF    f77c2000-f77c3000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
00000025 (D) C:\Program Files (x86)\Fear2\FEAR2.exe
    00000046    0
    0000003f    0
    0000003e    0
    00000032    0
    00000031   15
    00000030    0
    0000002f   15
    0000002e    0
    0000002d    0
    0000002c   15
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
    00000026    0 <==
System information:
    Wine build: wine-1.5.26
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.5.0-26-generic

**Source:** [http://askubuntu.com/questions/63074/why-is-my-video-ram-256mb-when-it-should-be-2gb](http://askubuntu.com/questions/63074/why-is-my-video-ram-256mb-when-it-should-be-2gb)[B]

Hardware:[/B] P8P67 DELUXE B3, i7-2600K, 8GB, NH-D14, HD6970, RAiD 0+1, BD-RE, HX850, DEFiNE R3, UBUNTU 12.04

Thanks in advance
Raklodder

---

