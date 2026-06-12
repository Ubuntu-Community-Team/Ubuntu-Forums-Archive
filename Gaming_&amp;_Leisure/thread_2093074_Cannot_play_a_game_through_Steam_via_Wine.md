---
title: "Cannot play a game through Steam via Wine"
date: 2012-12-09
forum: Gaming &amp; Leisure
---

### Post by Beardedturtle on 2012-12-09
Here is the error message:

```
Unhandled exception: page fault on write access to 0x009d601e in 32-bit code (0x7bc47aac).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc47aac ESP:0033f548 EBP:0033f5a0 EFLAGS:00010202(  R- --  I   - - - )
 EAX:005bf128 EBX:7bca6ff4 ECX:00005580 EDX:009d601a
 ESI:005f8d68 EDI:00000002
Stack dump:
0x0033f548:  0033f584 005bf060 005bf060 005bf060
0x0033f558:  00000002 005f33c8 7bca6ff4 7bc3512f
0x0033f568:  00005580 00000000 00000000 005bf000
0x0033f578:  005bf000 005bf000 005bf000 005bf014
0x0033f588:  005bf014 005bf014 7bc47a0d 00000000
0x0033f598:  005f3368 005f33e0 0033f5dc 0047e8ac
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x7bc47aac RtlAllocateHeap+0xac() in ntdll (0x0033f5a0)
  1 0x0047e8ac in munch (+0x7e8ab) (0x0033f5dc)
  2 0x004759b2 in munch (+0x759b1) (0x0033f604)
  3 0x004757b9 in munch (+0x757b8) (0x0033f644)
  4 0x00475766 in munch (+0x75765) (0x0033f660)
  5 0x00474edf in munch (+0x74ede) (0x0033f674)
0x7bc47aac RtlAllocateHeap+0xac in ntdll: movl    %eax,0x4(%edx)
Modules:
Module    Address            Debug info    Name (166 modules)
PE      3d0000-  3e6000    Deferred        xinput1_3
PE      400000-  4af000    Export          munch
PE     5540000- 5946000    Deferred        munch
PE    10000000-10098000    Deferred        gameoverlayrenderer
PE    18000000-1803a000    Deferred        binkw32
PE    30000000-302c4000    Deferred        steam
PE    38000000-386d5000    Deferred        steamclient
PE    3b400000-3b41f000    Deferred        steam_api
PE    3f000000-3f0a8000    Deferred        tier0_s
PE    3f600000-3f646000    Deferred        vstdlib_s
PE    60000000-60021000    Deferred        cserhelper
ELF    76bab000-76bd0000    Deferred        dmband<elf>
  \-PE    76bb0000-76bd0000    \               dmband
ELF    76bd0000-76c00000    Deferred        dmstyle<elf>
  \-PE    76be0000-76c00000    \               dmstyle
ELF    76d0e000-76d36000    Deferred        dmusic<elf>
  \-PE    76d10000-76d36000    \               dmusic
ELF    7b538000-7b563000    Deferred        libvorbis.so.0
ELF    7b563000-7b6db000    Deferred        libvorbisenc.so.2
ELF    7b6db000-7b729000    Deferred        libflac.so.8
ELF    7b729000-7b79b000    Deferred        libsndfile.so.1
ELF    7b79b000-7b800000    Deferred        libpulsecommon-1.1.so
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7ba20000-7ba28000    Deferred        libogg.so.0
ELF    7ba28000-7ba2f000    Deferred        libasyncns.so.0
ELF    7ba2f000-7ba39000    Deferred        libwrap.so.0
ELF    7ba39000-7ba87000    Deferred        libpulse.so.0
ELF    7ba87000-7bb79000    Deferred        libasound.so.2
ELF    7bb8e000-7bb95000    Deferred        libasound_module_pcm_pulse.so
ELF    7bb95000-7bbc1000    Deferred        winealsa<elf>
  \-PE    7bba0000-7bbc1000    \               winealsa
ELF    7bbc1000-7bc00000    Deferred        dmime<elf>
  \-PE    7bbd0000-7bc00000    \               dmime
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bcc7000-7bccf000    Deferred        libjson.so.0
ELF    7bccf000-7bcf2000    Deferred        mmdevapi<elf>
  \-PE    7bcd0000-7bcf2000    \               mmdevapi
ELF    7bcf2000-7bd1e000    Deferred        dmloader<elf>
  \-PE    7bd00000-7bd1e000    \               dmloader
ELF    7bd1e000-7bd61000    Deferred        dinput<elf>
  \-PE    7bd30000-7bd61000    \               dinput
ELF    7bd61000-7bd79000    Deferred        libresolv.so.2
ELF    7bd79000-7bdc2000    Deferred        libdbus-1.so.3
ELF    7bdc2000-7bdcb000    Deferred        libkrb5support.so.0
ELF    7bdcb000-7bdf3000    Deferred        libk5crypto.so.3
ELF    7bdf3000-7bec2000    Deferred        libkrb5.so.3
ELF    7bec2000-7bf00000    Deferred        libgssapi_krb5.so.2
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7bf07000-7bf0b000    Deferred        libkeyutils.so.1
ELF    7bf0b000-7bf10000    Deferred        libcom_err.so.2
ELF    7bf10000-7bf22000    Deferred        libavahi-client.so.3
ELF    7bf22000-7bf75000    Deferred        libcups.so.2
ELF    7bf7b000-7bf91000    Deferred        wbemprox<elf>
  \-PE    7bf80000-7bf91000    \               wbemprox
ELF    7bf91000-7bff8000    Deferred        setupapi<elf>
  \-PE    7bfa0000-7bff8000    \               setupapi
ELF    7c405000-7c413000    Deferred        libavahi-common.so.3
ELF    7c413000-7c44d000    Deferred        winspool<elf>
  \-PE    7c420000-7c44d000    \               winspool
ELF    7c44d000-7c469000    Deferred        dinput8<elf>
  \-PE    7c450000-7c469000    \               dinput8
ELF    7c469000-7c4ac000    Deferred        dsound<elf>
  \-PE    7c470000-7c4ac000    \               dsound
ELF    7d269000-7d274000    Deferred        libpciaccess.so.0
ELF    7d274000-7d391000    Deferred        libglsl.so
ELF    7d391000-7d60b000    Deferred        libdricore.so
ELF    7d7a6000-7d7c5000    Deferred        libdrm_intel.so.1
ELF    7d7c5000-7d8a5000    Deferred        i965_dri.so
ELF    7d8a5000-7d8ae000    Deferred        librt.so.1
ELF    7d8ae000-7d8c6000    Deferred        libxcb-glx.so.0
ELF    7da06000-7da13000    Deferred        libdrm.so.2
ELF    7da13000-7da16000    Deferred        libx11-xcb.so.1
ELF    7da16000-7da1a000    Deferred        libxdamage.so.1
ELF    7da1a000-7da30000    Deferred        libglapi.so.0
ELF    7da30000-7da89000    Deferred        libgl.so.1
ELF    7da89000-7daa7000    Deferred        libgcc_s.so.1
ELF    7daa7000-7db05000    Deferred        dbghelp<elf>
  \-PE    7dab0000-7db05000    \               dbghelp
ELF    7db05000-7db0a000    Deferred        libgpg-error.so.0
ELF    7db0a000-7db1c000    Deferred        libp11-kit.so.0
ELF    7db1c000-7dba1000    Deferred        libgcrypt.so.11
ELF    7dba1000-7dbb3000    Deferred        libtasn1.so.3
ELF    7dbb3000-7dc77000    Deferred        libgnutls.so.26
ELF    7dc93000-7dcbe000    Deferred        netapi32<elf>
  \-PE    7dca0000-7dcbe000    \               netapi32
ELF    7dcbe000-7dcea000    Deferred        secur32<elf>
  \-PE    7dcc0000-7dcea000    \               secur32
ELF    7dcea000-7dd0c000    Deferred        iphlpapi<elf>
  \-PE    7dcf0000-7dd0c000    \               iphlpapi
ELF    7dd0c000-7dd29000    Deferred        pdh<elf>
  \-PE    7dd10000-7dd29000    \               pdh
ELF    7dd29000-7de1b000    Deferred        oleaut32<elf>
  \-PE    7dd40000-7de1b000    \               oleaut32
ELF    7de1b000-7de2f000    Deferred        psapi<elf>
  \-PE    7de20000-7de2f000    \               psapi
ELF    7de2f000-7dee7000    Deferred        crypt32<elf>
  \-PE    7de40000-7dee7000    \               crypt32
ELF    7dee7000-7df19000    Deferred        ws2_32<elf>
  \-PE    7def0000-7df19000    \               ws2_32
ELF    7df19000-7df41000    Deferred        msacm32<elf>
  \-PE    7df20000-7df41000    \               msacm32
ELF    7df41000-7dfee000    Deferred        winmm<elf>
  \-PE    7df50000-7dfee000    \               winmm
ELF    7dfee000-7e063000    Deferred        rpcrt4<elf>
  \-PE    7e000000-7e063000    \               rpcrt4
ELF    7e063000-7e16b000    Deferred        ole32<elf>
  \-PE    7e080000-7e16b000    \               ole32
ELF    7e1d0000-7e204000    Deferred        uxtheme<elf>
  \-PE    7e1e0000-7e204000    \               uxtheme
ELF    7e204000-7e20a000    Deferred        libxfixes.so.3
ELF    7e20a000-7e215000    Deferred        libxcursor.so.1
ELF    7e215000-7e22f000    Deferred        imagehlp<elf>
  \-PE    7e220000-7e22f000    \               imagehlp
ELF    7e29b000-7e2c5000    Deferred        libexpat.so.1
ELF    7e2c5000-7e2f9000    Deferred        libfontconfig.so.1
ELF    7e2f9000-7e309000    Deferred        libxi.so.6
ELF    7e309000-7e30d000    Deferred        libxcomposite.so.1
ELF    7e30d000-7e316000    Deferred        libxrandr.so.2
ELF    7e316000-7e320000    Deferred        libxrender.so.1
ELF    7e320000-7e326000    Deferred        libxxf86vm.so.1
ELF    7e326000-7e32a000    Deferred        libxinerama.so.1
ELF    7e32a000-7e34c000    Deferred        imm32<elf>
  \-PE    7e330000-7e34c000    \               imm32
ELF    7e34c000-7e353000    Deferred        libxdmcp.so.6
ELF    7e353000-7e357000    Deferred        libxau.so.6
ELF    7e357000-7e378000    Deferred        libxcb.so.1
ELF    7e378000-7e37e000    Deferred        libuuid.so.1
ELF    7e37e000-7e398000    Deferred        libice.so.6
ELF    7e398000-7e4cc000    Deferred        libx11.so.6
ELF    7e4cc000-7e4de000    Deferred        libxext.so.6
ELF    7e4de000-7e4e7000    Deferred        libsm.so.6
ELF    7e4e7000-7e57a000    Deferred        winex11<elf>
  \-PE    7e4f0000-7e57a000    \               winex11
ELF    7e57a000-7e590000    Deferred        libz.so.1
ELF    7e590000-7e62a000    Deferred        libfreetype.so.6
ELF    7e646000-7e77a000    Deferred        wined3d<elf>
  \-PE    7e650000-7e77a000    \               wined3d
ELF    7e77a000-7e7ac000    Deferred        d3d8<elf>
  \-PE    7e780000-7e7ac000    \               d3d8
ELF    7e7ac000-7e8a4000    Deferred        comctl32<elf>
  \-PE    7e7b0000-7e8a4000    \               comctl32
ELF    7e8a4000-7e961000    Deferred        gdi32<elf>
  \-PE    7e8b0000-7e961000    \               gdi32
ELF    7e961000-7eaa1000    Deferred        user32<elf>
  \-PE    7e970000-7eaa1000    \               user32
ELF    7eaa1000-7eb0b000    Deferred        shlwapi<elf>
  \-PE    7eab0000-7eb0b000    \               shlwapi
ELF    7eb0b000-7ed1c000    Deferred        shell32<elf>
  \-PE    7eb20000-7ed1c000    \               shell32
ELF    7ed1c000-7ed7c000    Deferred        advapi32<elf>
  \-PE    7ed30000-7ed7c000    \               advapi32
ELF    7ed7c000-7ed89000    Deferred        libnss_files.so.2
ELF    7ed89000-7ed95000    Deferred        libnss_nis.so.2
ELF    7ed95000-7edaf000    Deferred        libnsl.so.1
ELF    7edaf000-7edb8000    Deferred        libnss_compat.so.2
ELF    7efb8000-7efe4000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7402000-f7407000    Deferred        libdl.so.2
ELF    f7407000-f75b1000    Deferred        libc.so.6
ELF    f75b2000-f75cd000    Deferred        libpthread.so.0
ELF    f75e9000-f772b000    Dwarf           libwine.so.1
ELF    f772d000-f774f000    Deferred        ld-linux.so.2
ELF    f774f000-f7750000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000014    0
    00000013    0
00000019 plugplay.exe
    00000020    0
    0000001c    0
    0000001a    0
00000021 explorer.exe
    00000022    0
00000023 Steam.exe
    00000053    0
    00000052    0
    00000051    0
    00000050    1
    0000004f    1
    0000004e    0
    0000004d    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    00000045    0
    0000003a    0
    00000027    0
    0000000d    0
    00000009    0
    0000000b    0
    00000047    0
    00000046    0
    00000043    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    00000039    0
    00000038    0
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
    00000028    0
    00000026    0
    00000025    0
    00000024    0
00000056 (D) C:\Program Files (x86)\Steam\steamapps\common\Oddworld Munchs Oddysee\bin\Munch.exe
    0000005c    0
    0000005b   15
    00000058   15
    00000063    0
    00000062    0
    00000061    0
    00000059    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-34-generic
```

---

### Post by holastickboy on 2012-12-11
I'm not an expert, but it appears you are trying to run Munchs Oddysee, which is not 100% compatible with WINE (according to the winehq database [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23957](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23957))

Have you tried any other games that have definitely been confirmed working on WINE? Such as Half Life 2 for example.

---

### Post by Beardedturtle on 2012-12-11
> **holastickboy said:**
> I'm not an expert, but it appears you are trying to run Munchs Oddysee, which is not 100% compatible with WINE (according to the winehq database [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23957](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23957))

Have you tried any other games that have definitely been confirmed working on WINE? Such as Half Life 2 for example.
  Give me a hint to where I can get a software to run MO. Torchlight 1 and 2 works with garbled sound.....

---

