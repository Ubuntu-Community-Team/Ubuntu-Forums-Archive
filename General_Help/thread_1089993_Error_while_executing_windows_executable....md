---
title: "Error while executing windows executable..."
date: 2009-03-07
forum: General Help
---

### Post by furqanbhai on 2009-03-07
wine Hadith.exe
fixme:shdocvwersistStreamInit_Load (0x159420)->(0x16255
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -1
fixme:shdocvw:navigate_url Unsupported args (Flags 0x49e414:10; TargetFrameName 0x49e414:10)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dbb4a08, overlapped 0x7dbb49ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x17bef34)
fixmele:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1594bc)->((null) 1 0x32e1cc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1594bc)->((null) 25 2 0x32e1e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1594bc)->((null) 26 2 0x32e1e0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1594bc)->(0x32e21c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1594bc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e2e0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1594bc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e370)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b844b20 (thread 0009), starting debugger...
First chance exception: 0xc0000025 in 32-bit code (0x7bc3b23c).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7bc3b23c ESP:0032ee04 EBP:0032ee68 EFLAGS:00000282( - 00 - -IS1)
EAX:0032ee10 EBX:7bc88444 ECX:00110048 EDX:00000000
ESI:0032f1f4 EDI:0032ee74
Stack dump:
0x0032ee04: 0060776c 0032f26c 00402776 c0000025
0x0032ee14: 00000001 0032f1f4 0060775c 00000000
0x0032ee24: 0040d670 00405a91 6f727245 65722072
0x0032ee34: 6e696461 73252067 73257325 7325203a
0x0032ee44: 7ecfd500 7ed25cf0 0032ee7c 7ecfe2db
0x0032ee54: 0000007c 0011c0d0 0000005c 7bc3b1f0
Backtrace:
=>1 0x7bc3b23c __regs_RtlRaiseException+0x4c() in ntdll (0x0032ee6
2 0x7bc76de3 in ntdll (+0x66de3) (0x0032f1d0)
3 0x7bc3a936 RtlRaiseException+0x6() in ntdll (0x0032f24
4 0x0041334b in hadith (+0x1334b) (0x0032f3b0)
5 0x004134f5 in hadith (+0x134f5) (0x0032f940)
6 0x00412eae in hadith (+0x12eae) (0x0032f960)
7 0x00412e90 in hadith (+0x12e90) (0x0032f970)
8 0x00414a6a in hadith (+0x14a6a) (0x0032f9e0)
9 0x00412f22 in hadith (+0x12f22) (0x0032fa0c)
10 0x00412e90 in hadith (+0x12e90) (0x0032fa1c)
11 0x00414a6a in hadith (+0x14a6a) (0x0032fa4c)
12 0x00412d41 in hadith (+0x12d41) (0x0032faa
13 0x00412f22 in hadith (+0x12f22) (0x0032fad4)
14 0x00412e61 in hadith (+0x12e61) (0x0032faf0)
15 0x00414a6a in hadith (+0x14a6a) (0x0032fb20)
16 0x0042ce4a in hadith (+0x2ce4a) (0x0032fb40)
17 0x00413c8c in hadith (+0x13c8c) (0x0032fbb0)
18 0x00411837 in hadith (+0x11837) (0x0032fbd0)
19 0x0040f7dc in hadith (+0xf7dc) (0x0032fbf4)
20 0x0040f986 in hadith (+0xf986) (0x0032fd14)
21 0x0040fa17 in hadith (+0xfa17) (0x0032fd44)
22 0x0042c806 in hadith (+0x2c806) (0x0032fe9
23 0x004336c8 in hadith (+0x336c (0x0032febc)
24 0x0049b477 in hadith (+0x9b477) (0x0032ff0
25 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe
0x7bc3b23c __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module Address Debug info Name (160 modules)
PE 400000- 4d9000 Export hadith
PE 770000- b0c000 Deferred bukhari32
PE c20000- c89000 Deferred xpcom_core
PE c90000- cb7000 Deferred nspr4
PE cc0000- cc7000 Deferred plc4
PE cd0000- cd6000 Deferred plds4
PE df0000- dff000 Deferred jsd3250
PE e00000- e71000 Deferred js3250
PE e80000- eb5000 Deferred xpc3250
PE ec0000- efe000 Deferred nssckbi
PE f00000- f11000 Deferred mozz
PE f20000- f36000 Deferred gkgfx
PE f40000- f46000 Deferred mozctlx
PE f50000- f8f000 Deferred softokn3
PE f90000- fb0000 Deferred ssl3
PE fb0000- 100b000 Deferred nss3
PE 1010000- 1023000 Deferred jsj3250
PE 1030000- 1061000 Deferred freebl3
PE 1070000- 1084000 Deferred xpcom_compat
PE 1090000- 10aa000 Deferred smime3
PE 10b0000- 10b6000 Deferred xpistub
PE 10c0000- 113d000 Deferred necko
PE 1140000- 114c000 Deferred xppref32
PE 1150000- 117e000 Deferred i18n
PE 1180000- 119f000 Deferred embedcomponents
PE 11a0000- 11af000 Deferred caps
PE 11b0000- 11bc000 Deferred typeaheadfind
PE 11c0000- 1459000 Deferred gklayout
PE 1460000- 1487000 Deferred imglib2
PE 1490000- 14ab000 Deferred rdf
PE 14b0000- 14e8000 Deferred appcomps
PE 1600000- 1610000 Deferred appshell
PE 1610000- 161f000 Deferred profile
PE 1620000- 1627000 Deferred xpcom_compat_c
PE 1630000- 1637000 Deferred sroaming
PE 1640000- 1650000 Deferred chrome
PE 1650000- 1689000 Deferred gkparser
PE 1690000- 174e000 Deferred uconv
PE 1750000- 177c000 Deferred docshell
PE 1780000- 178a000 Deferred nsprefm
PE 1790000- 179e000 Deferred webbrwsr
PE 17a0000- 17c5000 Deferred gkwidget
PE 17d0000- 17f4000 Deferred gkgfxwin
PE 1800000- 1808000 Deferred pipboot
PE 1810000- 181c000 Deferred oji
PE 1820000- 182d000 Deferred jar50
PE 1830000- 184a000 Deferred mork
PE 10000000-10006000 Deferred xpcom
ELF 7b800000-7b92d000 Export kernel32<elf>
\-PE 7b820000-7b92d000 \ kernel32
ELF 7bc00000-7bca4000 Export ntdll<elf>
\-PE 7bc10000-7bca4000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7d67a000-7d690000 Deferred msimtf<elf>
\-PE 7d680000-7d690000 \ msimtf
ELF 7d7a1000-7d7a5000 Deferred libgpg-error.so.0
ELF 7d7a5000-7d7f2000 Deferred libgcrypt.so.11
ELF 7d7f2000-7d802000 Deferred libtasn1.so.3
ELF 7d802000-7d805000 Deferred libkeyutils.so.1
ELF 7d805000-7d80d000 Deferred libkrb5support.so.0
ELF 7d80d000-7d83f000 Deferred libcrypt.so.1
ELF 7d83f000-7d8b5000 Deferred libgnutls.so.13
ELF 7d8b5000-7d8b8000 Deferred libcom_err.so.2
ELF 7d8b8000-7d8db000 Deferred libk5crypto.so.3
ELF 7d8db000-7d968000 Deferred libkrb5.so.3
ELF 7d968000-7d991000 Deferred libgssapi_krb5.so.2
ELF 7d991000-7d9c4000 Deferred libcups.so.2
ELF 7d9c4000-7da6f000 Deferred comdlg32<elf>
\-PE 7d9d0000-7da6f000 \ comdlg32
ELF 7da6f000-7daa5000 Deferred winspool<elf>
\-PE 7da80000-7daa5000 \ winspool
ELF 7ddd8000-7ddec000 Deferred midimap<elf>
\-PE 7dde0000-7ddec000 \ midimap
ELF 7ddec000-7de12000 Deferred msacm32<elf>
\-PE 7ddf0000-7de12000 \ msacm32
ELF 7de12000-7de29000 Deferred msacm32<elf>
\-PE 7de20000-7de29000 \ msacm32
ELF 7de29000-7deec000 Deferred libasound.so.2
ELF 7deff000-7df35000 Deferred winealsa<elf>
\-PE 7df10000-7df35000 \ winealsa
ELF 7df35000-7df9f000 Deferred msvcrt<elf>
\-PE 7df50000-7df9f000 \ msvcrt
ELF 7df9f000-7e031000 Deferred winmm<elf>
\-PE 7dfb0000-7e031000 \ winmm
ELF 7e031000-7e05d000 Deferred ws2_32<elf>
\-PE 7e040000-7e05d000 \ ws2_32
ELF 7e05d000-7e077000 Deferred wsock32<elf>
\-PE 7e060000-7e077000 \ wsock32
ELF 7e077000-7e117000 Deferred mshtml<elf>
\-PE 7e080000-7e117000 \ mshtml
ELF 7e117000-7e138000 Deferred mpr<elf>
\-PE 7e120000-7e138000 \ mpr
ELF 7e138000-7e186000 Deferred wininet<elf>
\-PE 7e140000-7e186000 \ wininet
ELF 7e186000-7e1c5000 Deferred urlmon<elf>
\-PE 7e190000-7e1c5000 \ urlmon
ELF 7e1d0000-7e20c000 Deferred shdocvw<elf>
\-PE 7e1e0000-7e20c000 \ shdocvw
ELF 7e462000-7e475000 Deferred olepro32<elf>
\-PE 7e470000-7e475000 \ olepro32
ELF 7e4c8000-7e4fb000 Deferred uxtheme<elf>
\-PE 7e4d0000-7e4fb000 \ uxtheme
ELF 7e4fb000-7e504000 Deferred libxcursor.so.1
ELF 7e504000-7e509000 Deferred libxfixes.so.3
ELF 7e509000-7e50c000 Deferred libxcomposite.so.1
ELF 7e50c000-7e512000 Deferred libxrandr.so.2
ELF 7e512000-7e51a000 Deferred libxrender.so.1
ELF 7e51a000-7e51d000 Deferred libxinerama.so.1
ELF 7e51d000-7e53d000 Deferred imm32<elf>
\-PE 7e520000-7e53d000 \ imm32
ELF 7e53d000-7e542000 Deferred libxdmcp.so.6
ELF 7e542000-7e55a000 Deferred libxcb.so.1
ELF 7e55a000-7e55c000 Deferred libxcb-xlib.so.0
ELF 7e55c000-7e55f000 Deferred libxau.so.6
ELF 7e55f000-7e646000 Deferred libx11.so.6
ELF 7e646000-7e654000 Deferred libxext.so.6
ELF 7e654000-7e659000 Deferred libxxf86vm.so.1
ELF 7e659000-7e671000 Deferred libice.so.6
ELF 7e671000-7e679000 Deferred libsm.so.6
ELF 7e68c000-7e723000 Deferred winex11<elf>
\-PE 7e6a0000-7e723000 \ winex11
ELF 7e741000-7e762000 Deferred libexpat.so.1
ELF 7e762000-7e78c000 Deferred libfontconfig.so.1
ELF 7e78c000-7e7a1000 Deferred libz.so.1
ELF 7e7a1000-7e80e000 Deferred libfreetype.so.6
ELF 7e80e000-7e867000 Deferred shlwapi<elf>
\-PE 7e820000-7e867000 \ shlwapi
ELF 7e867000-7e97a000 Deferred shell32<elf>
\-PE 7e880000-7e97a000 \ shell32
ELF 7e97a000-7ea39000 Deferred comctl32<elf>
\-PE 7e980000-7ea39000 \ comctl32
ELF 7ea39000-7ea4d000 Deferred lz32<elf>
\-PE 7ea40000-7ea4d000 \ lz32
ELF 7ea4d000-7ea66000 Deferred version<elf>
\-PE 7ea50000-7ea66000 \ version
ELF 7ea66000-7ea79000 Deferred libresolv.so.2
ELF 7ea8c000-7eaaa000 Deferred iphlpapi<elf>
\-PE 7ea90000-7eaaa000 \ iphlpapi
ELF 7eaaa000-7eb0b000 Deferred rpcrt4<elf>
\-PE 7eac0000-7eb0b000 \ rpcrt4
ELF 7eb0b000-7ebaf000 Deferred ole32<elf>
\-PE 7eb20000-7ebaf000 \ ole32
ELF 7ebaf000-7ec51000 Deferred oleaut32<elf>
\-PE 7ebc0000-7ec51000 \ oleaut32
ELF 7ec51000-7eca3000 Deferred advapi32<elf>
\-PE 7ec60000-7eca3000 \ advapi32
ELF 7eca3000-7ed3e000 Deferred gdi32<elf>
\-PE 7ecb0000-7ed3e000 \ gdi32
ELF 7ed3e000-7ee85000 Deferred user32<elf>
\-PE 7ed60000-7ee85000 \ user32
ELF 7efa5000-7efb0000 Deferred libnss_files.so.2
ELF 7efb0000-7efc8000 Deferred libnsl.so.1
ELF 7efc8000-7efed000 Deferred libm.so.6
ELF 7efed000-7eff7000 Deferred libnss_nis.so.2
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
ELF b7d25000-b7d29000 Deferred libdl.so.2
ELF b7d29000-b7e78000 Deferred libc.so.6
ELF b7e79000-b7e91000 Deferred libpthread.so.0
ELF b7ea4000-b7fda000 Deferred libwine.so.1
ELF b7fdc000-b7ff8000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) Z:\media\Islam\The Hadith Software\The Hadith Software\Hadith.exe
00000021 0
00000020 0
0000001f 0
0000001e 0
0000001d 0
0000001c 0
0000001b 0
0000001a 0
00000019 0
00000009 0 <==
0000000c 
00000014 0
00000013 0
00000012 0
0000000e 0
0000000d 0
0000000f 
00000016 0
00000015 0
00000011 0
00000010 0
00000017 
00000018 0
Backtrace:
=>1 0x7bc3b23c __regs_RtlRaiseException+0x4c() in ntdll (0x0032ee6
2 0x7bc76de3 in ntdll (+0x66de3) (0x0032f1d0)
3 0x7bc3a936 RtlRaiseException+0x6() in ntdll (0x0032f24
4 0x0041334b in hadith (+0x1334b) (0x0032f3b0)
5 0x004134f5 in hadith (+0x134f5) (0x0032f940)
6 0x00412eae in hadith (+0x12eae) (0x0032f960)
7 0x00412e90 in hadith (+0x12e90) (0x0032f970)
8 0x00414a6a in hadith (+0x14a6a) (0x0032f9e0)
9 0x00412f22 in hadith (+0x12f22) (0x0032fa0c)
10 0x00412e90 in hadith (+0x12e90) (0x0032fa1c)
11 0x00414a6a in hadith (+0x14a6a) (0x0032fa4c)
12 0x00412d41 in hadith (+0x12d41) (0x0032faa
13 0x00412f22 in hadith (+0x12f22) (0x0032fad4)
14 0x00412e61 in hadith (+0x12e61) (0x0032faf0)
15 0x00414a6a in hadith (+0x14a6a) (0x0032fb20)
16 0x0042ce4a in hadith (+0x2ce4a) (0x0032fb40)
17 0x00413c8c in hadith (+0x13c8c) (0x0032fbb0)
18 0x00411837 in hadith (+0x11837) (0x0032fbd0)
19 0x0040f7dc in hadith (+0xf7dc) (0x0032fbf4)
20 0x0040f986 in hadith (+0xf986) (0x0032fd14)
21 0x0040fa17 in hadith (+0xfa17) (0x0032fd44)
22 0x0042c806 in hadith (+0x2c806) (0x0032fe9
23 0x004336c8 in hadith (+0x336c (0x0032febc)
24 0x0049b477 in hadith (+0x9b477) (0x0032ff0
25 0x7b8773a7 in kernel32 (+0x573a7) (0x0032ffe
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
mohammed@Mohammed-desktop:/media/Islam/The Hadith Software/The Hadith Software$ 
 
 
 
The application "Hadith.exe was previously running well but now its not running and also Noblequran.exe is giving problems now... first it was giving HTML rendering disabled error but now its giving some OLE Error 80004001... Please Help Anyone, Thanks in Advance..."

---

### Post by Rallg on 2009-03-07
You might inquire over at the WINE part of the forum.

---

