---
title: "Ubuntu edgy and wine"
date: 2007-01-16
forum: Desktop Environments
---

### Post by Pietje on 2007-01-16
I have installed ubuntu edgy with latest patches and wine 0.9.29. i use a application called osfinancials, [www.osfinancials.org](www.osfinancials.org), this installs, but does not run. Strangly enough, it does run when using suse and wine, so it seems to be related to the combination of ubuntu edgy and wine.

When I run the exe, osfinancials.exe, I get the following errors:

sudo wine osFinancials.exe 
fixme:winspool:WINSPOOL_EnumPrinters We don't handle PRINTER_ENUM_CONNECTIONS
fixme:winspool:WINSPOOL_EnumPrinters We don't handle PRINTER_ENUM_CONNECTIONS
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b8407b0 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc2fc4c).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7bc2fc4c ESP:0033f5c4 EBP:0033f628 EFLAGS:00200282( - 00 - -IS1)
EAX:0033f5d0 EBX:7bc78904 ECX:00110020 EDX:0033f9ac
ESI:0033f9ac EDI:0033f634
Stack dump:
0x0033f5c4: 00110000 00000002 7ed46754 c0000025
0x0033f5d4: 00000001 0033f9ac 7ed01a3c 00000000
0x0033f5e4: 00000000 00173440 0000002e 0033f630
0x0033f5f4: 000003ff 00000000 00000000 0000000b
0x0033f604: 0033fa54 00402c57 0033fa54 004059c5
0x0033f614: 013b8648 0033f630 00405a08 7bc2fc00
Backtrace:
=>1 0x7bc2fc4c __regs_RtlRaiseException+0x4c() in ntdll (0x0033f62
2 0x7bc65863 in ntdll (+0x55863) (0x0033f98
3 0x7bc2f236 RtlRaiseException+0x6() in ntdll (0x0033fa00)
4 0x0043f986 in osfinancials (+0x3f986) (0x0033fe7
5 0x00440650 in osfinancials (+0x40650) (0x0033fea4)
6 0x00821a2b in osfinancials (+0x421a2b) (0x0033fec
7 0x004055b7 in osfinancials (+0x55b7) (0x0033ff0
8 0x7b8703ae in kernel32 (+0x503ae) (0x0033ffe
9 0xb7e09587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc2fc4c __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module Address Debug info Name (94 modules)
PE 400000-11a1000 Export osfinancials
ELF 7b800000-7b91c000 Export kernel32<elf>
\-PE 7b820000-7b91c000 \ kernel32
ELF 7bc00000-7bc83000 Export ntdll<elf>
\-PE 7bc10000-7bc83000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7e06e000-7e083000 Deferred midimap<elf>
\-PE 7e070000-7e083000 \ midimap
ELF 7e0a9000-7e0c1000 Deferred msacm32<elf>
\-PE 7e0b0000-7e0c1000 \ msacm32
ELF 7e0c1000-7e0fd000 Deferred wineoss<elf>
\-PE 7e0d0000-7e0fd000 \ wineoss
ELF 7e0fd000-7e101000 Deferred libgpg-error.so.0
ELF 7e101000-7e14f000 Deferred libgcrypt.so.11
ELF 7e14f000-7e162000 Deferred libtasn1.so.3
ELF 7e162000-7e190000 Deferred libcrypt.so.1
ELF 7e19b000-7e20a000 Deferred libgnutls.so.13
ELF 7e20a000-7e239000 Deferred libcups.so.2
ELF 7e266000-7e298000 Deferred uxtheme<elf>
\-PE 7e270000-7e298000 \ uxtheme
ELF 7e29a000-7e29f000 Deferred libxfixes.so.3
ELF 7e29f000-7e2a8000 Deferred libxcursor.so.1
ELF 7e2a8000-7e2c6000 Deferred ximcp.so.2
ELF 7e2c6000-7e2c9000 Deferred libxrandr.so.2
ELF 7e2c9000-7e2d1000 Deferred libxrender.so.1
ELF 7e2d1000-7e2d4000 Deferred libxinerama.so.1
ELF 7e2d4000-7e2db000 Deferred libdrm.so.2
ELF 7e2db000-7e34a000 Deferred libgl.so.1
ELF 7e34a000-7e34f000 Deferred libxdmcp.so.6
ELF 7e34f000-7e352000 Deferred libxau.so.6
ELF 7e352000-7e41b000 Deferred libx11.so.6
ELF 7e41b000-7e428000 Deferred libxext.so.6
ELF 7e428000-7e42d000 Deferred libxxf86vm.so.1
ELF 7e42d000-7e445000 Deferred libice.so.6
ELF 7e445000-7e4d2000 Deferred winex11<elf>
\-PE 7e450000-7e4d2000 \ winex11
ELF 7e4d2000-7e4f0000 Deferred libexpat.so.1
ELF 7e4f0000-7e51f000 Deferred libfontconfig.so.1
ELF 7e51f000-7e533000 Deferred libz.so.1
ELF 7e533000-7e59d000 Deferred libfreetype.so.6
ELF 7e59d000-7e62b000 Deferred winmm<elf>
\-PE 7e5b0000-7e62b000 \ winmm
ELF 7e62b000-7e63f000 Deferred lz32<elf>
\-PE 7e630000-7e63f000 \ lz32
ELF 7e63f000-7e658000 Deferred version<elf>
\-PE 7e650000-7e658000 \ version
ELF 7e658000-7e66c000 Deferred shfolder<elf>
\-PE 7e660000-7e66c000 \ shfolder
ELF 7e66c000-7e68e000 Deferred oledlg<elf>
\-PE 7e670000-7e68e000 \ oledlg
ELF 7e68e000-7e6ad000 Deferred mpr<elf>
\-PE 7e6a0000-7e6ad000 \ mpr
ELF 7e6ad000-7e6c9000 Deferred imm32<elf>
\-PE 7e6b0000-7e6c9000 \ imm32
ELF 7e6c9000-7e761000 Deferred oleaut32<elf>
\-PE 7e6e0000-7e761000 \ oleaut32
ELF 7e761000-7e77e000 Deferred hhctrl<elf>
\-PE 7e770000-7e77e000 \ hhctrl
ELF 7e77e000-7e7b0000 Deferred winspool<elf>
\-PE 7e790000-7e7b0000 \ winspool
ELF 7e7b0000-7e7c3000 Deferred libresolv.so.2
ELF 7e7c3000-7e7e1000 Deferred iphlpapi<elf>
\-PE 7e7d0000-7e7e1000 \ iphlpapi
ELF 7e7e1000-7e835000 Deferred rpcrt4<elf>
\-PE 7e7f0000-7e835000 \ rpcrt4
ELF 7e835000-7e8ce000 Deferred ole32<elf>
\-PE 7e840000-7e8ce000 \ ole32
ELF 7e8ce000-7e926000 Deferred shlwapi<elf>
\-PE 7e8e0000-7e926000 \ shlwapi
ELF 7e926000-7ea18000 Deferred shell32<elf>
\-PE 7e940000-7ea18000 \ shell32
ELF 7ea18000-7eab8000 Deferred comdlg32<elf>
\-PE 7ea20000-7eab8000 \ comdlg32
ELF 7eab8000-7eac3000 Deferred libgcc_s.so.1
ELF 7eac3000-7eac5000 Deferred xlcutf8load.so.2
ELF 7eac5000-7eace000 Deferred libsm.so.6
ELF 7ebad000-7ec63000 Deferred gdi32<elf>
\-PE 7ebc0000-7ec63000 \ gdi32
ELF 7ec63000-7ed9b000 Deferred user32<elf>
\-PE 7ec80000-7ed9b000 \ user32
ELF 7ed9b000-7ee5b000 Deferred comctl32<elf>
\-PE 7eda0000-7ee5b000 \ comctl32
ELF 7ee5b000-7eea1000 Deferred advapi32<elf>
\-PE 7ee70000-7eea1000 \ advapi32
ELF 7efae000-7efb9000 Deferred libnss_files.so.2
ELF 7efb9000-7efcf000 Deferred libnsl.so.1
ELF 7efcf000-7eff5000 Deferred libm.so.6
ELF 7eff6000-7f000000 Deferred libnss_nis.so.2
ELF b7ca2000-b7cab000 Deferred libnss_compat.so.2
ELF b7cac000-b7cb0000 Deferred libdl.so.2
ELF b7cb0000-b7de4000 Deferred libc.so.6
ELF b7de4000-b7df7000 Deferred libpthread.so.0
ELF b7e02000-b7f13000 Export libwine.so.1
ELF b7f15000-b7f30000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000a 
0000000c 0
0000000b 0
00000008 (D) C:\osFinancials\osFinancials.exe
00000009 0 <==

Can anybody help?

---

### Post by celem on 2007-01-16
I don't use osFinancials, but I am very interested in wine working well. Anyway, I installed osFinancials on my Dapper system to see if I got the same results. My results were virtually the same as yours, thus I won't post the output. However, it seems that the Firebird data base is required to be simultaneously running as a service, and that fails. Is the fact that Firebird is not running the cause of osFinancial's crash? Firebird fails as shown below:

[email]ecomer@verna:~/.wine[/email]/drive_c/osFinancials$ wine --version
wine-0.9.29
[email]ecomer@verna:~/.wine[/email]/drive_c/osFinancials$ wine Firebird.exe
fixme:advapi:CheckTokenMembership ((nil) 0x169980 0x34fe00) stub!
fixme:shell:SHGetFileInfoW This combination of flags is not supported yet
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\Firebird\\Firebird_1_5\\IPLicense.txt") stub
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
Firebird has been successfully installed in the registry.
Existing GDS32.DLL (same version) found.
No update needed.
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
wine: Unhandled page fault on read access to 0x00000004 at address 0x401061 (thread 0024), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00401061).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00401061 ESP:7e3199f8 EBP:00000000 EFLAGS:00210296(   - 00      RISAP1)
 EAX:001684a8 EBX:7ebcc54c ECX:00110020 EDX:00110024
 ESI:00000004 EDI:ffffffff
Stack dump:
0x7e3199f8:  7ffd8f10 7ffd8e0c 7ebcc54c 7e319a78
0x7e319a08:  00000000 00000002 b7e77334 00000005
0x7e319a18:  00110000 7bc28a27 b7dad0e0 00000010
0x7e319a28:  00000020 7ebc07f8 00000000 00000000
0x7e319a38:  7e319a78 7bc367b8 00110020 00000002
0x7e319a48:  00000000 b7e75adc 00000000 7e319aa0
Backtrace:
=>1 0x00401061 in fbguard (+0x1061) (0x00000000)
0x00401061: movl        0x0(%esi),%eax
Modules:
Module  Address                 Debug info      Name (71 modules)
PE      400000-410000   Export          fbguard
PE      10000000-1005c000       Deferred        fbclient
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b919000       Deferred        kernel32<elf>
  \-PE  7b820000-7b919000       \               kernel32
ELF     7bc00000-7bc81000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc81000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e459000-7e48b000       Deferred        uxtheme<elf>
  \-PE  7e460000-7e48b000       \               uxtheme
ELF     7e48b000-7e48f000       Deferred        libxfixes.so.3
ELF     7e48f000-7e498000       Deferred        libxcursor.so.1
ELF     7e498000-7e4b4000       Deferred        imm32<elf>
  \-PE  7e4a0000-7e4b4000       \               imm32
ELF     7e4b4000-7e4b7000       Deferred        libxrandr.so.2
ELF     7e4b7000-7e4bf000       Deferred        libxrender.so.1
ELF     7e4bf000-7e4c2000       Deferred        libxinerama.so.1
ELF     7e4c2000-7e4c9000       Deferred        libdrm.so.2
ELF     7e4c9000-7e52f000       Deferred        libgl.so.1
ELF     7e52f000-7e532000       Deferred        libxau.so.6
ELF     7e532000-7e618000       Deferred        libx11.so.6
ELF     7e618000-7e625000       Deferred        libxext.so.6
ELF     7e625000-7e63d000       Deferred        libice.so.6
ELF     7e63d000-7e6c9000       Deferred        winex11<elf>
  \-PE  7e650000-7e6c9000       \               winex11
ELF     7e6c9000-7e6e8000       Deferred        libexpat.so.1
ELF     7e6e8000-7e716000       Deferred        libfontconfig.so.1
ELF     7e716000-7e72a000       Deferred        libz.so.1
ELF     7e72a000-7e793000       Deferred        libfreetype.so.6
ELF     7e793000-7e7f5000       Deferred        msvcrt<elf>
  \-PE  7e7a0000-7e7f5000       \               msvcrt
ELF     7e7f5000-7e814000       Deferred        mpr<elf>
  \-PE  7e800000-7e814000       \               mpr
ELF     7e814000-7e83f000       Deferred        ws2_32<elf>
  \-PE  7e820000-7e83f000       \               ws2_32
ELF     7e83f000-7e853000       Deferred        lz32<elf>
  \-PE  7e850000-7e853000       \               lz32
ELF     7e853000-7e86c000       Deferred        version<elf>
  \-PE  7e860000-7e86c000       \               version
ELF     7e86c000-7e92e000       Deferred        comctl32<elf>
  \-PE  7e880000-7e92e000       \               comctl32
ELF     7e92e000-7e941000       Deferred        libresolv.so.2
ELF     7e941000-7e960000       Deferred        iphlpapi<elf>
  \-PE  7e950000-7e960000       \               iphlpapi
ELF     7e960000-7e9b3000       Deferred        rpcrt4<elf>
  \-PE  7e970000-7e9b3000       \               rpcrt4
ELF     7e9b3000-7ea48000       Deferred        ole32<elf>
  \-PE  7e9c0000-7ea48000       \               ole32
ELF     7ea48000-7ea9f000       Deferred        shlwapi<elf>
  \-PE  7ea60000-7ea9f000       \               shlwapi
ELF     7ea9f000-7eb8d000       Deferred        shell32<elf>
  \-PE  7eab0000-7eb8d000       \               shell32
ELF     7eb8d000-7ebd1000       Deferred        advapi32<elf>
  \-PE  7eba0000-7ebd1000       \               advapi32
ELF     7ebd1000-7ebdb000       Deferred        libgcc_s.so.1
ELF     7ecb0000-7ed64000       Deferred        gdi32<elf>
  \-PE  7ecd0000-7ed64000       \               gdi32
ELF     7ed64000-7ee98000       Deferred        user32<elf>
  \-PE  7ed80000-7ee98000       \               user32
ELF     7ee98000-7eea2000       Deferred        libnss_files.so.2
ELF     7eea2000-7eeb7000       Deferred        libnsl.so.1
ELF     7eeb7000-7eec0000       Deferred        libnss_compat.so.2
ELF     7eec2000-7eeca000       Deferred        libsm.so.6
ELF     7efd4000-7eff6000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d41000-b7d46000       Deferred        libxxf86vm.so.1
ELF     b7d48000-b7d4b000       Deferred        libdl.so.2
ELF     b7d4b000-b7e7a000       Deferred        libc.so.6
ELF     b7e7a000-b7e8c000       Deferred        libpthread.so.0
ELF     b7e96000-b7fa7000       Deferred        libwine.so.1
ELF     b7faa000-b7fc0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000021 (D) C:\Program Files\Firebird\Firebird_1_5\bin\fbguard.exe
        00000024    0 <==
        00000023    0
        00000022    0
0000001f
        00000020    0
0000000d
        0000000e    0
0000000a
        0000000c    0
        0000000b    0
00000008
        00000009    0
Service failed to complete its startup sequence.
[email]ecomer@verna:~/.wine[/email]/drive_c/osFinancials$

P.S.: I'll be uninstallin osFinancials so I won't be of any further help to you. Good Luck!

---

### Post by Pietje on 2007-01-18
Ok, I am glad to see it did not work for you, but sad to hear that you have uninstalled osfinancials. The problem I have is by running the actual program, osfinancials.exe, the firebird database is not important, as this is running under native linux on a server. All i need is for the client to work, so I can connect to the database on the server. Just to be clear, can you confirm that when you run osfinancials.exe, you experience the same errors as i have? Under suse it works...

Maybe I should open a wine bugreport for this..

---

### Post by celem on 2007-01-18
Yes, when running osfinancials my output was almost identical. I am running the "latest" version of WINE, downloaded from winehq.

---

### Post by celem on 2007-01-18
The following ling indicates that it is a Delphi problem and it sometimes happens in Windows. Comments in the lhe link makes me wonder if changing the Windows version in Wine might make a difference. Try running as Win98, Win2K or XP - see if it helps or changes.

[http://forums.devshed.com/delphi-programming-90/xp-error-on-createform-325842.html](http://forums.devshed.com/delphi-programming-90/xp-error-on-createform-325842.html)

---

### Post by Janneman100 on 2007-11-12
I have osFinancials running on vanilla wine, out of the box.
Install the latest version, currently 2.0.1.0 with wine and remove afterwards the plugin OBAangifte.mpt. This is a specific Dutch plugin, for posting tax to the government, non-dutch users doesn't use it. This plugin needs to be reworked to work with wine.

Into the wiki on osFinancials website a detailed installation instruction is available.
You have the option to run the firebird database, which is osFinancials using to store the data, directly on Ubuntu Linux, on a network server or in wine.

---

### Post by bharadwaj on 2007-11-12
Iam sure this will be usefull to you this is all about winefix.
[http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html](http://wine-review.blogspot.com/2007/10/winefix-improved-desktop-integration.html)

---

