---
title: "Eve Online: Captain's Quarters"
date: 2014-10-21
forum: Gaming &amp; Leisure
---

### Post by Urbanmasque on 2014-10-21
Hey guys,

So I've playing Eve Online without real issue once I got the appropriate NVidia 660 GeForce driver (331.38) on it. No real issues, but the only thing that my system seems to have a problem with is when I select "Enter Captains Quarters" which would give me the below view.

[IMG]http://images.mmorpg.com/images/newsImages/402011/EVE_t.jpg[/IMG]

The issue is everytime I try to enter the quaters I get the following Error.  I wanted a shot in the dark to see if someone would be able to help - I'm guessing a few of you may play or may have had some luck.

```

Error Message:
-----------------------------------------------------------------------------------------------------------------------------
Unhandled exception: page fault on write access to 0x00000018 in 32-bit code (0x08139551).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:08139551 ESP:0033adac EBP:0033ae9c EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:00000000 ECX:283a6c84 EDX:283a9564
 ESI:00000010 EDI:283a7a50
Stack dump:
0x0033adac:  283a6c84 0810e132 0033add4 283a9564
0x0033adbc:  00000000 283a7980 283a7a50 00000000
0x0033adcc:  00000000 081107cd 283a9564 0864c050
0x0033addc:  283a69e8 0811088d 283a69e8 0810e7c8
0x0033adec:  283a69e8 00007f44 283a69e8 0805b169
0x0033adfc:  0864c050 513d80be 00007f44 27fff160
Backtrace:
=>0 0x08139551 in _gameworld (+0x1c9551) (0x0033ae9c)
  1 0x0805b4ed in _gameworld (+0xeb4ec) (0x0033af54)
  2 0x07f8aa00 in _gameworld (+0x1a9ff) (0x0033af6c)
  3 0x07f94617 in _gameworld (+0x24616) (0x0033af98)
  4 0x07f947f0 in _gameworld (+0x247ef) (0x0033afa8)
  5 0x1e026a66 in python27 (+0x26a65) (0x117b0bf0)
0x08139551: movl    %edx,0x8(%esi)
Modules:
Module    Address            Debug info    Name (221 modules)
PE      350000-  3ef000    Deferred        d3dinfo.pyd
PE      400000-  48b000    Deferred        exefile
PE     4580000- 465d000    Deferred        _ssl.pyd
PE     4660000- 47a2000    Deferred        _audio2
PE     47b0000- 47ca000    Deferred        _vivox
PE     4910000- 54ff000    Deferred        _trinity_dx9_deploy
PE     5500000- 55ce000    Deferred        umbra
PE     55d0000- 5639000    Deferred        bink2w32
PE     5640000- 5653000    Deferred        physxloader
PE     5660000- 5757000    Deferred        apexframework_x86
PE     5760000- 5788000    Deferred        tbb
PE     7e10000- 7e4e000    Deferred        evelocalization
PE     7e50000- 7e7f000    Deferred        geo2
PE     7e80000- 7eb6000    Deferred        _yaml.pyd
PE     7ec0000- 7f36000    Deferred        pyfsd.pyd
PE     7f40000- 7f63000    Deferred        pyexpat.pyd
PE     7f70000- 86f9000    Export          _gameworld
PE     8700000- 8a76000    Deferred        physxcore
PE     8a80000- 8aca000    Deferred        cudart32_30_9
PE     8d00000- 8d64000    Deferred        physxcooking
PE     9110000- 9159000    Deferred        ortp
PE     9160000- 9172000    Deferred        pychartdir27.pyd
PE     9180000- 91aa000    Deferred        _planetresources
PE     9b10000- 9b2b000    Deferred        extensions
PE     9e10000- 9e6c000    Deferred        vivoxoal
PE     e6d0000- ed70000    Deferred        vivoxsdk
PE     ed70000- ee92000    Deferred        ccpbrowserhost.pyd
PE     f0c0000- f2f6000    Deferred        chartdir
PE     f410000- f48c000    Deferred        destiny
PE     f490000- f53b000    Deferred        unicodedata.pyd
PE     f540000- f5db000    Deferred        pyevepathfinder
PE     f5e0000- f603000    Deferred        _twitch
PE     f610000- f6ff000    Deferred        twitchsdk_32_release
PE    10000000-10328000    Deferred        blue
PE    1d1a0000-1d1b7000    Deferred        _ctypes.pyd
PE    1d550000-1d654000    Deferred        apex_clothing_x86
PE    1d770000-1d7bc000    Deferred        apex_framework_legacy_x86
PE    1d8d0000-1d980000    Deferred        apex_clothing_legacy_x86
PE    1e000000-1e3b0000    Export          python27
PE    65980000-6599d000    Deferred        swresample-ttv-0
PE    6eb80000-6ec09000    Deferred        libmp3lame-ttv
PE    6f140000-6f199000    Deferred        libsndfile-1
PE    70a40000-70a7a000    Deferred        avutil-ttv-51
PE    78aa0000-78b5f000    Deferred        msvcr100
ELF    7b800000-7ba60000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba60000    \               kernel32
ELF    7bc00000-7bce1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce1000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7d924000-7d94d000    Deferred        libexpat.so.1
ELF    7d94d000-7d988000    Deferred        libfontconfig.so.1
ELF    7d988000-7d9b0000    Deferred        libpng12.so.0
ELF    7d9b0000-7da50000    Deferred        libfreetype.so.6
ELF    7da50000-7da77000    Deferred        mpr<elf>
  \-PE    7da60000-7da77000    \               mpr
ELF    7da77000-7daf5000    Deferred        wininet<elf>
  \-PE    7da80000-7daf5000    \               wininet
ELF    7daf5000-7dc01000    Deferred        msvcp100<elf>
  \-PE    7db30000-7dc01000    \               msvcp100
ELF    7dc01000-7dc7b000    Deferred        shlwapi<elf>
  \-PE    7dc10000-7dc7b000    \               shlwapi
ELF    7dc7b000-7deb2000    Deferred        shell32<elf>
  \-PE    7dc90000-7deb2000    \               shell32
ELF    7deb2000-7deb9000    Deferred        libffi.so.6
ELF    7deb9000-7deea000    Deferred        libcrypt.so.1
ELF    7deea000-7dfa7000    Deferred        libsqlite3.so.0
ELF    7dfa7000-7dfee000    Deferred        libhx509.so.5
ELF    7dfee000-7dffd000    Deferred        libheimbase.so.1
ELF    7dffd000-7e026000    Deferred        libwind.so.0
ELF    7e026000-7e062000    Deferred        libp11-kit.so.0
ELF    7e062000-7e07b000    Deferred        libz.so.1
ELF    7e07b000-7e08d000    Deferred        libtasn1.so.3
ELF    7e08d000-7e0a3000    Deferred        libroken.so.18
ELF    7e0a3000-7e0d8000    Deferred        libhcrypto.so.4
ELF    7e0d8000-7e17e000    Deferred        libasn1.so.8
ELF    7e17e000-7e204000    Deferred        libkrb5.so.26
ELF    7e204000-7e20d000    Deferred        libheimntlm.so.0
ELF    7e20d000-7e294000    Deferred        libgcrypt.so.11
ELF    7e294000-7e35d000    Deferred        libgnutls.so.26
ELF    7e35d000-7e399000    Deferred        libgssapi.so.3
ELF    7e399000-7e3b4000    Deferred        libsasl2.so.2
ELF    7e3b4000-7e3c3000    Deferred        liblber-2.4.so.2
ELF    7e3c3000-7e415000    Deferred        libldap_r-2.4.so.2
ELF    7e433000-7e497000    Deferred        wldap32<elf>
  \-PE    7e440000-7e497000    \               wldap32
ELF    7e497000-7e51c000    Deferred        rpcrt4<elf>
  \-PE    7e4a0000-7e51c000    \               rpcrt4
ELF    7e51c000-7e65e000    Deferred        ole32<elf>
  \-PE    7e530000-7e65e000    \               ole32
ELF    7e65e000-7e7a1000    Deferred        oleaut32<elf>
  \-PE    7e680000-7e7a1000    \               oleaut32
ELF    7e7a1000-7e7dd000    Deferred        winhttp<elf>
  \-PE    7e7b0000-7e7dd000    \               winhttp
ELF    7e7dd000-7e7f5000    Deferred        libresolv.so.2
ELF    7e7f7000-7e813000    Deferred        jsproxy<elf>
  \-PE    7e800000-7e813000    \               jsproxy
ELF    7e813000-7e839000    Deferred        iphlpapi<elf>
  \-PE    7e820000-7e839000    \               iphlpapi
ELF    7e839000-7e8aa000    Deferred        advapi32<elf>
  \-PE    7e850000-7e8aa000    \               advapi32
ELF    7e8aa000-7e9c9000    Deferred        gdi32<elf>
  \-PE    7e8c0000-7e9c9000    \               gdi32
ELF    7e9c9000-7eb26000    Deferred        user32<elf>
  \-PE    7e9e0000-7eb26000    \               user32
ELF    7eb26000-7ebf7000    Deferred        crypt32<elf>
  \-PE    7eb30000-7ebf7000    \               crypt32
ELF    7ebf7000-7ec2e000    Deferred        ws2_32<elf>
  \-PE    7ec00000-7ec2e000    \               ws2_32
ELF    7ec2e000-7ec3b000    Deferred        libnss_files.so.2
ELF    7ec3b000-7ec47000    Deferred        libnss_nis.so.2
ELF    7ec47000-7ec60000    Deferred        libnsl.so.1
ELF    7ec60000-7ec69000    Deferred        libnss_compat.so.2
ELF    7efd9000-7efe2000    Deferred        librt.so.1
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f1a52000-f1a6f000    Deferred        libgcc_s.so.1
ELF    f3233000-f327b000    Deferred        dsound<elf>
  \-PE    f3240000-f327b000    \               dsound
ELF    f327b000-f3284000    Deferred        libogg.so.0
ELF    f3284000-f32b0000    Deferred        libvorbis.so.0
ELF    f32b0000-f3428000    Deferred        libvorbisenc.so.2
ELF    f3428000-f345c000    Deferred        libflac.so.8
ELF    f345c000-f3463000    Deferred        libasyncns.so.0
ELF    f3463000-f34d5000    Deferred        libsndfile.so.1
ELF    f34d5000-f34df000    Deferred        libwrap.so.0
ELF    f34df000-f354e000    Deferred        libpulsecommon-4.0.so
ELF    f354e000-f3559000    Deferred        libjson-c.so.2
ELF    f3559000-f35a8000    Deferred        libpulse.so.0
ELF    f35a8000-f369e000    Deferred        libasound.so.2
ELF    f36ae000-f36b5000    Deferred        libasound_module_pcm_pulse.so
ELF    f36bc000-f36ec000    Deferred        winealsa<elf>
  \-PE    f36c0000-f36ec000    \               winealsa
ELF    f36ec000-f370e000    Deferred        mmdevapi<elf>
  \-PE    f36f0000-f370e000    \               mmdevapi
ELF    f370e000-f372d000    Deferred        dnsapi<elf>
  \-PE    f3710000-f372d000    \               dnsapi
ELF    f372d000-f3740000    Deferred        sensapi<elf>
  \-PE    f3730000-f3740000    \               sensapi
ELF    f3740000-f37f2000    Deferred        msvcrt<elf>
  \-PE    f3760000-f37f2000    \               msvcrt
ELF    f37f2000-f3820000    Deferred        netapi32<elf>
  \-PE    f3800000-f3820000    \               netapi32
ELF    f3820000-f3864000    Deferred        usp10<elf>
  \-PE    f3830000-f3864000    \               usp10
ELF    f3864000-f38af000    Deferred        libdbus-1.so.3
ELF    f38af000-f38bb000    Deferred        libkrb5support.so.0
ELF    f38bb000-f3979000    Deferred        libkrb5.so.3
ELF    f3979000-f39be000    Deferred        libgssapi_krb5.so.2
ELF    f39be000-f3a2b000    Deferred        libcups.so.2
ELF    f3a2b000-f3b71000    Deferred        wined3d<elf>
  \-PE    f3a40000-f3b71000    \               wined3d
ELF    f3b71000-f3c79000    Deferred        comctl32<elf>
  \-PE    f3b80000-f3c79000    \               comctl32
ELF    f3d79000-f3da9000    Deferred        libk5crypto.so.3
ELF    f3da9000-f3ddf000    Deferred        uxtheme<elf>
  \-PE    f3db0000-f3ddf000    \               uxtheme
ELF    f3ddf000-f3e1c000    Deferred        d3d9<elf>
  \-PE    f3df0000-f3e1c000    \               d3d9
ELF    f3e1c000-f3f09000    Deferred        comdlg32<elf>
  \-PE    f3e20000-f3f09000    \               comdlg32
ELF    f3f09000-f3f7f000    Deferred        d3dcompiler_43<elf>
  \-PE    f3f10000-f3f7f000    \               d3dcompiler_43
ELF    f4678000-f467f000    Deferred        libnss_dns.so.2
ELF    f4815000-f4827000    Deferred        libavahi-client.so.3
ELF    f4827000-f4835000    Deferred        libavahi-common.so.3
ELF    f4835000-f48c5000    Deferred        d3dx9_36<elf>
  \-PE    f4840000-f48c5000    \               d3dx9_36
ELF    f48c5000-f48e9000    Deferred        imm32<elf>
  \-PE    f48d0000-f48e9000    \               imm32
ELF    f4aad000-f6cf1000    Deferred        libnvidia-glcore.so.331.38
ELF    f6cf1000-f6df5000    Deferred        libgl.so.1
ELF    f6df8000-f6e13000    Deferred        wsock32<elf>
  \-PE    f6e00000-f6e13000    \               wsock32
ELF    f6e13000-f6e19000    Deferred        libxfixes.so.3
ELF    f6e19000-f6e24000    Deferred        libxcursor.so.1
ELF    f6e24000-f6e35000    Deferred        libxi.so.6
ELF    f6e35000-f6e39000    Deferred        libxcomposite.so.1
ELF    f6e39000-f6e44000    Deferred        libxrandr.so.2
ELF    f6e44000-f6e4f000    Deferred        libxrender.so.1
ELF    f6e4f000-f6e55000    Deferred        libxxf86vm.so.1
ELF    f6e55000-f6e77000    Deferred        libxcb.so.1
ELF    f6e77000-f6fab000    Deferred        libx11.so.6
ELF    f6fab000-f6fbe000    Deferred        libxext.so.6
ELF    f6fd6000-f6fda000    Deferred        libnvidia-tls.so.331.38
ELF    f6fdc000-f706f000    Deferred        winex11<elf>
  \-PE    f6ff0000-f706f000    \               winex11
ELF    f706f000-f718a000    Deferred        opengl32<elf>
  \-PE    f7090000-f718a000    \               opengl32
ELF    f718d000-f71a1000    Deferred        d3d11<elf>
  \-PE    f7190000-f71a1000    \               d3d11
ELF    f71a6000-f71aa000    Deferred        libkeyutils.so.1
ELF    f71aa000-f71ec000    Deferred        winspool<elf>
  \-PE    f71b0000-f71ec000    \               winspool
ELF    f71ec000-f7212000    Deferred        d3dxof<elf>
  \-PE    f71f0000-f7212000    \               d3dxof
ELF    f7212000-f722b000    Deferred        d3dx9_42<elf>
  \-PE    f7220000-f722b000    \               d3dx9_42
ELF    f722b000-f7255000    Deferred        msacm32<elf>
  \-PE    f7230000-f7255000    \               msacm32
ELF    f7255000-f730d000    Deferred        winmm<elf>
  \-PE    f7260000-f730d000    \               winmm
ELF    f730d000-f7324000    Deferred        wtsapi32<elf>
  \-PE    f7310000-f7324000    \               wtsapi32
ELF    f7324000-f7366000    Deferred        rsaenh<elf>
  \-PE    f7330000-f7366000    \               rsaenh
ELF    f7366000-f7379000    Deferred        psapi<elf>
  \-PE    f7370000-f7379000    \               psapi
ELF    f7379000-f73e0000    Deferred        dbghelp<elf>
  \-PE    f7380000-f73e0000    \               dbghelp
ELF    f73e2000-f7428000    Deferred        libm.so.6
ELF    f7428000-f742d000    Deferred        libdl.so.2
ELF    f742d000-f75dd000    Deferred        libc.so.6
ELF    f75dd000-f75f9000    Deferred        libpthread.so.0
ELF    f75fb000-f7600000    Deferred        libgpg-error.so.0
ELF    f7601000-f7605000    Deferred        libxinerama.so.1
ELF    f7605000-f760c000    Deferred        libxdmcp.so.6
ELF    f760c000-f7610000    Deferred        libxau.so.6
ELF    f7612000-f7617000    Deferred        libcom_err.so.2
ELF    f7618000-f77ce000    Dwarf           libwine.so.1
ELF    f77d0000-f77f2000    Deferred        ld-linux.so.2
ELF    f77f2000-f77f3000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
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
00000020 explorer.exe
    00000021    0
0000003c (D) C:\Program Files\CCP\EVE\bin\exefile.exe
    00000038    0
    00000037    0
    00000036    0
    00000034    0
    00000032   15
    00000031    0
    00000030    0
    0000002f    0
    0000002e    0
    00000028    0
    0000005e    0
    00000067    0
    00000065   15
    00000064   15
    00000063   15
    00000062   15
    00000060    0
    0000005f    0
    0000005d    2
    0000005c    1
    0000005b   15
    0000005a    0
    00000059    0
    00000058    0
    00000057    0
    00000056    1
    00000055    0
    00000054    0
    00000053    0
    00000052    0
    00000051    0
    00000050    0
    0000004f    0
    0000004e    0
    0000004d    0
    0000004c    0
    0000004b    0
    0000004a    0
    00000049    0
    00000048    0
    0000002d    0
    0000002c    0
    00000009    0
    0000000b    0
    0000000d    0
    0000000c    0
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
    0000003d    0 <==
System information:
    Wine build: wine-1.7.28
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-37-generic
--------------------------------------------------------------------------------------

```
Any help would be greatly appreciated!

---

