---
title: "Neverwinter Nights 2 complete crush"
date: 2014-04-19
forum: Gaming &amp; Leisure
---

### Post by pawe4 on 2014-04-19
Hi
I am currently trying to launch neverwinter nights 2 complete to play with my brother. Unfortunetly after succsessful installation nwn crash when its trying to launch new game. i can choose campaing, and hero, but when the game is loading nwn crashes. I have done everything what is said on [http://ubuntuforums.org/showthread.php?t=2195996](http://ubuntuforums.org/showthread.php?t=2195996), but it still doesnt work. I have the crash register copied:
Unhandled exception: assertion failed in 32-bit code (0xf779e430).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f779e430 ESP:0033edd4 EBP:eca2dc08 EFLAGS:00000296(   - --  I S -A-P- )
 EAX:00000000 EBX:00002c2e ECX:00002c2e EDX:00000006
 ESI:ec7d1df8 EDI:f75feff4
Stack dump:
0x0033edd4:  eca2dc08 00000006 00002c2e f74871df
0x0033ede4:  f75feff4 0033ef10 f748a825 00000006
0x0033edf4:  0033ee90 00000000 f1fb1f7b 00000000
0x0033ee04:  ec782748 00000023 f2134ff4 ec83dc98
0x0033ee14:  00000004 f2134ff4 f1fbf58b 00000070
0x0033ee24:  00002710 00000010 f75ff470 f75ff478
Backtrace:
=>0 0xf779e430 __kernel_vsyscall+0x10() in [vdso].so (0xeca2dc08)
  1 0xf74871df gsignal+0x4e() in libc.so.6 (0xeca2dc08)
  2 0xf748a825 abort+0x174() in libc.so.6 (0xeca2dc08)
  3 0xf1fc2288 in nouveau_dri.so (+0x92287) (0xeca2dc08)
  4 0xf1fc2ff3 nv_pc_exec_pass1+0x162() in nouveau_dri.so (0xeca04668)
  5 0xf1fb228c nv50_generate_code+0x16b() in nouveau_dri.so (0x00000017)
  6 0xf1fafe24 nv50_program_translate+0xe43() in nouveau_dri.so (0x00000017)
  7 0xf1fb0400 in nouveau_dri.so (+0x803ff) (0x001f028f)
  8 0xf1fb0974 nv50_vertprog_validate+0x33() in nouveau_dri.so (0x001f028f)
  9 0xf1fac9f4 nv50_state_validate+0x133() in nouveau_dri.so (0x001f028f)
  10 0xf1fadb46 nv50_draw_vbo+0xd5() in nouveau_dri.so (0x00000000)
  11 0xf19033ca st_draw_vbo+0x7c9() in libgallium.so (0x0033f5bc)
  12 0xf1dc8c8d in libdricore.so (+0x112c8c) (0x00000000)
  13 0xf1dc8fbd in libdricore.so (+0x112fbc) (0x00000000)
  14 0x7e435131 in wined3d (+0x55130) (0x0033f8c8)
  15 0x7e41caef wined3d_device_draw_indexed_primitive+0xbe() in wined3d (0x0033f918)
  16 0x7e514eba in d3d9 (+0x14eb9) (0x0033f96c)
0xf779e430 __kernel_vsyscall+0x10 in [vdso].so: popl	%ebp
Modules:
Module	Address			Debug info	Name (161 modules)
PE	  400000-  b31000	Export          nwn2main
PE	  b40000-  da0000	Deferred        d3dx9_30
PE	 3f30000- 40e5000	Deferred        dxdiagn
PE	10000000-10015000	Deferred        nwn2_memorymgr
PE	21100000-21164000	Deferred        mss32
PE	22300000-22338000	Deferred        msseax.m3d
PE	22400000-22419000	Deferred        msssoft.m3d
PE	22600000-22618000	Deferred        mssdx7.m3d
PE	22700000-22776000	Deferred        mssrsx.m3d
PE	24100000-24120000	Deferred        mssdsp.flt
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	30000000-3006d000	Deferred        binkw32
PE	50000000-50090000	Deferred        granny2
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b904000	Deferred        kernel32<elf>
  \-PE	7b810000-7b904000	\               kernel32
ELF	7bc00000-7bcc7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc7000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7da9b000-7dace000	Deferred        uxtheme<elf>
  \-PE	7daa0000-7dace000	\               uxtheme
ELF	7dace000-7dad4000	Deferred        libxfixes.so.3
ELF	7dad4000-7dadf000	Deferred        libxcursor.so.1
ELF	7dadf000-7daf0000	Deferred        libxi.so.6
ELF	7daf0000-7daf4000	Deferred        libxcomposite.so.1
ELF	7daf4000-7dafd000	Deferred        libxrandr.so.2
ELF	7dafd000-7db07000	Deferred        libxrender.so.1
ELF	7db07000-7db0d000	Deferred        libxxf86vm.so.1
ELF	7db0d000-7db11000	Deferred        libxinerama.so.1
ELF	7db11000-7db15000	Deferred        libxau.so.6
ELF	7db15000-7db3a000	Deferred        libxcb.so.1
ELF	7db3a000-7db40000	Deferred        libuuid.so.1
ELF	7db40000-7dc74000	Deferred        libx11.so.6
ELF	7dc74000-7dc86000	Deferred        libxext.so.6
ELF	7dc86000-7dca0000	Deferred        libice.so.6
ELF	7dca0000-7dca9000	Deferred        libsm.so.6
ELF	7dcc3000-7dd4e000	Deferred        winex11<elf>
  \-PE	7dcd0000-7dd4e000	\               winex11
ELF	7dd9d000-7ddc7000	Deferred        libexpat.so.1
ELF	7ddc7000-7ddfb000	Deferred        libfontconfig.so.1
ELF	7ddfb000-7de95000	Deferred        libfreetype.so.6
ELF	7deaf000-7dfca000	Deferred        oleaut32<elf>
  \-PE	7ded0000-7dfca000	\               oleaut32
ELF	7dfca000-7e0c0000	Deferred        comctl32<elf>
  \-PE	7dfd0000-7e0c0000	\               comctl32
ELF	7e0c0000-7e2d7000	Deferred        shell32<elf>
  \-PE	7e0d0000-7e2d7000	\               shell32
ELF	7e2d7000-7e2f9000	Deferred        imm32<elf>
  \-PE	7e2e0000-7e2f9000	\               imm32
ELF	7e2f9000-7e3cf000	Deferred        opengl32<elf>
  \-PE	7e310000-7e3cf000	\               opengl32
ELF	7e3cf000-7e4fc000	Dwarf           wined3d<elf>
  \-PE	7e3e0000-7e4fc000	\               wined3d
ELF	7e4fc000-7e532000	Dwarf           d3d9<elf>
  \-PE	7e500000-7e532000	\               d3d9
ELF	7e532000-7e54d000	Deferred        dinput8<elf>
  \-PE	7e540000-7e54d000	\               dinput8
ELF	7e54d000-7e5bc000	Deferred        shlwapi<elf>
  \-PE	7e560000-7e5bc000	\               shlwapi
ELF	7e5bc000-7e655000	Deferred        msvcrt<elf>
  \-PE	7e5d0000-7e655000	\               msvcrt
ELF	7e655000-7e686000	Deferred        ws2_32<elf>
  \-PE	7e660000-7e686000	\               ws2_32
ELF	7e686000-7e699000	Deferred        psapi<elf>
  \-PE	7e690000-7e699000	\               psapi
ELF	7e699000-7e6ad000	Deferred        libz.so.1
ELF	7e6ad000-7e70a000	Deferred        dbghelp<elf>
  \-PE	7e6b0000-7e70a000	\               dbghelp
ELF	7e72e000-7e756000	Deferred        msacm32<elf>
  \-PE	7e730000-7e756000	\               msacm32
ELF	7e756000-7e7ce000	Deferred        rpcrt4<elf>
  \-PE	7e760000-7e7ce000	\               rpcrt4
ELF	7e7ce000-7e8e2000	Deferred        ole32<elf>
  \-PE	7e7f0000-7e8e2000	\               ole32
ELF	7e8e2000-7e948000	Deferred        advapi32<elf>
  \-PE	7e8f0000-7e948000	\               advapi32
ELF	7e948000-7ea4e000	Deferred        gdi32<elf>
  \-PE	7e950000-7ea4e000	\               gdi32
ELF	7ea4e000-7eb93000	Deferred        user32<elf>
  \-PE	7ea60000-7eb93000	\               user32
ELF	7eb93000-7ec43000	Deferred        winmm<elf>
  \-PE	7eba0000-7ec43000	\               winmm
ELF	7ec43000-7ec50000	Deferred        libnss_files.so.2
ELF	7ec50000-7ec5c000	Deferred        libnss_nis.so.2
ELF	7ec5c000-7ec65000	Deferred        libnss_compat.so.2
ELF	7ec67000-7ec7f000	Deferred        version<elf>
  \-PE	7ec70000-7ec7f000	\               version
ELF	7efb1000-7efdd000	Deferred        libm.so.6
ELF	7efdd000-7efe6000	Deferred        librt.so.1
ELF	7efe6000-7f000000	Deferred        libnsl.so.1
ELF	eef71000-eefb6000	Deferred        dinput<elf>
  \-PE	eef80000-eefb6000	\               dinput
ELF	eefb6000-ef01e000	Deferred        ddraw<elf>
  \-PE	eefc0000-ef01e000	\               ddraw
ELF	ef11e000-ef122000	Deferred        libgpg-error.so.0
ELF	ef122000-ef126000	Deferred        libkeyutils.so.1
ELF	ef126000-ef19a000	Deferred        libgcrypt.so.11
ELF	ef19a000-ef1aa000	Deferred        libtasn1.so.3
ELF	ef1aa000-ef1b3000	Deferred        libkrb5support.so.0
ELF	ef1b3000-ef1b8000	Deferred        libcom_err.so.2
ELF	ef1b8000-ef1e0000	Deferred        libk5crypto.so.3
ELF	ef1e0000-ef2af000	Deferred        libkrb5.so.3
ELF	ef2af000-ef2c1000	Deferred        libavahi-client.so.3
ELF	ef2c1000-ef359000	Deferred        libgnutls.so.26
ELF	ef359000-ef397000	Deferred        libgssapi_krb5.so.2
ELF	ef397000-ef3ea000	Deferred        libcups.so.2
ELF	ef404000-ef441000	Deferred        winspool<elf>
  \-PE	ef410000-ef441000	\               winspool
ELF	ef441000-ef4aa000	Deferred        setupapi<elf>
  \-PE	ef450000-ef4aa000	\               setupapi
ELF	ef4aa000-ef4cd000	Deferred        dxgi<elf>
  \-PE	ef4b0000-ef4cd000	\               dxgi
ELF	ef4cd000-ef4f0000	Deferred        iphlpapi<elf>
  \-PE	ef4d0000-ef4f0000	\               iphlpapi
ELF	ef4f0000-ef51a000	Deferred        wbemprox<elf>
  \-PE	ef500000-ef51a000	\               wbemprox
ELF	f0483000-f17da000	Deferred        libllvm-3.0.so.1
ELF	f17da000-f1b99000	Dwarf           libgallium.so
ELF	f1b99000-f1cb6000	Deferred        libglsl.so
ELF	f1cb6000-f1f30000	Dwarf           libdricore.so
ELF	f1f30000-f2300000	Dwarf           nouveau_dri.so
ELF	f2402000-f2410000	Deferred        libavahi-common.so.3
ELF	f24e2000-f2500000	Deferred        libgcc_s.so.1
ELF	f2611000-f2631000	Deferred        dpnet<elf>
  \-PE	f2620000-f2631000	\               dpnet
ELF	f2631000-f2638000	Deferred        libffi.so.6
ELF	f2638000-f263f000	Deferred        libdrm_nouveau.so.1
ELF	f263f000-f264c000	Deferred        libdrm.so.2
ELF	f264c000-f2667000	Deferred        libxcb-glx.so.0
ELF	f2667000-f267d000	Deferred        libglapi.so.0
ELF	f267d000-f26d6000	Deferred        libgl.so.1
ELF	f6ef2000-f6f0a000	Deferred        libresolv.so.2
ELF	f6f0a000-f6f12000	Deferred        libogg.so.0
ELF	f6f12000-f6f3d000	Deferred        libvorbis.so.0
ELF	f6f3d000-f70b5000	Deferred        libvorbisenc.so.2
ELF	f70b5000-f7103000	Deferred        libflac.so.8
ELF	f7103000-f710a000	Deferred        libasyncns.so.0
ELF	f710a000-f717c000	Deferred        libsndfile.so.1
ELF	f717c000-f7186000	Deferred        libwrap.so.0
ELF	f7186000-f71cf000	Deferred        libdbus-1.so.3
ELF	f71cf000-f7234000	Deferred        libpulsecommon-1.1.so
ELF	f7234000-f7282000	Deferred        libpulse.so.0
ELF	f7282000-f7374000	Deferred        libasound.so.2
ELF	f7378000-f737f000	Deferred        libasound_module_pcm_pulse.so
ELF	f738e000-f73bb000	Deferred        winealsa<elf>
  \-PE	f7390000-f73bb000	\               winealsa
ELF	f73bb000-f73db000	Deferred        mmdevapi<elf>
  \-PE	f73c0000-f73db000	\               mmdevapi
ELF	f73db000-f7420000	Deferred        dsound<elf>
  \-PE	f73e0000-f7420000	\               dsound
ELF	f7454000-f7459000	Deferred        libdl.so.2
ELF	f7459000-f7603000	Dwarf           libc.so.6
ELF	f7603000-f761e000	Deferred        libpthread.so.0
ELF	f7621000-f7625000	Deferred        libxdamage.so.1
ELF	f7625000-f762d000	Deferred        libjson.so.0
ELF	f762d000-f7630000	Deferred        libx11-xcb.so.1
ELF	f7639000-f777a000	Dwarf           libwine.so.1
ELF	f777c000-f779e000	Deferred        ld-linux.so.2
ELF	f779e000-f779f000	Dwarf           [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 nwn2.exe
	00000009    0
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
00000021 (D) C:\GOG Games\Neverwinter Nights 2 Complete\nwn2main.exe
	00000038    0
	00000037    0
	00000036    0
	00000031    0
	0000002d    0
	0000002a   15
	00000028   15
	00000025    0
	00000022    0 <==
00000023 explorer.exe
	00000024    0
System information:
    Wine build: wine-1.5.27
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-60-generic
I would be very gratefull if anybody would help
Thanks

---

### Post by pawe4 on 2014-04-19
btw I cant also crate character, only choose

---

