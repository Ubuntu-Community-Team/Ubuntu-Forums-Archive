---
title: "Steam suddenly stoped working (dont know what to do) Please help"
date: 2013-12-04
forum: Gaming &amp; Leisure
---

### Post by Marioaaj on 2013-12-04
Hello I am a new user to linux, I use ubuntu linux and today Steam suddenly stoped working. Steam was working just fine yestrday I tend to look at the problem before asking for help checking fourms if i find the problem but this time I have no idea what the problem is or how to look for it other then asking for help. I am using ubuntu 12.04 with navdia Geforce GTX 560M 2 GB as a grpahics card. Also there was a problem that poped up but I dont know how to read it. It came out as back trace when i saved it.
Help would Be appricated

BackTrace:```

Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc54942).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc54942 ESP:07dfb2c0 EBP:07dfb388 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:0000000c EBX:7bcaa518 ECX:00000000 EDX:00000010
 ESI:07dfb408 EDI:00000000
Stack dump:
0x07dfb2c0:  07dfb300 00000010 07dfb32c 00000020
0x07dfb2d0:  07dfb2f0 7bcaa518 07dfb348 7bc49e7b
0x07dfb2e0:  001f02f8 00110000 07dfb348 7bc49e7b
0x07dfb2f0:  00110060 00000020 00000000 0068af44
0x07dfb300:  00000000 0000000c 0000000c 00000000
0x07dfb310:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7bc54942 NtAdjustPrivilegesToken+0xc2() in ntdll (0x07dfb388)
  1 0x7e9dd290 AdjustTokenPrivileges+0x6f() in advapi32 (0x07dfb3d8)
  2 0x38234dae in steamclient (+0x234dad) (0x07dfb430)
  3 0x382358e4 in steamclient (+0x2358e3) (0x07dfb708)
  4 0x381e8d49 in steamclient (+0x1e8d48) (0x07dfb770)
  5 0x381eacf2 in steamclient (+0x1eacf1) (0x07dfb7a4)
  6 0x380ee459 in steamclient (+0xee458) (0x07dfb90c)
  7 0x380ef0cc in steamclient (+0xef0cb) (0x07dfcad0)
  8 0x3845e478 in steamclient (+0x45e477) (0x07dfcbe8)
  9 0x3845eda0 in steamclient (+0x45ed9f) (0x07dfcc38)
  10 0x380eef36 in steamclient (+0xeef35) (0x07dfde00)
  11 0x3849d807 in steamclient (+0x49d806) (0x07dfe210)
  12 0x3849da24 in steamclient (+0x49da23) (0x07dfe224)
  13 0x38450239 in steamclient (+0x450238) (0x07dfe448)
  14 0x3841c3c3 in steamclient (+0x41c3c2) (0x07dfe46c)
  15 0x3846201c in steamclient (+0x46201b) (0x07dfe478)
  16 0x38461ca3 in steamclient (+0x461ca2) (0x07dfe504)
  17 0x3819a222 in steamclient (+0x19a221) (0x07dfe574)
  18 0x3819a370 in steamclient (+0x19a36f) (0x07dfe588)
  19 0x3f00ca4f in tier0_s (+0xca4e) (0x07dfe5b8)
  20 0x3f00db0c in tier0_s (+0xdb0b) (0x07dfe5dc)
  21 0x3f011b70 in tier0_s (+0x11b6f) (0x07dfea18)
  22 0x7bc756b0 call_thread_func_wrapper+0xb() in ntdll (0x07dfea28)
  23 0x7bc7590d call_thread_func+0x7c() in ntdll (0x07dfeaf8)
  24 0x7bc7568e RtlRaiseException+0x21() in ntdll (0x07dfeb18)
  25 0x7bc7fd59 in ntdll (+0x6fd58) (0x07dff368)
  26 0xf765bd4c start_thread+0xcb() in libpthread.so.0 (0x07dff468)
0x7bc54942 NtAdjustPrivilegesToken+0xc2 in ntdll: movl    %edx,0x0(%edi)
Modules:
Module    Address            Debug info    Name (173 modules)
PE      400000-  63d000    Deferred        steam
PE      fd0000- 1087000    Deferred        sdl2
PE     42d0000- 43ea000    Deferred        chromehtml
PE     43f0000- 57cb000    Deferred        libcef
PE     7e00000- 810d000    Deferred        steamservice
PE    10000000-100b4000    Deferred        crashhandler
PE    30000000-302c1000    Deferred        steam
PE    38000000-38881000    Export          steamclient
PE    3a000000-3aaf4000    Deferred        steamui
PE    3f000000-3f0ac000    Export          tier0_s
PE    3f200000-3f2b1000    Deferred        vgui2_s
PE    3f600000-3f64b000    Deferred        vstdlib_s
PE    3f800000-3f82e000    Deferred        filesystem_stdio
PE    4ad00000-4b67f000    Deferred        icudt
PE    60000000-60021000    Deferred        cserhelper
PE    65ec0000-66072000    Deferred        avcodec-53
PE    68b80000-68ba7000    Deferred        avutil-51
PE    6ab00000-6ab33000    Deferred        avformat-53
ELF    7b800000-7b904000    Deferred        kernel32<elf>
  \-PE    7b810000-7b904000    \               kernel32
ELF    7bc00000-7bcc7000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc7000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c00f000-7c13c000    Deferred        wined3d<elf>
  \-PE    7c020000-7c13c000    \               wined3d
ELF    7c7e1000-7c7e8000    Deferred        libnss_dns.so.2
ELF    7c805000-7c828000    Deferred        dxgi<elf>
  \-PE    7c810000-7c828000    \               dxgi
ELF    7c828000-7c852000    Deferred        wbemprox<elf>
  \-PE    7c830000-7c852000    \               wbemprox
ELF    7c871000-7c9e9000    Deferred        libvorbisenc.so.2
ELF    7c9e9000-7ca37000    Deferred        libflac.so.8
ELF    7ca37000-7caa9000    Deferred        libsndfile.so.1
ELF    7caa9000-7cb0e000    Deferred        libpulsecommon-1.1.so
ELF    7cb0e000-7cc00000    Deferred        libasound.so.2
ELF    7cd03000-7cd0b000    Deferred        libogg.so.0
ELF    7cd0b000-7cd36000    Deferred        libvorbis.so.0
ELF    7cd36000-7cd40000    Deferred        libwrap.so.0
ELF    7cd40000-7cd48000    Deferred        libjson.so.0
ELF    7cd48000-7cd96000    Deferred        libpulse.so.0
ELF    7cd98000-7cdac000    Deferred        hid<elf>
  \-PE    7cda0000-7cdac000    \               hid
ELF    7cdac000-7cdb3000    Deferred        libasound_module_pcm_pulse.so
ELF    7cdb3000-7cde0000    Deferred        winealsa<elf>
  \-PE    7cdc0000-7cde0000    \               winealsa
ELF    7cde0000-7ce00000    Deferred        mmdevapi<elf>
  \-PE    7cdf0000-7ce00000    \               mmdevapi
ELF    7d102000-7d147000    Deferred        dsound<elf>
  \-PE    7d110000-7d147000    \               dsound
ELF    7d147000-7d184000    Deferred        rsaenh<elf>
  \-PE    7d150000-7d184000    \               rsaenh
ELF    7d184000-7d1a1000    Deferred        pdh<elf>
  \-PE    7d190000-7d1a1000    \               pdh
ELF    7d1a1000-7d1ba000    Deferred        imagehlp<elf>
  \-PE    7d1b0000-7d1ba000    \               imagehlp
ELF    7d345000-7d3dd000    Deferred        msvcrt<elf>
  \-PE    7d360000-7d3dd000    \               msvcrt
ELF    7d3dd000-7d41c000    Deferred        usp10<elf>
  \-PE    7d3e0000-7d41c000    \               usp10
ELF    7d41c000-7d430000    Deferred        dhcpcsvc<elf>
  \-PE    7d420000-7d430000    \               dhcpcsvc
ELF    7d430000-7d4c1000    Deferred        urlmon<elf>
  \-PE    7d440000-7d4c1000    \               urlmon
ELF    7d4c1000-7d52a000    Deferred        setupapi<elf>
  \-PE    7d4d0000-7d52a000    \               setupapi
ELF    7d52a000-7d600000    Deferred        opengl32<elf>
  \-PE    7d550000-7d600000    \               opengl32
ELF    7d702000-7d72c000    Deferred        netapi32<elf>
  \-PE    7d710000-7d72c000    \               netapi32
ELF    7d72c000-7d75a000    Deferred        secur32<elf>
  \-PE    7d730000-7d75a000    \               secur32
ELF    7d75a000-7d771000    Deferred        userenv<elf>
  \-PE    7d760000-7d771000    \               userenv
ELF    7d771000-7d7a9000    Deferred        winhttp<elf>
  \-PE    7d780000-7d7a9000    \               winhttp
ELF    7d7a9000-7d7cc000    Deferred        iphlpapi<elf>
  \-PE    7d7b0000-7d7cc000    \               iphlpapi
ELF    7d7cc000-7d7ea000    Deferred        libgcc_s.so.1
ELF    7d7ea000-7d7ee000    Deferred        libgpg-error.so.0
ELF    7d7ee000-7d806000    Deferred        libresolv.so.2
ELF    7d806000-7d80a000    Deferred        libkeyutils.so.1
ELF    7d80a000-7d853000    Deferred        libdbus-1.so.3
ELF    7d853000-7d8c7000    Deferred        libgcrypt.so.11
ELF    7d8c7000-7d8d7000    Deferred        libtasn1.so.3
ELF    7d8d7000-7d8ff000    Deferred        libk5crypto.so.3
ELF    7d8ff000-7d9ce000    Deferred        libkrb5.so.3
ELF    7d9ce000-7d9e0000    Deferred        libavahi-client.so.3
ELF    7d9e0000-7da78000    Deferred        libgnutls.so.26
ELF    7da78000-7dab6000    Deferred        libgssapi_krb5.so.2
ELF    7dab6000-7db09000    Deferred        libcups.so.2
ELF    7db09000-7db10000    Deferred        libasyncns.so.0
ELF    7db13000-7db26000    Deferred        msimg32<elf>
  \-PE    7db20000-7db26000    \               msimg32
ELF    7db26000-7db63000    Deferred        winspool<elf>
  \-PE    7db30000-7db63000    \               winspool
ELF    7db63000-7dc43000    Deferred        comdlg32<elf>
  \-PE    7db70000-7dc43000    \               comdlg32
ELF    7dc43000-7dd00000    Deferred        crypt32<elf>
  \-PE    7dc50000-7dd00000    \               crypt32
ELF    7de00000-7de09000    Deferred        libkrb5support.so.0
ELF    7de09000-7de17000    Deferred        libavahi-common.so.3
ELF    7de17000-7de3f000    Deferred        msacm32<elf>
  \-PE    7de20000-7de3f000    \               msacm32
ELF    7de3f000-7deef000    Deferred        winmm<elf>
  \-PE    7de50000-7deef000    \               winmm
ELF    7deef000-7df11000    Deferred        imm32<elf>
  \-PE    7df00000-7df11000    \               imm32
ELF    7df41000-7df9f000    Deferred        dbghelp<elf>
  \-PE    7df50000-7df9f000    \               dbghelp
ELF    7df9f000-7dfc4000    Deferred        mpr<elf>
  \-PE    7dfb0000-7dfc4000    \               mpr
ELF    7dfc4000-7e036000    Deferred        wininet<elf>
  \-PE    7dfd0000-7e036000    \               wininet
ELF    7e036000-7e069000    Deferred        uxtheme<elf>
  \-PE    7e040000-7e069000    \               uxtheme
ELF    7e069000-7e06f000    Deferred        libxfixes.so.3
ELF    7e06f000-7e07a000    Deferred        libxcursor.so.1
ELF    7e07a000-7e08a000    Deferred        libxi.so.6
ELF    7e08a000-7e08e000    Deferred        libxcomposite.so.1
ELF    7e08e000-7e097000    Deferred        libxrandr.so.2
ELF    7e097000-7e0a1000    Deferred        libxrender.so.1
ELF    7e0a1000-7e0a7000    Deferred        libxxf86vm.so.1
ELF    7e0a7000-7e0ab000    Deferred        libxinerama.so.1
ELF    7e0ab000-7e0af000    Deferred        libxau.so.6
ELF    7e0af000-7e0d4000    Deferred        libxcb.so.1
ELF    7e0d4000-7e0da000    Deferred        libuuid.so.1
ELF    7e0da000-7e20e000    Deferred        libx11.so.6
ELF    7e20e000-7e220000    Deferred        libxext.so.6
ELF    7e220000-7e23a000    Deferred        libice.so.6
ELF    7e23a000-7e243000    Deferred        libsm.so.6
ELF    7e246000-7e24b000    Deferred        libcom_err.so.2
ELF    7e24b000-7e25e000    Deferred        psapi<elf>
  \-PE    7e250000-7e25e000    \               psapi
ELF    7e260000-7e2eb000    Deferred        winex11<elf>
  \-PE    7e270000-7e2eb000    \               winex11
ELF    7e34e000-7e378000    Deferred        libexpat.so.1
ELF    7e378000-7e3ac000    Deferred        libfontconfig.so.1
ELF    7e3ac000-7e3c0000    Deferred        libz.so.1
ELF    7e3c0000-7e45a000    Deferred        libfreetype.so.6
ELF    7e477000-7e4ef000    Deferred        rpcrt4<elf>
  \-PE    7e480000-7e4ef000    \               rpcrt4
ELF    7e4ef000-7e603000    Deferred        ole32<elf>
  \-PE    7e510000-7e603000    \               ole32
ELF    7e603000-7e71e000    Deferred        oleaut32<elf>
  \-PE    7e620000-7e71e000    \               oleaut32
ELF    7e71e000-7e78d000    Deferred        shlwapi<elf>
  \-PE    7e730000-7e78d000    \               shlwapi
ELF    7e78d000-7e9a4000    Deferred        shell32<elf>
  \-PE    7e7a0000-7e9a4000    \               shell32
ELF    7e9a4000-7ea0a000    Dwarf           advapi32<elf>
  \-PE    7e9b0000-7ea0a000    \               advapi32
ELF    7ea0a000-7eb10000    Deferred        gdi32<elf>
  \-PE    7ea20000-7eb10000    \               gdi32
ELF    7eb10000-7ec55000    Deferred        user32<elf>
  \-PE    7eb20000-7ec55000    \               user32
ELF    7ec55000-7ed4b000    Deferred        comctl32<elf>
  \-PE    7ec60000-7ed4b000    \               comctl32
ELF    7ed4b000-7ed7b000    Deferred        ws2_32<elf>
  \-PE    7ed50000-7ed7b000    \               ws2_32
ELF    7ed7b000-7ed88000    Deferred        libnss_files.so.2
ELF    7ed88000-7ed94000    Deferred        libnss_nis.so.2
ELF    7ed94000-7edae000    Deferred        libnsl.so.1
ELF    7edae000-7edb7000    Deferred        libnss_compat.so.2
ELF    7efb7000-7efe3000    Deferred        libm.so.6
ELF    7efe8000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f74a5000-f74aa000    Deferred        libdl.so.2
ELF    f74aa000-f7654000    Dwarf           libc.so.6
ELF    f7655000-f7670000    Dwarf           libpthread.so.0
ELF    f7684000-f768d000    Deferred        librt.so.1
ELF    f768d000-f77ce000    Dwarf           libwine.so.1
ELF    f77d0000-f77f2000    Deferred        ld-linux.so.2
ELF    f77f2000-f77f3000    Deferred        [vdso].so
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
00000037 (D) C:\Program Files\Steam\Steam.exe
    00000033    0
    00000035    0
    0000003a    0
    00000036    0
    00000030    0
    00000031    0
    00000032    0
    00000029    0
    0000002d    0
    0000002b    0
    0000002a    0
    0000002c    0 <==
    00000017    0
    00000026    0
    00000027    0
    00000024    0
    00000009    0
    00000023    0
    0000000b    0
    0000000d    0
    0000000c    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000040    0
    0000003d    0
    0000003c    0
    00000038    0
```
System information:
    Wine build: wine-1.5.25
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-34-generic

---

### Post by dannyboy79 on 2013-12-04
is this steam for linux we're talking about? your back trace is weird because it mentions Wine at the end, which is an emulation layer to be able to run Windows executables in linux. are you trying to run windows version of steam within wine?

 Open a terminal window, try to launch steam from the terminal by just typing in ```
steam
``` what is the output that shows up in the terminal window? paste all the output at pastebin and then link to it here instead of posting all the output here like you did in your last post. It's generally best to use pastebin when you want to show others a ton of information, that way threads don't become gigantic on the forums (i'm not yelling at you just informing you so you know for next time) good luck

---

### Post by pdcant on 2013-12-04
You are not alone. There were messages on winehq.org for Steam, but they were deleted by the moderator. I learned from those posts that Steam rolled out an upgrade for the Windows version of Steam. Windows Steam under Wine gets to the login, but after that, it crashes and sends an error report to Steam. Hopefully, someone at Steam is watching those.

I can load and run games on the Linux version of Steam, but not the Windows version since yesterday. Winehq.org jumped to the conclusion that, since it was a Steam update, it is a Steam problem, despite the fact that Steam runs on Windows and not Wine.

For others, there are games available on Windows Steam that haven't been ported to Linux Steam yet. Until then, running Steam under Wine is a good solution. For now, it is now a bad option until either Steam or Wine makes changes.

---

### Post by pdcant on 2013-12-04
It became a formal bug on Wine: [http://bugs.winehq.org/show_bug.cgi?id=35030](http://bugs.winehq.org/show_bug.cgi?id=35030)

---

### Post by DanglingPointer on 2013-12-05
So this is Steam running in WINE?

---

### Post by pdcant on 2013-12-06
Download the latest version of Wine v1.7.8 because it fixes this problem. It was caused by a Steam update. Its just like Java and Adobe Reader needing to update after ever Windows update. Something changed causing the apps to fail.

Users of Linux Steam may ignore this problem. It was only Wine Steam users.

---

### Post by dannyboy79 on 2013-12-08
which begs the question, if there is a linux steam client why are you using a windows steam client in wine?

---

### Post by oldrocker99 on 2013-12-08
> 

    which begs the question, if there is a linux steam client why are you using a windows steam client in wine? 



Uh, I play Skyrim and Oblivion using the Windows Steam client which I installed using PlayOnLinux. That's one reason I can think of.

---

