---
title: "Dark Souls 2 not starting"
date: 2014-12-19
forum: Gaming &amp; Leisure
---

### Post by IDOMATH on 2014-12-19
I have a windows steam installed with Wine and when I try to start Dark Souls 2, I get this

Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00d6fb9d).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00d6fb9d ESP:0033f8f8 EBP:0033f908 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:8876086a EBX:00000000 ECX:0033f8ec EDX:00000001
 ESI:00000000 EDI:0514d3d8
Stack dump:
0x0033f8f8:  0033fa20 0514c120 0033f9d0 0514a0c0
0x0033f908:  0033f9c0 0084ea88 00000500 0514c110
0x0033f918:  00000000 00000000 00000001 40000000
0x0033f928:  00000000 00000140 00000140 ff808080
0x0033f938:  00000000 00000280 00000168 00000006
0x0033f948:  00000016 00000000 0630eba0 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x00d6fb9d in darksoulsii (+0x96fb9d) (0x0033f908)
  1 0x0084ea88 in darksoulsii (+0x44ea87) (0x0033f9c0)
  2 0x00853854 in darksoulsii (+0x453853) (0x0033fa50)
  3 0x006cb8a1 in darksoulsii (+0x2cb8a0) (0x0033fae8)
  4 0x00d2b713 in darksoulsii (+0x92b712) (0x0033fb60)
  5 0x006ca854 in darksoulsii (+0x2ca853) (0x0033fdd0)
  6 0x00e2a855 in darksoulsii (+0xa2a854) (0x0033fe60)
  7 0x7b85e5cc call_process_entry+0xb() in kernel32 (0x0033fe78)
  8 0x7b85f653 in kernel32 (+0x4f652) (0x0033feb8)
  9 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  10 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  11 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  12 0x7bc4e8fe call_dll_entry_point+0x7ed() in ntdll (0x0033ffe8)
  13 0xf75bf50d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  14 0xf75bf5cb wine_switch_to_stack+0x2a() in libwine.so.1 (0xffdb6928)
  15 0x7bc541e2 LdrInitializeThunk+0x3a1() in ntdll (0xffdb6988)
  16 0x7b865bdd __wine_kernel_init+0xa0c() in kernel32 (0xffdb7aa8)
  17 0x7bc547a3 __wine_process_init+0x192() in ntdll (0xffdb7b38)
  18 0xf75bcc70 wine_init+0x30f() in libwine.so.1 (0xffdb7b98)
  19 0x7bf00fdc main+0xfb() in <wine-loader> (0xffdb7fe8)
  20 0xf73e1a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x00d6fb9d: movl    0x0(%esi),%eax
Modules:
Module    Address            Debug info    Name (141 modules)
PE      340000-  3ac000    Deferred        fmod_event
PE      3b0000-  3c6000    Deferred        xinput1_3
PE      400000- 1769000    Export          darksoulsii
PE     1770000- 196f000    Deferred        d3dx9_43
PE     c900000- c9d1000    Deferred        steam
PE    10000000-10151000    Deferred        fmodex
PE    30000000-302c1000    Deferred        steam2
PE    38000000-38935000    Deferred        steamclient
PE    3b400000-3b41d000    Deferred        steam_api
PE    3f000000-3f0b0000    Deferred        tier0_s
PE    3f600000-3f651000    Deferred        vstdlib_s
PE    60000000-60021000    Deferred        cserhelper
ELF    79afa000-7b800000    Deferred        libnvidia-glcore.so.304.125
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7ba88000-7bc00000    Deferred        libvorbisenc.so.2
ELF    7bc00000-7bcdb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bd8e000-7be00000    Deferred        libsndfile.so.1
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7bf0d000-7bf25000    Deferred        libresolv.so.2
ELF    7bf25000-7bf51000    Deferred        libvorbis.so.0
ELF    7c412000-7c446000    Deferred        libflac.so.8
ELF    7c446000-7c491000    Deferred        libdbus-1.so.3
ELF    7c491000-7c500000    Deferred        libpulsecommon-4.0.so
ELF    7c604000-7c653000    Deferred        libpulse.so.0
ELF    7c859000-7c862000    Deferred        libogg.so.0
ELF    7c862000-7c86b000    Deferred        librt.so.1
ELF    7c86b000-7c893000    Deferred        winepulse<elf>
  \-PE    7c870000-7c893000    \               winepulse
ELF    7c893000-7c8b5000    Deferred        mmdevapi<elf>
  \-PE    7c8a0000-7c8b5000    \               mmdevapi
ELF    7c90d000-7c934000    Deferred        dxgi<elf>
  \-PE    7c910000-7c934000    \               dxgi
ELF    7c934000-7c966000    Deferred        wbemprox<elf>
  \-PE    7c940000-7c966000    \               wbemprox
ELF    7c966000-7c9b1000    Deferred        dinput<elf>
  \-PE    7c970000-7c9b1000    \               dinput
ELF    7c9b1000-7ca19000    Deferred        dbghelp<elf>
  \-PE    7c9c0000-7ca19000    \               dbghelp
ELF    7ca19000-7ca36000    Deferred        libgcc_s.so.1
ELF    7ca37000-7ca3e000    Deferred        libasyncns.so.0
ELF    7ca3e000-7ca48000    Deferred        libwrap.so.0
ELF    7ca48000-7ca53000    Deferred        libjson-c.so.2
ELF    7ca53000-7ca83000    Deferred        p11-kit-trust.so
ELF    7ca83000-7ca8a000    Deferred        libffi.so.6
ELF    7ca8a000-7cb50000    Deferred        libgnutls.so.26
ELF    7cc50000-7cc8c000    Deferred        libp11-kit.so.0
ELF    7cc8c000-7cd13000    Deferred        libgcrypt.so.11
ELF    7cd13000-7cde2000    Deferred        crypt32<elf>
  \-PE    7cd20000-7cde2000    \               crypt32
ELF    7d670000-7d675000    Deferred        libgpg-error.so.0
ELF    7d675000-7d689000    Deferred        libtasn1.so.6
ELF    7d693000-7d6a6000    Deferred        gnome-keyring-pkcs11.so
ELF    7d6a6000-7d6d3000    Deferred        netapi32<elf>
  \-PE    7d6b0000-7d6d3000    \               netapi32
ELF    7d6d3000-7d706000    Deferred        secur32<elf>
  \-PE    7d6e0000-7d706000    \               secur32
ELF    7d706000-7d720000    Deferred        imagehlp<elf>
  \-PE    7d710000-7d720000    \               imagehlp
ELF    7d720000-7d745000    Deferred        imm32<elf>
  \-PE    7d730000-7d745000    \               imm32
ELF    7d80c000-7d8e8000    Deferred        libgl.so.1
ELF    7d905000-7d93c000    Deferred        uxtheme<elf>
  \-PE    7d910000-7d93c000    \               uxtheme
ELF    7d93c000-7d942000    Deferred        libxfixes.so.3
ELF    7d942000-7d94d000    Deferred        libxcursor.so.1
ELF    7d94d000-7d95e000    Deferred        libxi.so.6
ELF    7d95e000-7d962000    Deferred        libxcomposite.so.1
ELF    7d962000-7d96d000    Deferred        libxrandr.so.2
ELF    7d96d000-7d978000    Deferred        libxrender.so.1
ELF    7d978000-7d97e000    Deferred        libxxf86vm.so.1
ELF    7d97e000-7d982000    Deferred        libxinerama.so.1
ELF    7d982000-7d989000    Deferred        libxdmcp.so.6
ELF    7d989000-7d98d000    Deferred        libxau.so.6
ELF    7d98d000-7d9af000    Deferred        libxcb.so.1
ELF    7d9af000-7dae3000    Deferred        libx11.so.6
ELF    7dae3000-7daf6000    Deferred        libxext.so.6
ELF    7daf9000-7dafd000    Deferred        libnvidia-tls.so.304.125
ELF    7dafd000-7db11000    Deferred        psapi<elf>
  \-PE    7db00000-7db11000    \               psapi
ELF    7db13000-7dba5000    Deferred        winex11<elf>
  \-PE    7db20000-7dba5000    \               winex11
ELF    7dbe1000-7dc0a000    Deferred        libexpat.so.1
ELF    7dc0a000-7dc45000    Deferred        libfontconfig.so.1
ELF    7dc45000-7dc6d000    Deferred        libpng12.so.0
ELF    7dc6d000-7dc87000    Deferred        libz.so.1
ELF    7dc87000-7dd27000    Deferred        libfreetype.so.6
ELF    7dd44000-7de7a000    Deferred        oleaut32<elf>
  \-PE    7dd60000-7de7a000    \               oleaut32
ELF    7de7a000-7deeb000    Deferred        setupapi<elf>
  \-PE    7de80000-7deeb000    \               setupapi
ELF    7deeb000-7df07000    Deferred        dinput8<elf>
  \-PE    7def0000-7df07000    \               dinput8
ELF    7df07000-7e00e000    Deferred        comctl32<elf>
  \-PE    7df10000-7e00e000    \               comctl32
ELF    7e00e000-7e088000    Deferred        shlwapi<elf>
  \-PE    7e020000-7e088000    \               shlwapi
ELF    7e088000-7e2bb000    Deferred        shell32<elf>
  \-PE    7e0a0000-7e2bb000    \               shell32
ELF    7e2bb000-7e363000    Deferred        msvcrt<elf>
  \-PE    7e2d0000-7e363000    \               msvcrt
ELF    7e363000-7e472000    Deferred        opengl32<elf>
  \-PE    7e380000-7e472000    \               opengl32
ELF    7e472000-7e5b2000    Deferred        wined3d<elf>
  \-PE    7e480000-7e5b2000    \               wined3d
ELF    7e5b2000-7e5ef000    Deferred        d3d9<elf>
  \-PE    7e5c0000-7e5ef000    \               d3d9
ELF    7e5ef000-7e615000    Deferred        iphlpapi<elf>
  \-PE    7e600000-7e615000    \               iphlpapi
ELF    7e615000-7e631000    Deferred        wsock32<elf>
  \-PE    7e620000-7e631000    \               wsock32
ELF    7e631000-7e667000    Deferred        ws2_32<elf>
  \-PE    7e640000-7e667000    \               ws2_32
ELF    7e667000-7e692000    Deferred        msacm32<elf>
  \-PE    7e670000-7e692000    \               msacm32
ELF    7e692000-7e713000    Deferred        rpcrt4<elf>
  \-PE    7e6a0000-7e713000    \               rpcrt4
ELF    7e713000-7e84f000    Deferred        ole32<elf>
  \-PE    7e730000-7e84f000    \               ole32
ELF    7e84f000-7e8c1000    Deferred        advapi32<elf>
  \-PE    7e860000-7e8c1000    \               advapi32
ELF    7e8c1000-7e9de000    Deferred        gdi32<elf>
  \-PE    7e8d0000-7e9de000    \               gdi32
ELF    7e9de000-7eb38000    Deferred        user32<elf>
  \-PE    7e9f0000-7eb38000    \               user32
ELF    7eb38000-7ebf2000    Deferred        winmm<elf>
  \-PE    7eb40000-7ebf2000    \               winmm
ELF    7ebf2000-7ebff000    Deferred        libnss_files.so.2
ELF    7ebff000-7ec0b000    Deferred        libnss_nis.so.2
ELF    7ec0b000-7ec24000    Deferred        libnsl.so.1
ELF    7ec24000-7ec2d000    Deferred        libnss_compat.so.2
ELF    7ef9d000-7efe3000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73c8000-f7577000    Dwarf           libc.so.6
ELF    f7577000-f757c000    Deferred        libdl.so.2
ELF    f757d000-f7599000    Deferred        libpthread.so.0
ELF    f75b6000-f776b000    Dwarf           libwine.so.1
ELF    f776d000-f778f000    Deferred        ld-linux.so.2
ELF    f778f000-f7790000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
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
    0000006a    0
    0000008b    0
    00000088    0
    00000081    0
    0000005d    0
    0000005c    0
    0000005b    0
    00000058    0
    00000057    0
    00000056    0
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
    0000004b   15
    0000004a    0
    00000049    0
    00000048    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    0000002a    0
    00000029    0
    00000025    0
0000002b steamwebhelper.exe
    00000026    0
    00000069    0
    00000093    0
    0000006e    0
    0000008e    0
    00000068    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
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
0000005e steamwebhelper.exe
    0000007c    0
    0000007b    0
    00000046    0
    0000000b    0
    00000067    0
    00000066    0
    00000065    0
    00000064    0
    00000063    0
    00000062    0
    00000061    0
    00000060    0
    0000005f    0
00000070 (D) C:\Program Files (x86)\Steam\steamapps\common\Dark Souls II\Game\DarkSoulsII.exe
    00000082    2
    0000005a    2
    00000083   15
    0000007f    0
    0000007e    0
    00000080    0
    0000007d   15
    00000047    1
    00000009    0
    0000006b    0
    0000006c   -1
    00000075    0
    00000073    0
    00000072    0
    00000071    0 <==
0000008f steamwebhelper.exe
    00000077    0
    0000006d    0
    0000008c    0
    00000089    0
    0000008a    0
    00000074    0
    00000079    0
    0000006f    0
    00000076    0
    00000096    0
    00000094    0
    00000090    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-43-generic


I am new to Ubuntu and have no idea what this means. All help is appreciated!

---

