---
title: "cs wine and freese when trying to play the game (alsa issue I think)"
date: 2006-04-12
forum: Gaming &amp; Leisure
---

### Post by syklitengutt on 2006-04-12
I know we have a ubuntu gameing forum, but I think its better chanses of beeng able to solve the problem by asking here.

I use 
I use ubuntu 5.10 with 2.6.12-10-k7 kernel.
I use wine Wine 0.9.6
and ati:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5695 (8.23.7)

The problem is that the game freezes after some playing.
Before I wasnt able to play at all, but now Im able to play but the game freezes after a while, and I think its something with the alsa-config to do.

The way im able to play now is to do a :
cd /usr/share/alsa-base/
sudo ./snddevices

What does this do?

But the game still freezes, but after a while.

The error I get in terminal is:
[email]chris@chris:~/.wine[/email]/drive_c/Program Files/Steam$ WINEDEBUG="-all" wine Steam -applaunch 10
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.


I think I have found a solution, but its on french and I dont understand any of it. Its on a ubuntuforum for france...

Anyone who cares to translate this?
[http://http://forum.ubuntu-fr.org/viewtopic.php?pid=242286]("http://http://forum.ubuntu-fr.org/viewtopic.php?pid=242286")

---

### Post by justleen on 2006-04-12
have you tried running winecfg and change the Audio there to OSS?
(i have no experience with CS:S under wine, but WoW seems to have some problems with the alsa driver too)

---

### Post by syklitengutt on 2006-04-12
When I press the sound button winecfg crashes.
The output from terminal is:
> chris@chris:~$ winecfg
wine: Unhandled page fault on write access to 0x6c474c80 at address 0x7ec853b1 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x6c474c80 in 32-bit code (0x7ec853b1).
In 32 bit mode.
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
EIP:7ec853b1 ESP:7fabc6c8 EBP:7fabc6f0 EFLAGS:00010202( - 00 - -RI1)
EAX:7c0e0d0c EBX:7ed21cd0 ECX:7c053b30 EDX:7c0f1850
ESI:00000004 EDI:7c0e17d0
Stack dump:
0x7fabc6c8: 7c2021b0 7c0fa658 00000001 7d9841a0
0x7fabc6d8: 00001388 7c0e0dc8 7fabc720 7d9841a0
0x7fabc6e8: 7c053b38 7d9869d0 7fabc720 7d97eaff
0x7fabc6f8: 7d9869e0 7c053b30 00000004 7d9869d0
0x7fabc708: 7c2021b0 7c205750 fffffff0 7d4f03ec
0x7fabc718: 7c053b38 7c200d84 7fabc760 7d4df560
0200: sel=1007 base=7fec2000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ec853b1 (0x7ec853b1)
2 0x7d97eaff _ZN9__gnu_cxx10__mt_allocISsNS_20__common_pool_policyINS_6__poolELb1EEEE10deallocateEPSsj+0x5f in libartscbackend.so.0 (0x7d97eaff)
3 0x7d4df560 _ZN4Arts12InterfaceDefD1Ev+0x1a0 in libmcop.so.1 (0x7d4df560)
4 0x7d4a081a _ZSt8_DestroyIN9__gnu_cxx17__normal_iteratorIPN4Arts12InterfaceDefESt6vectorIS3_SaIS3_EEEES6_EvT_S9_T0_+0x2a in libmcop.so.1 (0x7d4a081a)
5 0x7d4d6443 _ZNSt6vectorIN4Arts12InterfaceDefESaIS1_EE13_M_insert_auxEN9__gnu_cxx17__normal_iteratorIPS1_S3_EERKS1_+0x723 in libmcop.so.1 (0x7d4d6443)
6 0x7d4d6d3f _ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x67f in libmcop.so.1 (0x7d4d6d3f)
7 0x7d4844a9 _ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x49 in libmcop.so.1 (0x7d4844a9)
8 0x7d486daf _ZN4Arts9ModuleDefC1ERNS_6BufferE+0x12f in libmcop.so.1 (0x7d486daf)
9 0x7d487541 _ZN4Arts10IDLFileReg7startupEv+0xe1 in libmcop.so.1 (0x7d487541)
10 0x7d419c2d _ZN4Arts14StartupManager7startupEv+0x4d in libmcop.so.1 (0x7d419c2d)
11 0x7d4920cb _ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x3cb in libmcop.so.1 (0x7d4920cb)
12 0x7d97cb27 arts_backend_init+0x87 in libartscbackend.so.0 (0x7d97cb27)
13 0x7d96d2d6 arts_init+0x46 in libartsc.so.0 (0x7d96d2d6)
14 0x7d99cf37 ARTS_WaveInit+0x27 in winearts (0x7d99cf37)
15 0x7d9991a2 ARTS_DriverProc+0x52 in winearts (0x7d9991a2)
16 0x7eaa167f in winmm (+0x1167f) (0x7eaa167f)
17 0x7eaa1ca9 DRIVER_TryOpenDriver32+0xc9 in winmm (0x7eaa1ca9)
18 0x7eaa1fa9 OpenDriver+0x169 in winmm (0x7eaa1fa9)
19 0x7eaa207e OpenDriverA+0x3e in winmm (0x7eaa207e)
20 0x7fadac79 in winecfg (+0xac79) (0x7fadac79)
21 0x7fadbc28 AudioDlgProc+0x298 in winecfg (0x7fadbc28)
22 0x7f6d3caa WINPROC_wrapper+0x1a in user32 (0x7f6d3caa)
23 0x7f6d4850 in user32 (+0x94850) (0x7f6d4850)
24 0x7f6d98ce CallWindowProcW+0x1ae in user32 (0x7f6d98ce)
25 0x7f67a257 DefDlgProcW+0x57 in user32 (0x7f67a257)
26 0x7f6d3caa WINPROC_wrapper+0x1a in user32 (0x7f6d3caa)
27 0x7f6d4850 in user32 (+0x94850) (0x7f6d4850)
28 0x7f6d9b16 CallWindowProcW+0x3f6 in user32 (0x7f6d9b16)
29 0x7f6a8abf in user32 (+0x68abf) (0x7f6a8abf)
30 0x7f6ac1d6 SendMessageTimeoutW+0x156 in user32 (0x7f6ac1d6)
31 0x7f6ac225 SendMessageW+0x35 in user32 (0x7f6ac225)
32 0x7f67f3e2 in user32 (+0x3f3e2) (0x7f67f3e2)
33 0x7f67fd7d CreateDialogIndirectParamAorW+0x2d in user32 (0x7f67fd7d)
34 0x7f67fdbb CreateDialogIndirectParamW+0x2b in user32 (0x7f67fdbb)
35 0x7eb744b3 in comctl32 (+0x444b3) (0x7eb744b3)
36 0x7eb757f1 in comctl32 (+0x457f1) (0x7eb757f1)
37 0x7eb773da PROPSHEET_DialogProc+0x95a in comctl32 (0x7eb773da)
38 0x7f6d3caa WINPROC_wrapper+0x1a in user32 (0x7f6d3caa)
39 0x7f6d4850 in user32 (+0x94850) (0x7f6d4850)
40 0x7f6d98ce CallWindowProcW+0x1ae in user32 (0x7f6d98ce)
41 0x7f67a257 DefDlgProcW+0x57 in user32 (0x7f67a257)
42 0x7f6d3caa WINPROC_wrapper+0x1a in user32 (0x7f6d3caa)
43 0x7f6d4850 in user32 (+0x94850) (0x7f6d4850)
44 0x7f6d9b16 CallWindowProcW+0x3f6 in user32 (0x7f6d9b16)
45 0x7f6a8abf in user32 (+0x68abf) (0x7f6a8abf)
46 0x7f6ac1d6 SendMessageTimeoutW+0x156 in user32 (0x7f6ac1d6)
47 0x7f6ac225 SendMessageW+0x35 in user32 (0x7f6ac225)
48 0x7eb893cc in comctl32 (+0x593cc) (0x7eb893cc)
49 0x7eb8d456 in comctl32 (+0x5d456) (0x7eb8d456)
50 0x7f6d3caa WINPROC_wrapper+0x1a in user32 (0x7f6d3caa)
51 0x7f6d4850 in user32 (+0x94850) (0x7f6d4850)
52 0x7f6d98ce CallWindowProcW+0x1ae in user32 (0x7f6d98ce)
53 0x7f6a92bc DispatchMessageW+0x16c in user32 (0x7f6a92bc)
54 0x7f67dea2 IsDialogMessageW+0xe2 in user32 (0x7f67dea2)
55 0x7eb7330b in comctl32 (+0x4330b) (0x7eb7330b)
56 0x7eb74f36 PropertySheetW+0x246 in comctl32 (0x7eb74f36)
57 0x7fae0125 WinMain+0x335 in winecfg (0x7fae0125)
58 0x7fae384e main+0x8e in winecfg (0x7fae384e)
59 0x7fae379a in winecfg (+0x1379a) (0x7fae379a)
60 0x7fcce567 in kernel32 (+0x4e567) (0x7fcce567)
61 0xb7f1cc17 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f1cc17)
0x7ec853b1: decl 0x0(%edx,%eax,4)
Modules:
Module Address Debug info Name (104 modules)
ELF 0x7399e000-739a6000 Deferred libxrender.so.1
ELF 0x7be8b000-7bf00000 Deferred ntdll<elf>
\-PE 0x7bea0000-7bf00000 \ ntdll
ELF 0x7bf00000-7bf03000 Deferred <wine-loader>
ELF 0x7d26c000-7d2b3000 Deferred libkmedia2_idl.so.1
ELF 0x7d2b3000-7d2da000 Deferred libvorbis.so.0
ELF 0x7d2da000-7d3d9000 Deferred libvorbisenc.so.2
ELF 0x7d3d9000-7d4ff000 Export libmcop.so.1
ELF 0x7d4ff000-7d54d000 Deferred libxt.so.6
ELF 0x7d54d000-7d561000 Deferred libaudio.so.2
ELF 0x7d561000-7d582000 Deferred libaudiofile.so.0
ELF 0x7d582000-7d643000 Deferred libartsflow_idl.so.1
ELF 0x7d643000-7d6ad000 Deferred libsoundserver_idl.so.1
ELF 0x7d6ad000-7d81b000 Deferred libartsflow.so.1
ELF 0x7d830000-7d8b1000 Deferred libglib-2.0.so.0
ELF 0x7d8b1000-7d964000 Deferred libasound.so.2
ELF 0x7d964000-7d96c000 Deferred libvorbisfile.so.3
ELF 0x7d96c000-7d972000 Export libartsc.so.0
ELF 0x7d973000-7d987000 Export libartscbackend.so.0
ELF 0x7d987000-7d9a1000 Export winearts<elf>
\-PE 0x7d990000-7d9a1000 \ winearts
ELF 0x7daf3000-7db17000 Deferred msacm32<elf>
\-PE 0x7db00000-7db17000 \ msacm32
ELF 0x7db17000-7db2e000 Deferred msacm<elf>
\-PE 0x7db20000-7db2e000 \ msacm
ELF 0x7db2e000-7db70000 Deferred wineoss<elf>
\-PE 0x7db40000-7db70000 \ wineoss
ELF 0x7db70000-7dbbc000 Deferred libgcrypt.so.11
ELF 0x7dbbc000-7dc1e000 Deferred libgnutls.so.11
ELF 0x7dc1e000-7dc3b000 Deferred libcups.so.2
ELF 0x7dc3b000-7dc50000 Deferred midimap<elf>
\-PE 0x7dc40000-7dc50000 \ midimap
ELF 0x7dc96000-7dca0000 Deferred libesd.so.0
ELF 0x7dd78000-7dd81000 Deferred libxcursor.so.1
ELF 0x7dd81000-7dd86000 Deferred libogg.so.0
ELF 0x7dd86000-7dd96000 Deferred libtasn1.so.2
ELF 0x7dd96000-7ddb1000 Deferred imm32<elf>
\-PE 0x7dda0000-7ddb1000 \ imm32
ELF 0x7ddb1000-7ddcd000 Deferred ximcp.so.2
ELF 0x7ddcd000-7ddd6000 Deferred librt.so.1
ELF 0x7de90000-7e773000 Deferred fglrx_dri.so
ELF 0x7e773000-7e812000 Deferred libgl.so.1
ELF 0x7e812000-7e816000 Deferred libxdmcp.so.6
ELF 0x7e816000-7e819000 Deferred libxau.so.6
ELF 0x7e819000-7e8d9000 Deferred libx11.so.6
ELF 0x7e8d9000-7e8e6000 Deferred libxext.so.6
ELF 0x7e8e6000-7e8eb000 Deferred libxxf86vm.so.1
ELF 0x7e8eb000-7e904000 Deferred libice.so.6
ELF 0x7e904000-7e981000 Deferred winex11<elf>
\-PE 0x7e910000-7e981000 \ winex11
ELF 0x7e981000-7e9a0000 Deferred libexpat.so.1
ELF 0x7e9a0000-7e9ce000 Deferred libfontconfig.so.1
ELF 0x7e9ce000-7e9e2000 Deferred libz.so.1
ELF 0x7e9e2000-7ea4c000 Deferred libfreetype.so.6
ELF 0x7ea4c000-7ea7c000 Deferred uxtheme<elf>
\-PE 0x7ea50000-7ea7c000 \ uxtheme
ELF 0x7ea7c000-7eafd000 Export winmm<elf>
\-PE 0x7ea90000-7eafd000 \ winmm
ELF 0x7eafd000-7eb26000 Deferred winspool<elf>
\-PE 0x7eb10000-7eb26000 \ winspool
ELF 0x7eb26000-7ebd5000 Export comctl32<elf>
\-PE 0x7eb30000-7ebd5000 \ comctl32
ELF 0x7ebd5000-7ebf3000 Deferred iphlpapi<elf>
\-PE 0x7ebe0000-7ebf3000 \ iphlpapi
ELF 0x7ebf3000-7ec3a000 Deferred rpcrt4<elf>
\-PE 0x7ec00000-7ec3a000 \ rpcrt4
ELF 0x7ec3a000-7ec45000 Deferred libgcc_s.so.1
ELF 0x7ed2b000-7f62b000 Deferred gdi32<elf>
\-PE 0x7ed70000-7f62b000 \ gdi32
ELF 0x7f62b000-7f744000 Export user32<elf>
\-PE 0x7f640000-7f744000 \ user32
ELF 0x7f744000-7f780000 Deferred advapi32<elf>
\-PE 0x7f750000-7f780000 \ advapi32
ELF 0x7f780000-7f807000 Deferred ole32<elf>
\-PE 0x7f790000-7f807000 \ ole32
ELF 0x7f807000-7f85d000 Deferred shlwapi<elf>
\-PE 0x7f820000-7f85d000 \ shlwapi
ELF 0x7f85d000-7f91c000 Deferred shell32<elf>
\-PE 0x7f870000-7f91c000 \ shell32
ELF 0x7f91c000-7f9b0000 Deferred comdlg32<elf>
\-PE 0x7f930000-7f9b0000 \ comdlg32
ELF 0x7fac1000-7fac6000 Deferred libxxf86dga.so.1
ELF 0x7fac6000-7fb00000 Export winecfg<elf>
\-PE 0x7fad0000-7fb00000 \ winecfg
ELF 0x7fc65000-7fd60000 Export kernel32<elf>
\-PE 0x7fc80000-7fd60000 \ kernel32
ELF 0x7fe71000-7fe78000 Deferred libsm.so.6
ELF 0x7fe78000-7fe83000 Deferred libnss_files.so.2
ELF 0x7fe83000-7fe8d000 Deferred libnss_nis.so.2
ELF 0x7fe8d000-7fea3000 Deferred libnsl.so.1
ELF 0x7fea3000-7fead000 Deferred libnss_compat.so.2
ELF 0x7feb0000-7feb4000 Deferred libgthread-2.0.so.0
ELF 0x7feb4000-7feb7000 Deferred libgmodule-2.0.so.0
ELF 0x7feb7000-7febb000 Deferred libgpg-error.so.0
ELF 0x7febb000-7febf000 Deferred libxfixes.so.3
ELF 0x7febf000-7fec2000 Deferred libxrandr.so.2
ELF 0x7fec4000-7fec6000 Deferred xlcutf8load.so.2
ELF 0x7fec6000-7fee9000 Deferred libm.so.6
ELF 0x7fee9000-7ffe0000 Deferred libwine_unicode.so.1
ELF 0xb7dd3000-b7dd7000 Deferred libdl.so.2
ELF 0xb7dd7000-b7f05000 Deferred libc.so.6
ELF 0xb7f05000-b7f18000 Deferred libpthread.so.0
ELF 0xb7f18000-b7f32000 Export libwine.so.1
ELF 0xb7f49000-b7f5f000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
00000009 0 <==
WineDbg terminated on pid 0x8

---

### Post by justleen on 2006-04-12
pfoe, thats way too much ubuntu :)

im not sure on this one.. i had this before (wine crashing when selecting Audio), and i recompiled the whole wine.. 

perhaps some else here has any thoughts on this?

---

### Post by syklitengutt on 2006-04-12
Ive read allot and people sais that if I want to play cs 1.6 
I should use wine0.9.6
So thats what I do...

Anyone who got any ideas on this....
To change the sounddriver by edit a cfg file or something

---

