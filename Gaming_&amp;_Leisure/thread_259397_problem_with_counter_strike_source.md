---
title: "problem with counter strike source"
date: 2006-09-17
forum: Gaming &amp; Leisure
---

### Post by NiksaVel on 2006-09-17
Hey all, I just installed steam and counter-strike source following the howto from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam).

I can start steam, update it, I see counter strike as installed, it even did some updating, but when I try to start it, it loads for a minute or two, shows me the counter-strike menu background image and at the point where it should load and show the menu it just closes and I am brought back to my desktop, at a lower resolution...


can anyone help me with this?  


I was thinking it might be a problem with my wine setup, when I click on the audio tab, I see some errors in the console:

> ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: No such file or directory
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory


I have selected OSS drivers, because I read somewhere that I should do so :)



thank you in advance for your help!

---

### Post by haxer on 2006-09-17
Hmm.. installed all graphic card drivers?

---

### Post by NiksaVel on 2006-09-17
I believe so:

> niksavel@darth-kubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

niksavel@darth-kubuntu:~$


---

### Post by NiksaVel on 2006-09-18
here is the console error I get when it drops me to desktop... maybe it will help some1 help me

> 
niksavel@darth-kubuntu:~$ WINEDEBUG=-all nice -n 19 wine d:/Program\ Files/Steam/Steam.exe -fullscreen
wine: Unhandled page fault on read access to 0x0d2fa1a0 at address 0xe203e2c (thread 003a), starting debugger...
WineDbg starting on pid 0x39
Unhandled exception: page fault on read access to 0x0d2fa1a0 in 32-bit code (0x0e203e2c).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:0e203e2c ESP:0034fc04 EBP:0034fc3c EFLAGS:00210206( - 00 - RIP1)
EAX:0d2fa1a0 EBX:00000001 ECX:05240960 EDX:ffffffff
ESI:05240960 EDI:0e216050
Stack dump:
0x0034fc04: 00000001 00000000 00000001 0e21604c
0x0034fc14: 0e2082e7 00000000 00000000 00000001
0x0034fc24: 0034fc18 0034f758 0034fc84 0e2083d4
0x0034fc34: 0e213518 00000000 0034fc58 0e20836b
0x0034fc44: 00000000 00000000 00000001 0e2069b8
0x0034fc54: 00000000 0034fc94 0e206ac4 0e200000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x0e203e2c in scenefilecache (+0x3e2c) (0x0e203e2c)
2 0x0e20836b in scenefilecache (+0x836b) (0x0e20836b)
3 0x0e206ac4 in scenefilecache (+0x6ac4) (0x0e206ac4)
4 0x7efb83f5 call_dll_entry_point+0x15 in ntdll (0x7efb83f5)
5 0x7efb9da8 in ntdll (+0x29da8) (0x7efb9da8)
6 0x7efba287 in ntdll (+0x2a287) (0x7efba287)
7 0x7eeca3dc ExitProcess+0x1b in kernel32 (0x7eeca3dc)
8 0x00401abe in hl2 (+0x1abe) (0x00401abe)
9 0x00401c41 in hl2 (+0x1c41) (0x00401c41)
10 0x7eecba6f in kernel32 (+0x4ba6f) (0x7eecba6f)
11 0xb7e43287 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7e43287)
0x0e203e2c: call *0x0(%eax)
Modules:
Module Address Debug info Name (115 modules)
PE 350000-36e000 Deferred vstdlib
PE 370000-3a6000 Deferred tier0
PE 400000-41c000 Export hl2
PE d660000-dc94000 Deferred engine
PE dca0000-dcb0000 Deferred steam_api
PE df40000-df4f000 Deferred unicode
PE e1c0000-e1f6000 Deferred soundemittersystem
PE e200000-e21b000 Export scenefilecache
PE e220000-e333000 Deferred steamclient
PE e340000-e37d000 Deferred vstdlib_s
PE e380000-e3bf000 Deferred tier0_s
PE e4e0000-e6c1000 Deferred gameui
PE f670000-f680000 Deferred vaudio_miles
PE 10000000-10030000 Deferred launcher
PE 20000000-2030a000 Deferred steam
PE 21100000-21164000 Deferred mss32
PE 22000000-2263e000 Deferred server
PE 24000000-2446e000 Deferred client
PE 26400000-26439000 Deferred mssvoice.asi
PE 26f00000-26f2e000 Deferred mssmp3.asi
PE 60000000-60021000 Deferred cserhelper
ELF 73820000-73865000 Deferred dbghelp<elf>
\-PE 73830000-73865000 \ dbghelp
ELF 73add000-73b26000 Deferred dsound<elf>
\-PE 73af0000-73b26000 \ dsound
ELF 73b26000-73b60000 Deferred shdocvw<elf>
\-PE 73b30000-73b60000 \ shdocvw
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7c961000-7c976000 Deferred psapi<elf>
\-PE 7c970000-7c976000 \ psapi
ELF 7c9a7000-7c9bb000 Deferred joystick<elf>
\-PE 7c9b0000-7c9bb000 \ joystick
ELF 7cbdd000-7cbe2000 Deferred libnss_dns.so.2
ELF 7cd2d000-7cd4c000 Deferred mpr<elf>
\-PE 7cd30000-7cd4c000 \ mpr
ELF 7cd4c000-7cd93000 Deferred wininet<elf>
\-PE 7cd60000-7cd93000 \ wininet
ELF 7cd93000-7ce25000 Deferred oleaut32<elf>
\-PE 7cda0000-7ce25000 \ oleaut32
ELF 7ce85000-7ce9a000 Deferred midimap<elf>
\-PE 7ce90000-7ce9a000 \ midimap
ELF 7cec0000-7ced8000 Deferred msacm32<elf>
\-PE 7ced0000-7ced8000 \ msacm32
ELF 7ced8000-7cf14000 Deferred wineoss<elf>
\-PE 7cee0000-7cf14000 \ wineoss
ELF 7cf14000-7cf9c000 Deferred winmm<elf>
\-PE 7cf20000-7cf9c000 \ winmm
ELF 7d18a000-7d1bb000 Deferred uxtheme<elf>
\-PE 7d190000-7d1bb000 \ uxtheme
ELF 7d1bb000-7d1cf000 Deferred mswsock<elf>
\-PE 7d1c0000-7d1cf000 \ mswsock
ELF 7d1cf000-7d1e3000 Deferred lz32<elf>
\-PE 7d1e0000-7d1e3000 \ lz32
ELF 7d1e3000-7d1fc000 Deferred version<elf>
\-PE 7d1f0000-7d1fc000 \ version
ELF 7d1fc000-7d2be000 Deferred comctl32<elf>
\-PE 7d210000-7d2be000 \ comctl32
ELF 7d2be000-7d314000 Deferred shlwapi<elf>
\-PE 7d2d0000-7d314000 \ shlwapi
ELF 7d314000-7d3fa000 Deferred shell32<elf>
\-PE 7d320000-7d3fa000 \ shell32
ELF 7d3fa000-7d449000 Deferred rpcrt4<elf>
\-PE 7d410000-7d449000 \ rpcrt4
ELF 7d449000-7d4d9000 Deferred ole32<elf>
\-PE 7d460000-7d4d9000 \ ole32
ELF 7d4d9000-7d4ec000 Deferred libresolv.so.2
ELF 7d4f7000-7d4fe000 Deferred libnss_mdns.so.2
ELF 7d4fe000-7d51d000 Deferred iphlpapi<elf>
\-PE 7d510000-7d51d000 \ iphlpapi
ELF 7d51d000-7d547000 Deferred ws2_32<elf>
\-PE 7d530000-7d547000 \ ws2_32
ELF 7d547000-7d561000 Deferred wsock32<elf>
\-PE 7d550000-7d561000 \ wsock32
ELF 7d563000-7d568000 Deferred libxfixes.so.3
ELF 7d568000-7d571000 Deferred libxcursor.so.1
ELF 7d571000-7d58d000 Deferred imm32<elf>
\-PE 7d580000-7d58d000 \ imm32
ELF 7d58d000-7d595000 Deferred libxrender.so.1
ELF 7de35000-7de3d000 Deferred librt.so.1
ELF 7df09000-7e804000 Deferred fglrx_dri.so
ELF 7e804000-7e8a4000 Deferred libgl.so.1
ELF 7e8a4000-7e98a000 Deferred libx11.so.6
ELF 7e98a000-7e997000 Deferred libxext.so.6
ELF 7e997000-7e9af000 Deferred libice.so.6
ELF 7e9af000-7ea30000 Deferred winex11<elf>
\-PE 7e9c0000-7ea30000 \ winex11
ELF 7ea30000-7ea4f000 Deferred libexpat.so.1
ELF 7ea4f000-7ea7d000 Deferred libfontconfig.so.1
ELF 7ea7d000-7ea91000 Deferred libz.so.1
ELF 7ea91000-7eaf3000 Deferred libfreetype.so.6
ELF 7eaf3000-7eb37000 Deferred advapi32<elf>
\-PE 7eb00000-7eb37000 \ advapi32
ELF 7eb37000-7eb41000 Deferred libgcc_s.so.1
ELF 7ec16000-7ecc8000 Deferred gdi32<elf>
\-PE 7ec30000-7ecc8000 \ gdi32
ELF 7ecc8000-7edfb000 Deferred user32<elf>
\-PE 7ece0000-7edfb000 \ user32
ELF 7edfb000-7ee05000 Deferred libnss_files.so.2
ELF 7ee05000-7ee0e000 Deferred libnss_nis.so.2
ELF 7ee0e000-7ee23000 Deferred libnsl.so.1
ELF 7ee23000-7ee2c000 Deferred libnss_compat.so.2
ELF 7ee5f000-7ef60000 Export kernel32<elf>
\-PE 7ee80000-7ef60000 \ kernel32
ELF 7ef60000-7ef82000 Deferred libm.so.6
ELF 7ef82000-7f000000 Export ntdll<elf>
\-PE 7ef90000-7f000000 \ ntdll
ELF b7ce1000-b7ce4000 Deferred libxrandr.so.2
ELF b7ce5000-b7ce8000 Deferred libdl.so.2
ELF b7ce8000-b7e17000 Deferred libc.so.6
ELF b7e17000-b7e29000 Deferred libpthread.so.0
ELF b7e2c000-b7e2f000 Deferred libxau.so.6
ELF b7e2f000-b7e34000 Deferred libxxf86vm.so.1
ELF b7e34000-b7e3c000 Deferred libsm.so.6
ELF b7e3c000-b7f4c000 Export libwine.so.1
ELF b7f4f000-b7f65000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000039 (D) D:\Program Files\steam\SteamApps\nileder\counter-strike source\hl2.exe
00000042 15
0000003f 0
0000003b 2
0000003a 0 <==
0000000a
0000000b 0
00000008
00000038 0
00000037 0
00000035 0
00000034 0
00000033 1
00000032 0
00000031 1
00000030 0
0000002f 1
0000002e 0
0000002d 1
0000002c 0
0000002b 1
0000002a 0
00000029 1
00000028 0
00000027 1
00000026 0
00000025 1
00000023 0
0000001f 0
0000001e 0
0000001c 0
0000001b 1
00000019 0
00000016 0
00000015 0
00000014 1
00000013 0
00000012 0
00000011 0
00000010 0
0000000f 0
0000000d 0
0000000c 0
00000009 0


---

