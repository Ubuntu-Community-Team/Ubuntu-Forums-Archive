---
title: "Wine Error"
date: 2005-08-12
forum: Gaming &amp; Leisure
---

### Post by speedemonV12 on 2005-08-12
this is the error i get when trying to run SOF2 mp test.

wine: Unhandled exception (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x00000290 in 32-bit code (0x7c8492c6).
In 32 bit mode.
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:7c8492c6 ESP:7b99fc6c EBP:7b99fc94 EFLAGS:00210246( - 00 -RIZP1)
EAX:00000000 EBX:7c86ef74 ECX:0002002e EDX:7bc79ca8
ESI:7c86ee68 EDI:00000002
Stack dump:
0x7b99fc6c: 7be83000 7b99fc9c 005409e0 005409d0
0x7b99fc7c: bd6dd71a 7c86ee68 7bc79cc8 00000001
0x7b99fc8c: 00000001 00000002 7b99fd5c 00467aab
0x7b99fc9c: 7bc79ca8 0002002e 00000002 00bd5528
0x7b99fcac: 00000001 004436be 0055b8b0 0000000c
0x7b99fcbc: 00000000 00000000 7a566b98 00000001
Backtrace:
=>1 0x7c8492c6 in dsound (+0x192c6) (0x7b99fc94)
fixme:dbghelp:sffip_cb NIY on 'D:\projects\sof2mp\code\Release\SoF2MP.pdb'
2 0x00467aab in sof2mp-test (+0x67aab) (0x7b99fd5c)
3 0x00465b7b in sof2mp-test (+0x65b7b) (0x7b99ff20)
4 0x7bb777b2 in kernel32 (+0x477b2) (0x7b99fff4)
5 0xb7fc71b1 wine_switch_to_stack+0x11 in libwine.so.1 (0x00000000)
0x7c8492c6: movl %edi,0x290(%eax)
Modules:
Module Address Debug info Name (79 modules)
PE 0x00400000-01263000 Export sof2mp-test
ELF 0x77402000-77478000 Deferred libglu.so.1
ELF 0x77485000-77520000 Deferred opengl32<elf>
\-PE 0x774c0000-77520000 \ opengl32
ELF 0x7a239000-7a2fc000 Deferred comctl32<elf>
\-PE 0x7a250000-7a2fc000 \ comctl32
ELF 0x7a2fc000-7a3c7000 Deferred shell32<elf>
\-PE 0x7a320000-7a3c7000 \ shell32
ELF 0x7a3c7000-7a425000 Deferred shlwapi<elf>
\-PE 0x7a3e0000-7a425000 \ shlwapi
ELF 0x7a425000-7a445000 Deferred mpr<elf>
\-PE 0x7a430000-7a445000 \ mpr
ELF 0x7a445000-7a48b000 Deferred wininet<elf>
\-PE 0x7a450000-7a48b000 \ wininet
ELF 0x7a48b000-7a4d6000 Deferred rpcrt4<elf>
\-PE 0x7a4a0000-7a4d6000 \ rpcrt4
ELF 0x7a4d6000-7a567000 Deferred ole32<elf>
\-PE 0x7a4f0000-7a567000 \ ole32
ELF 0x7a567000-7a587000 Deferred iphlpapi<elf>
\-PE 0x7a570000-7a587000 \ iphlpapi
ELF 0x7a587000-7a5b1000 Deferred ws2_32<elf>
\-PE 0x7a590000-7a5b1000 \ ws2_32
ELF 0x7a5b1000-7a5ce000 Deferred wsock32<elf>
\-PE 0x7a5c0000-7a5ce000 \ wsock32
ELF 0x7a5ce000-7a5d9000 Deferred libgcc_s.so.1
ELF 0x7a6a0000-7afab000 Deferred gdi32<elf>
\-PE 0x7a6f0000-7afab000 \ gdi32
ELF 0x7afab000-7b0dd000 Deferred user32<elf>
\-PE 0x7afd0000-7b0dd000 \ user32
ELF 0x7b0dd000-7b15e000 Deferred winmm<elf>
\-PE 0x7b0f0000-7b15e000 \ winmm
ELF 0x7b15e000-7b1a0000 Deferred advapi32<elf>
\-PE 0x7b170000-7b1a0000 \ advapi32
ELF 0x7baff000-7bc10000 Export kernel32<elf>
\-PE 0x7bb30000-7bc10000 \ kernel32
ELF 0x7bd27000-7bd30000 Deferred libnss_files.so.2
ELF 0x7bd30000-7bd39000 Deferred libnss_nis.so.2
ELF 0x7bd39000-7bd4d000 Deferred libnsl.so.1
ELF 0x7bd4d000-7bd55000 Deferred libnss_compat.so.2
ELF 0x7bd62000-7bd83000 Deferred libm.so.6
ELF 0x7bd83000-7be78000 Deferred libwine_unicode.so.1
ELF 0x7be85000-7bf00000 Deferred ntdll<elf>
\-PE 0x7bea0000-7bf00000 \ ntdll
ELF 0x7bf00000-7bf03000 Deferred <wine-loader>
ELF 0x7c820000-7c870000 Export dsound<elf>
\-PE 0x7c830000-7c870000 \ dsound
ELF 0x7d1eb000-7d200000 Deferred midimap<elf>
\-PE 0x7d1f0000-7d200000 \ midimap
ELF 0x7d311000-7d335000 Deferred msacm32<elf>
\-PE 0x7d320000-7d335000 \ msacm32
ELF 0x7d335000-7d34e000 Deferred msacm.drv<elf>
\-PE 0x7d340000-7d34e000 \ msacm.drv
ELF 0x7d34e000-7d394000 Deferred wineoss.drv<elf>
\-PE 0x7d360000-7d394000 \ wineoss.drv
ELF 0x7d3b2000-7d3bb000 Deferred libxcursor.so.1
ELF 0x7d3c8000-7d3e7000 Deferred imm32<elf>
\-PE 0x7d3d0000-7d3e7000 \ imm32
ELF 0x7d3e7000-7d403000 Deferred ximcp.so.2
ELF 0x7d403000-7d407000 Deferred libxrandr.so.2
ELF 0x7d407000-7d40f000 Deferred libxrender.so.1
ELF 0x7d41a000-7d41c000 Deferred xlcutf8load.so.2
ELF 0x7fb7f000-7fd40000 Deferred r200_dri.so
ELF 0x7fd40000-7fd45000 Deferred libxxf86vm.so.1
ELF 0x7fd45000-7fdac000 Deferred libgl.so.1
ELF 0x7fdac000-7fe71000 Deferred libx11.so.6
ELF 0x7fe71000-7fe7e000 Deferred libxext.so.6
ELF 0x7fe7e000-7fe96000 Deferred libice.so.6
ELF 0x7fe96000-7fe9f000 Deferred libsm.so.6
ELF 0x7feac000-7ff2e000 Deferred winex11.drv<elf>
\-PE 0x7fec0000-7ff2e000 \ winex11.drv
ELF 0x7ff2e000-7ff4e000 Deferred libexpat.so.1
ELF 0x7ff4e000-7ff75000 Deferred libfontconfig.so.1
ELF 0x7ff75000-7ff86000 Deferred libz.so.1
ELF 0x7ff86000-7fff3000 Deferred libfreetype.so.6
ELF 0xb7e81000-b7e84000 Deferred libdl.so.2
ELF 0xb7e85000-b7fb2000 Deferred libc.so.6
ELF 0xb7fb2000-b7fc2000 Deferred libpthread.so.0
ELF 0xb7fc2000-b7fdb000 Export libwine.so.1
ELF 0xb7fea000-b8000000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:\ProgramFiles\SoldierofFortuneII-DoubleHelixMPTEST\SoF2MP-Test.exe
00000009 0 <==
WineDbg terminated on pid 0x8



anyone know what i need to do?

---

