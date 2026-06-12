---
title: "League of Legends problem when running on PlayOnLinux"
date: 2015-12-05
forum: Gaming &amp; Leisure
---

### Post by Ricardo_Velasco on 2015-12-05
Greeting:

Wanting install League of Legends or rather from a portable directory try to run this game on PlayOnLinux .

But a mistake which I get is as follows :

> Failed to launch RADS / system / rads_user_kernel.exe

I have this game in another partition ..

It will be possible to be in another partition will not run well the game? ..

Thank you

[IMG]http://i64.tinypic.com/303eark.png[/IMG]

---

### Post by r2rX on 2015-12-06
What file system is the other partition the game is located in? Just to test, copy LoL to your Ubuntu partition (your 'home' folder, for example) and try again.

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

Try copying the game to own Ubuntu partition and I came another mistake , I'll translate for you to understand :




```
The rads_user_kernel.exe program encountered a serious problem and needs to close. We apologize for any inconvenience .

This may be caused by a problem in the program or a deficiency in Wine. Maybe you want to check in Database Applications advice how to run this application.

```

Here I put the details of the problem:

```
Unhandled exception: unimplemented function msvcp80.dll.??0?$basic_stringstream@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@H@Z called in 32-bit code (0x7b839cf2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839cf2 ESP:0033f9b0 EBP:0033fa14 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b826245 EBX:7b894ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:00000008
Stack dump:
0x0033f9b0:  0033fa34 00000008 00000000 80000100
0x0033f9c0:  00000001 00000000 7b839cf2 00000002
0x0033f9d0:  7e9303a2 7e934ed1 4bb13f80 01d12fd2
0x0033f9e0:  fe7ead80 01d13065 4bb13f80 01d12fd2
0x0033f9f0:  ff14e56f 01d13065 00000020 7b83b68c
0x0033fa00:  00000018 00000000 7b839caa 00000010
Backtrace:
=>0 0x7b839cf2 in kernel32 (+0x29cf2) (0x0033fa14)
  1 0x7e930348 in msvcp80 (+0x20347) (0x0033fa44)
  2 0x7e921391 in msvcp80 (+0x11390) (0x0033fbf4)
  3 0x00452e01 in rads_user_kernel (+0x52e00) (0x0033fbf4)
  4 0x00452bf4 in rads_user_kernel (+0x52bf3) (0x7e7ce720)
  5 0x458b48ec (0x83e58955)
0x7b839cf2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (106 modules)
PE      400000-  53e000    Export          rads_user_kernel
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d6d8000-7d70c000    Deferred        uxtheme<elf>
  \-PE    7d6e0000-7d70c000    \               uxtheme
ELF    7d70c000-7d712000    Deferred        libxfixes.so.3
ELF    7d712000-7d71d000    Deferred        libxcursor.so.1
ELF    7d7ab000-7d7d5000    Deferred        libexpat.so.1
ELF    7d7d5000-7d809000    Deferred        libfontconfig.so.1
ELF    7d809000-7d81a000    Deferred        libxi.so.6
ELF    7d81a000-7d81e000    Deferred        libxcomposite.so.1
ELF    7d81e000-7d827000    Deferred        libxrandr.so.2
ELF    7d827000-7d831000    Deferred        libxrender.so.1
ELF    7d831000-7d837000    Deferred        libxxf86vm.so.1
ELF    7d837000-7d83b000    Deferred        libxinerama.so.1
ELF    7d83b000-7d85d000    Deferred        imm32<elf>
  \-PE    7d840000-7d85d000    \               imm32
ELF    7d85d000-7d864000    Deferred        libxdmcp.so.6
ELF    7d864000-7d868000    Deferred        libxau.so.6
ELF    7d868000-7d889000    Deferred        libxcb.so.1
ELF    7d889000-7d8a3000    Deferred        libice.so.6
ELF    7d8a3000-7d9d7000    Deferred        libx11.so.6
ELF    7d9d7000-7d9e9000    Deferred        libxext.so.6
ELF    7d9e9000-7d9f2000    Deferred        libsm.so.6
ELF    7d9f2000-7da85000    Deferred        winex11<elf>
  \-PE    7da00000-7da85000    \               winex11
ELF    7daa6000-7daac000    Deferred        libuuid.so.1
ELF    7daac000-7db47000    Deferred        libfreetype.so.6
ELF    7db47000-7db78000    Deferred        libcrypt.so.1
ELF    7db78000-7dc1d000    Deferred        libsqlite3.so.0
ELF    7dc1d000-7dc64000    Deferred        libhx509.so.5
ELF    7dc64000-7dc73000    Deferred        libheimbase.so.1
ELF    7dc73000-7dc9c000    Deferred        libwind.so.0
ELF    7dc9c000-7dcae000    Deferred        libp11-kit.so.0
ELF    7dcae000-7dcc0000    Deferred        libtasn1.so.3
ELF    7dcc0000-7dcd6000    Deferred        libroken.so.18
ELF    7dcd6000-7dd0b000    Deferred        libhcrypto.so.4
ELF    7dd0b000-7ddb0000    Deferred        libasn1.so.8
ELF    7ddb0000-7de33000    Deferred        libkrb5.so.26
ELF    7de33000-7de3b000    Deferred        libheimntlm.so.0
ELF    7de3b000-7dec1000    Deferred        libgcrypt.so.11
ELF    7dec1000-7df86000    Deferred        libgnutls.so.26
ELF    7df86000-7dfc3000    Deferred        libgssapi.so.3
ELF    7dfc3000-7dfdf000    Deferred        libsasl2.so.2
ELF    7dfdf000-7dff7000    Deferred        libresolv.so.2
ELF    7dff7000-7e006000    Deferred        liblber-2.4.so.2
ELF    7e006000-7e058000    Deferred        libldap_r-2.4.so.2
ELF    7e058000-7e0b4000    Deferred        wldap32<elf>
  \-PE    7e060000-7e0b4000    \               wldap32
ELF    7e0b4000-7e0dc000    Deferred        msacm32<elf>
  \-PE    7e0c0000-7e0dc000    \               msacm32
ELF    7e0dc000-7e151000    Deferred        rpcrt4<elf>
  \-PE    7e0f0000-7e151000    \               rpcrt4
ELF    7e151000-7e259000    Deferred        ole32<elf>
  \-PE    7e170000-7e259000    \               ole32
ELF    7e259000-7e306000    Deferred        winmm<elf>
  \-PE    7e260000-7e306000    \               winmm
ELF    7e306000-7e3fe000    Deferred        comctl32<elf>
  \-PE    7e310000-7e3fe000    \               comctl32
ELF    7e3fe000-7e60f000    Deferred        shell32<elf>
  \-PE    7e410000-7e60f000    \               shell32
ELF    7e60f000-7e679000    Deferred        shlwapi<elf>
  \-PE    7e620000-7e679000    \               shlwapi
ELF    7e679000-7e69f000    Deferred        mpr<elf>
  \-PE    7e680000-7e69f000    \               mpr
ELF    7e69f000-7e6b5000    Deferred        libz.so.1
ELF    7e6cc000-7e73b000    Deferred        wininet<elf>
  \-PE    7e6e0000-7e73b000    \               wininet
ELF    7e73b000-7e76a000    Deferred        msvcr90<elf>
  \-PE    7e740000-7e76a000    \               msvcr90
ELF    7e76a000-7e795000    Deferred        msvcr80<elf>
  \-PE    7e770000-7e795000    \               msvcr80
ELF    7e795000-7e822000    Deferred        msvcrt<elf>
  \-PE    7e7b0000-7e822000    \               msvcrt
ELF    7e822000-7e907000    Deferred        msvcp90<elf>
  \-PE    7e840000-7e907000    \               msvcp90
ELF    7e907000-7e9b0000    Dwarf           msvcp80<elf>
  \-PE    7e910000-7e9b0000    \               msvcp80
ELF    7e9b0000-7e9c9000    Deferred        version<elf>
  \-PE    7e9c0000-7e9c9000    \               version
ELF    7e9c9000-7ea29000    Deferred        advapi32<elf>
  \-PE    7e9d0000-7ea29000    \               advapi32
ELF    7ea29000-7eae6000    Deferred        gdi32<elf>
  \-PE    7ea40000-7eae6000    \               gdi32
ELF    7eae6000-7ec26000    Deferred        user32<elf>
  \-PE    7eb00000-7ec26000    \               user32
ELF    7ec26000-7ec58000    Deferred        ws2_32<elf>
  \-PE    7ec30000-7ec58000    \               ws2_32
ELF    7ec58000-7ec65000    Deferred        libnss_files.so.2
ELF    7ec65000-7ec71000    Deferred        libnss_nis.so.2
ELF    7ec71000-7ec8b000    Deferred        libnsl.so.1
ELF    7efbd000-7efe9000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        psapi<elf>
  \-PE    7eff0000-7f000000    \               psapi
ELF    b7410000-b7415000    Deferred        libgpg-error.so.0
ELF    b7415000-b741e000    Deferred        libnss_compat.so.2
ELF    b741f000-b7424000    Deferred        libdl.so.2
ELF    b7424000-b75cd000    Deferred        libc.so.6
ELF    b75ce000-b75e9000    Deferred        libpthread.so.0
ELF    b75eb000-b75f0000    Deferred        libcom_err.so.2
ELF    b7600000-b7742000    Dwarf           libwine.so.1
ELF    b7744000-b7766000    Deferred        ld-linux.so.2
ELF    b7766000-b7767000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000018    0
    00000017    0
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
00000021 (D) Z:\home\ricardo\League of Legends\RADS\system\rads_user_kernel.exe
    00000023    0
    00000022    0 <==
00000024 explorer.exe
    00000025    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-71-generic

```


Thank You

---

### Post by mastablasta on 2015-12-07
and? did you check the wine appdb? I wouldn't bother with game much: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=31794](https://appdb.winehq.org/objectManager.php?sClass=version&iId=31794)


though it seem like it will work with a workarround, the issue is that the next patch might make it useless work. and they patch it at least once a week.

would be good if they had a Linux version.

---

### Post by Ricardo_Velasco on 2015-12-13
Greeting:

It seems I found the problem , had to upgrade wine, but I get this error.

[IMG]http://i68.tinypic.com/iokrko.png[/IMG]

---

