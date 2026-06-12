---
title: "Latest patch of League of legends 4.16 crash when im logging in"
date: 2014-09-11
forum: Gaming &amp; Leisure
---

### Post by fredrik4 on 2014-09-11
Sometimes i get the message instantlly and after tried like 6 times i got in, but the message came up after a while.

I got this message:

Unhandled exception: assertion failed in 32-bit code (0xf76ff430).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f76ff430 ESP:1f72d5d4 EBP:1f72d7b8 EFLAGS:00200296(   - --  I S -A-P- )
 EAX:00000000 EBX:00007022 ECX:000070f2 EDX:00000006
 ESI:7d2b5000 EDI:f74e7000
Stack dump:
0x1f72d5d4:  1f72d7b8 00000006 000070f2 f7369577
0x1f72d5e4:  f74e7000 1f72d684 f736c9a3 00000006
0x1f72d5f4:  1f72d604 00000000 f73b1f98 1f72d640
0x1f72d604:  00000020 00000000 00000000 00000000
0x1f72d614:  00000000 00000000 00000000 00000000
0x1f72d624:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0xf76ff430 __kernel_vsyscall+0x10() in [vdso].so (0x1f72d7b8)
  1 0xf7369577 gsignal+0x46() in libc.so.6 (0x1f72d7b8)
  2 0xf736c9a3 abort+0x142() in libc.so.6 (0x1f72d7b8)
  3 0xf73626c7 in libc.so.6 (+0x276c6) (0x1f72d7b8)
  4 0xf7362777 __assert_fail+0x56() in libc.so.6 (0x1f72d7b8)
  5 0x7d59e2e5 in libgcrypt.so.11 (+0xf2e4) (0x1f72d7b8)
  6 0x7d5db9f0 in libgcrypt.so.11 (+0x4c9ef) (0x1f72d7d8)
  7 0x7d5dbb8c in libgcrypt.so.11 (+0x4cb8b) (0x1f72d7f8)
  8 0x7d5dbcbc in libgcrypt.so.11 (+0x4ccbb) (0x1f72d848)
  9 0x7d5db5c5 in libgcrypt.so.11 (+0x4c5c4) (0x1f72d878)
  10 0x7d5943d4 gcry_create_nonce+0x63() in libgcrypt.so.11 (0x1f72d8a8)
  11 0x7d76d0e4 in libgnutls.so.26 (+0x3b0e3) (0x1f72d8c8)
  12 0x7d76addf _gnutls_rnd+0x3e() in libgnutls.so.26 (0x1f72d8e8)
  13 0x7d747919 in libgnutls.so.26 (+0x15918) (0x1f72d918)
  14 0x7d74a728 in libgnutls.so.26 (+0x18727) (0x1f72dda8)
  15 0x7d74ae34 in libgnutls.so.26 (+0x18e33) (0x1f72dde8)
  16 0x7d74b890 gnutls_handshake+0x10f() in libgnutls.so.26 (0x1f72de28)
  17 0x7d987957 in secur32 (+0x17956) (0x1f72de78)
  18 0x7d98520a in secur32 (+0x15209) (0x1f72df48)
  19 0x7d98719a in secur32 (+0x17199) (0x1f72dfe8)
  20 0x7d98e7fc InitializeSecurityContextA+0x1fb() in secur32 (0x1f72e0b8)
  21 0x63030772 in wininet (+0x30771) (0x1f72e11c)
  22 0x63030591 in wininet (+0x30590) (0x1f72e198)
0xf76ff430 __kernel_vsyscall+0x10 in [vdso].so: popl    %ebp
Modules:
Module    Address            Debug info    Name (163 modules)
PE      400000-  416000    Deferred        lolclient
PE    10000000-114d1000    Deferred        adobe air
PE    1aac0000-1af57000    Deferred        webkit
PE    63000000-63072000    Export          wininet
PE    697a0000-6a7e4000    Deferred        npswf32
ELF    7937b000-793bc000    Deferred        usp10<elf>
  \-PE    79380000-793bc000    \               usp10
ELF    795bc000-7b800000    Deferred        libnvidia-glcore.so.331.38
ELF    7b800000-7ba4b000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba4b000    \               kernel32
ELF    7bac3000-7bb00000    Deferred        rsaenh<elf>
  \-PE    7bad0000-7bb00000    \               rsaenh
ELF    7bc00000-7bcd0000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcd0000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c01a000-7c033000    Deferred        cryptnet<elf>
  \-PE    7c020000-7c033000    \               cryptnet
ELF    7c033000-7c066000    Deferred        wintrust<elf>
  \-PE    7c040000-7c066000    \               wintrust
ELF    7c066000-7c080000    Deferred        rasapi32<elf>
  \-PE    7c070000-7c080000    \               rasapi32
ELF    7c5d3000-7c5ed000    Deferred        wsock32<elf>
  \-PE    7c5e0000-7c5ed000    \               wsock32
ELF    7c9c8000-7c9e5000    Deferred        libgcc_s.so.1
ELF    7c9e5000-7cae9000    Deferred        libgl.so.1
ELF    7cae9000-7cbce000    Deferred        opengl32<elf>
  \-PE    7cb10000-7cbce000    \               opengl32
ELF    7cbce000-7cd00000    Deferred        wined3d<elf>
  \-PE    7cbe0000-7cd00000    \               wined3d
ELF    7ce04000-7ce0b000    Deferred        libnss_dns.so.2
ELF    7ce6e000-7cea5000    Deferred        d3d9<elf>
  \-PE    7ce70000-7cea5000    \               d3d9
ELF    7cea5000-7ceae000    Deferred        libogg.so.0
ELF    7ceae000-7ceda000    Deferred        libvorbis.so.0
ELF    7ceda000-7d052000    Deferred        libvorbisenc.so.2
ELF    7d052000-7d086000    Deferred        libflac.so.8
ELF    7d086000-7d08d000    Deferred        libasyncns.so.0
ELF    7d08d000-7d0ff000    Deferred        libsndfile.so.1
ELF    7d0ff000-7d16e000    Deferred        libpulsecommon-4.0.so
ELF    7d16e000-7d1bd000    Deferred        libpulse.so.0
ELF    7d1bd000-7d2b3000    Deferred        libasound.so.2
ELF    7d2c2000-7d2c9000    Deferred        libasound_module_pcm_pulse.so
ELF    7d2d3000-7d300000    Deferred        winealsa<elf>
  \-PE    7d2e0000-7d300000    \               winealsa
ELF    7d401000-7d405000    Deferred        libnvidia-tls.so.331.38
ELF    7d405000-7d410000    Deferred        libjson-c.so.2
ELF    7d410000-7d430000    Deferred        mmdevapi<elf>
  \-PE    7d420000-7d430000    \               mmdevapi
ELF    7d430000-7d445000    Deferred        schannel<elf>
  \-PE    7d440000-7d445000    \               schannel
ELF    7d445000-7d467000    Deferred        imm32<elf>
  \-PE    7d450000-7d467000    \               imm32
ELF    7d467000-7d48d000    Deferred        mlang<elf>
  \-PE    7d470000-7d48d000    \               mlang
ELF    7d4e2000-7d540000    Deferred        dbghelp<elf>
  \-PE    7d4f0000-7d540000    \               dbghelp
ELF    7d540000-7d544000    Deferred        libgpg-error.so.0
ELF    7d544000-7d58f000    Deferred        libdbus-1.so.3
ELF    7d58f000-7d603000    Dwarf           libgcrypt.so.11
ELF    7d603000-7d613000    Deferred        libtasn1.so.3
ELF    7d613000-7d61f000    Deferred        libkrb5support.so.0
ELF    7d61f000-7d624000    Deferred        libcom_err.so.2
ELF    7d624000-7d654000    Deferred        libk5crypto.so.3
ELF    7d654000-7d712000    Deferred        libkrb5.so.3
ELF    7d712000-7d724000    Deferred        libavahi-client.so.3
ELF    7d724000-7d732000    Deferred        libavahi-common.so.3
ELF    7d732000-7d7ca000    Dwarf           libgnutls.so.26
ELF    7d7ca000-7d80f000    Deferred        libgssapi_krb5.so.2
ELF    7d80f000-7d87c000    Deferred        libcups.so.2
ELF    7d87c000-7d886000    Deferred        libwrap.so.0
ELF    7d889000-7d89c000    Deferred        psapi<elf>
  \-PE    7d890000-7d89c000    \               psapi
ELF    7d89c000-7d8e0000    Deferred        dsound<elf>
  \-PE    7d8a0000-7d8e0000    \               dsound
ELF    7d8e0000-7d8f8000    Deferred        libresolv.so.2
ELF    7d8fa000-7d918000    Deferred        dnsapi<elf>
  \-PE    7d900000-7d918000    \               dnsapi
ELF    7d918000-7d93c000    Deferred        iphlpapi<elf>
  \-PE    7d920000-7d93c000    \               iphlpapi
ELF    7d93c000-7d968000    Deferred        netapi32<elf>
  \-PE    7d940000-7d968000    \               netapi32
ELF    7d968000-7d996000    Dwarf           secur32<elf>
  \-PE    7d970000-7d996000    \               secur32
ELF    7d996000-7d9e3000    Deferred        liblcms2.so.2
ELF    7d9e3000-7da02000    Deferred        mscms<elf>
  \-PE    7d9f0000-7da02000    \               mscms
ELF    7da02000-7da41000    Deferred        winspool<elf>
  \-PE    7da10000-7da41000    \               winspool
ELF    7da41000-7db27000    Deferred        comdlg32<elf>
  \-PE    7da50000-7db27000    \               comdlg32
ELF    7db27000-7db56000    Deferred        oleacc<elf>
  \-PE    7db30000-7db56000    \               oleacc
ELF    7db56000-7db7e000    Deferred        msacm32<elf>
  \-PE    7db60000-7db7e000    \               msacm32
ELF    7db7e000-7dc31000    Deferred        winmm<elf>
  \-PE    7db90000-7dc31000    \               winmm
ELF    7dc31000-7dcf5000    Deferred        crypt32<elf>
  \-PE    7dc40000-7dcf5000    \               crypt32
ELF    7dcf5000-7dd27000    Deferred        ws2_32<elf>
  \-PE    7dd00000-7dd27000    \               ws2_32
ELF    7dd4a000-7dd7d000    Deferred        uxtheme<elf>
  \-PE    7dd50000-7dd7d000    \               uxtheme
ELF    7dd7d000-7dd83000    Deferred        libxfixes.so.3
ELF    7dd83000-7dd8e000    Deferred        libxcursor.so.1
ELF    7dd8e000-7dd9f000    Deferred        libxi.so.6
ELF    7dd9f000-7dda3000    Deferred        libxcomposite.so.1
ELF    7dda3000-7ddae000    Deferred        libxrandr.so.2
ELF    7ddae000-7ddb9000    Deferred        libxrender.so.1
ELF    7ddb9000-7ddbf000    Deferred        libxxf86vm.so.1
ELF    7ddbf000-7ddc3000    Deferred        libxinerama.so.1
ELF    7ddc3000-7ddca000    Deferred        libxdmcp.so.6
ELF    7ddca000-7ddce000    Deferred        libxau.so.6
ELF    7ddce000-7ddf0000    Deferred        libxcb.so.1
ELF    7ddf0000-7df24000    Deferred        libx11.so.6
ELF    7df24000-7df37000    Deferred        libxext.so.6
ELF    7df37000-7df3b000    Deferred        libkeyutils.so.1
ELF    7df3b000-7df4e000    Deferred        msimg32<elf>
  \-PE    7df40000-7df4e000    \               msimg32
ELF    7df57000-7dfe2000    Deferred        winex11<elf>
  \-PE    7df60000-7dfe2000    \               winex11
ELF    7e04c000-7e075000    Deferred        libexpat.so.1
ELF    7e075000-7e0b0000    Deferred        libfontconfig.so.1
ELF    7e0b0000-7e0d8000    Deferred        libpng12.so.0
ELF    7e0d8000-7e178000    Deferred        libfreetype.so.6
ELF    7e198000-7e1ac000    Deferred        libz.so.1
ELF    7e1ac000-7e1cb000    Deferred        cabinet<elf>
  \-PE    7e1b0000-7e1cb000    \               cabinet
ELF    7e1cb000-7e2c3000    Deferred        comctl32<elf>
  \-PE    7e1d0000-7e2c3000    \               comctl32
ELF    7e2c3000-7e3da000    Deferred        oleaut32<elf>
  \-PE    7e2e0000-7e3da000    \               oleaut32
ELF    7e3da000-7e454000    Deferred        rpcrt4<elf>
  \-PE    7e3f0000-7e454000    \               rpcrt4
ELF    7e454000-7e56b000    Deferred        ole32<elf>
  \-PE    7e470000-7e56b000    \               ole32
ELF    7e56b000-7e5fe000    Deferred        urlmon<elf>
  \-PE    7e580000-7e5fe000    \               urlmon
ELF    7e5fe000-7e6ea000    Deferred        msi<elf>
  \-PE    7e610000-7e6ea000    \               msi
ELF    7e6ea000-7e750000    Deferred        advapi32<elf>
  \-PE    7e700000-7e750000    \               advapi32
ELF    7e750000-7e85e000    Deferred        gdi32<elf>
  \-PE    7e760000-7e85e000    \               gdi32
ELF    7e85e000-7e9a6000    Deferred        user32<elf>
  \-PE    7e870000-7e9a6000    \               user32
ELF    7e9a6000-7ea16000    Deferred        shlwapi<elf>
  \-PE    7e9b0000-7ea16000    \               shlwapi
ELF    7ea16000-7ec33000    Deferred        shell32<elf>
  \-PE    7ea20000-7ec33000    \               shell32
ELF    7ec33000-7ec40000    Deferred        libnss_files.so.2
ELF    7ec40000-7ec4c000    Deferred        libnss_nis.so.2
ELF    7ec4c000-7ec65000    Deferred        libnsl.so.1
ELF    7ec65000-7ec6e000    Deferred        libnss_compat.so.2
ELF    7ec75000-7ec8e000    Deferred        version<elf>
  \-PE    7ec80000-7ec8e000    \               version
ELF    f72e5000-f72ee000    Deferred        librt.so.1
ELF    f72f0000-f7336000    Deferred        libm.so.6
ELF    f7336000-f733b000    Deferred        libdl.so.2
ELF    f733b000-f74eb000    Dwarf           libc.so.6
ELF    f74eb000-f7507000    Deferred        libpthread.so.0
ELF    f7528000-f76db000    Dwarf           libwine.so.1
ELF    f76dd000-f76ff000    Deferred        ld-linux.so.2
ELF    f76ff000-f7700000    Dwarf           [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000000b    0
    0000008e    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 rads_user_kernel.exe
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
    00000026    0
    00000021    0
00000023 explorer.exe
    00000024    0
0000002e LoLLauncher.exe
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
00000036 LoLPatcher.exe
    00000064    0
    00000065    0
    00000075    0
    00000074    0
    00000073    0
    00000051    0
    00000050    0
    0000004f    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    0000002d    0
    00000025    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
00000076 (D) C:\Riot Games\League of Legends\RADS\projects\lol_air_client\releases\0.0.1.107\deploy\LolClient.exe
    0000005f    0
    00000061    0 <==
    00000090    0
    0000005d    0
    0000005c    0
    00000095    0
    0000008f    0
    00000063    2
    00000022    0
    00000085    0
    00000086    0
    00000082    0
    00000081    0
    00000080    0
    0000007f    0
    0000007e    0
    0000007d    0
    0000007c    0
    0000007b    0
    0000007a    0
    00000079    0
    00000078    0
    00000077    0
System information:
    Wine build: wine-1.7.19
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-35-generic




Can someone help me please, i dont understand that the problems is, thanks !

---

