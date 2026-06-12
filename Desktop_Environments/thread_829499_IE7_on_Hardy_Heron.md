---
title: "IE7 on Hardy Heron"
date: 2008-06-14
forum: Desktop Environments
---

### Post by Kat of Zion on 2008-06-14
Hello

I just recently upgraded Kubuntu to Hardy Heron from Feisty.  One thing I noticed that is not working correctly after upgrade, is my Wine version of IE7.  Originally it was installed by IEs4linux and worked gorgeously.  Now it opens the browser but it no longer can connect to a webpage.  I simply get a blank page and it has a progress bar on the bottom like it is trying ot reach the site, but then never gives me a page nor comes back with "server not found" or any other "page not available error". I have tried to access a site like google to see if it is just a small bug, but no avail.

What happened?  Is this Hardy's problem with IE7?  Or, was this a problem in Gutsy as well?  Could IE7 not be playing well with Hardy?  If IE7 truly is something that Hardy users are SOL on, please let me know of some alternatives to help me test for IE7.  One thread that I did find useful (but didnt want to bump due to forum etiquette) is this:
[http://ubuntuforums.org/showthread.php?t=516513&highlight=web+design+ie7](http://ubuntuforums.org/showthread.php?t=516513&highlight=web+design+ie7)

You may wonder why I am so frustrated, especially about IE7 (blargh!), but I am a web designer and this is why running IE7 is so necessary and why it is all the more frustrating because IE7 did work at one time and now does not. :(

---

### Post by tobestool on 2008-08-05
I have the same problem, which is annoying as I've just asked to look into an IE7 specific bug.

Did you (or anyone else) resolve this problem?

Thanks

P.S. I used the latest ie4linux (2.99.0.1) and I have Wine version 1.1.2, but have a report of a similar problem from an Ubuntu user with Wine 1.0.

---

### Post by Kat of Zion on 2008-08-05
> **tobestool said:**
> I have the same problem, which is annoying as I've just asked to look into an IE7 specific bug.

Did you (or anyone else) resolve this problem?

Thanks

P.S. I used the latest ie4linux (2.99.0.1) and I have Wine version 1.1.2, but have a report of a similar problem from an Ubuntu user with Wine 1.0.

No resolution as of yet over here. *sigh*

---

### Post by TylerRick on 2008-09-03
> **Kat of Zion said:**
> Hello
Now it opens the browser but it no longer can connect to a webpage.  I simply get a blank page and it has a progress bar on the bottom like it is trying ot reach the site, but then never gives me a page nor comes back with "server not found" or any other "page not available error". I have tried to access a site like google to see if it is just a small bug, but no avail.


Yeah, I am experiencing the same thing. Only difference is I never tried it when I was on Gutsy, so I've never had it working. But I can sure confirm that it's not working now!

ies4linux-2.99.0.1
wine-1.0

Sure would be nice to have though for testing our web sites! Anyone found a solution to this yet (or even figured out what the problem is)?

---

### Post by pvincent on 2008-09-29
Same problem here.

xubuntu 8.04.1
wine 1.1.5
ies4linux 2.99.0.1

IE6 does work, but never ends properly. CPU almost 100%.
I need to do 'pkill -9 wineserver' to stop the fan and let the cpu slowing down.

IE7 opens its frame but never displays html pages.

---

### Post by pvincent on 2008-09-29
I ran IE7 with 'export DEBUG=true'

here are the stacktrace:

```
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
err:shell:ReadCabinetState Initializing shell cabinet settings
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:toolbar:TOOLBAR_CheckStyle [0x10038] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10038] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10038,0x00008003,0x00008000,0x0000c076,0x00000001,0x33de18):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10038, wParam=0x00000000, size.cx=1280, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10038] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10038] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x1003e wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_SetExtendedStyle Unknown Toolbar Extended Style 0x00000080. Please report.
fixme:advapi:CheckTokenMembership ((nil) 0x147168 0x33dc80) stub!
fixme:dpa:DPA_LoadStream phDpa=0x33d854 loadProc=0xbaba1c pStream=0x14d548 lParam=14d5d8
fixme:dpa:DPA_LoadStream dwSize=0 dwData2=0 dwItems=0
fixme:dpa:DPA_LoadStream new hDpa=0x14d580, errorcode=80004005
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10054, wParam=0x00000000, size.cx=1280, size.cy=1020 stub!
fixme:shell:NTSHChangeNotifyRegister (0x10054,0x00008003,0x0c02b7ff,0x0000c076,0x00000001,0x33de58):semi stub.
fixme:advapi:RegisterTraceGuidsA 0x7721212f 0x7724bfc0 0x771da48c 1 0x33b9a8 (null) (null) 0x7724bfc8
fixme:advapi:RegisterTraceGuidsA 0x7721212f 0x7724bfe0 0x771da49c 1 0x33b9a8 (null) (null) 0x7724bfe8
fixme:advapi:CheckTokenMembership ((nil) 0x150178 0x33b9a0) stub!
fixme:advapi:ParseStringSidToSid String constant not supported: L"LW"
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x162410,0x7de778e4,0x154714),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x162410,0x7de7759c,0x15478c),stub!
fixme:winsock:WSALookupServiceBeginW (0x7de778f0 0x00000210 0x152fa8) Stub!
fixme:advapi:ParseStringSidToSid String constant not supported: L"LW"
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x164e68,0x7de77404,0x164d54),stub!
fixme:shell:DllGetClassObject failed for CLSID=
{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:shell:NTSHChangeNotifyRegister (0x1002c,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x33ea88):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x16d6c8,0x7de77404,0x169c5c),stub!
fixme:shell:DllGetClassObject failed for CLSID=
{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:heap:HeapSetInformation 0x110000 0 0x33b294 4
fixme:advapi:RegisterTraceGuidsW 0x11dd52d 0x12e6320 0xff4fd8 1 0x33b1ec (null) (null) 0x12e6328
fixme:advapi:RegisterTraceGuidsW 0x11dd52d 0x12e6340 0xff4fe8 1 0x33b1ec (null) (null) 0x12e6348
fixme:shell:DllGetClassObject failed for CLSID=
{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x19c028,0x7dd668e4,0x19bf14),stub!
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x19c460,0x7dd66404,0x19c34c),stub!
fixme:shell:DllGetClassObject failed for CLSID=
{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
{a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
{a07034fd-6caa-4954-ac3f-97a27216f98a} (unknown)
fixme:shell:DllGetClassObject failed for CLSID=
{871c5380-42a0-1069-a2ea-08002b30309d} (unknown)
fixme:win:GetProcessDefaultLayout ( 0x33d2c8 ): No BiDi
fixme:win:GetProcessDefaultLayout ( 0x33d2c8 ): No BiDi
fixme:ras:RasConnectionNotificationW (0xffffffff,0x174,0x00000003),stub!
fixme:ras:RasEnumEntriesW ((nil),(null),0x1b0330,0x7dc3c8e4,0x1a9a6c),stub!
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.I_RpcExceptionFilter
wine: Call from 0x7b844f90 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
wine: Unimplemented function rpcrt4.dll.I_RpcExceptionFilter called at address 0x7b844f90 (thread 0013), starting debugger...
Unhandled exception: unimplemented function rpcrt4.dll.I_RpcExceptionFilter called in 32-bit code (0x7b845006).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7b845006 ESP:7dc3bf74 EBP:7dc3bfd8 EFLAGS:00200212( - 00 - -IA1)
EAX:7b82eddd EBX:7b8b4f28 ECX:00000000 EDX:7ec2d173
ESI:7ec2d173 EDI:7ec2d168
Stack dump:
0x7dc3bf74: 7dc3c004 00000008 7b8ad794 7ec2d173
0x7dc3bf84: 80000100 00000001 00000000 7b844f90
0x7dc3bf94: 00000002 7ec2d168 7ec2d173 00000001
0x7dc3bfa4: 7b93a030 7b8ad794 7b8ad6d9 7dc3bff0
0x7dc3bfb4: ffffffff 001105d0 7dc3bfd8 00000000
0x7dc3bfc4: 00000000 00000000 7dc3bff0 7b8b4f28
Backtrace:
=>1 0x7b845006 in kernel32 (+0x25006) (0x7dc3bfd8)
2 0x7b86633b DelayLoadFailureHook+0x5b() in kernel32 (0x7dc3c018)
3 0x7ec1f7a5 in advapi32 (+0x2f7a5) (0x7dc3c038)
4 0x7ebf59e0 in advapi32 (+0x59e0) (0x7dc3c058)
5 0x7ec146ea in advapi32 (+0x246ea) (0x7dc3c088)
6 0x7bc64f85 call_exception_handler+0x29() in ntdll (0x7dc3c0b8)
7 0x7bc64f57 EXC_CallHandler+0x1b() in ntdll (0x7dc3c0d8)
8 0x7bc3b80e in ntdll (+0x2b80e) (0x7dc3c158)
9 0x7bc3b929 __regs_RtlRaiseException+0x29() in ntdll (0x7dc3c1c8)
10 0x7bc78883 in ntdll (+0x68883) (0x7dc3c524)
11 0x7bc3b046 RtlRaiseException+0x6() in ntdll (0x7dc3c59c)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "rpcrt4.dbg" ("")
12 0x7010a6d7 in rpcrt4 (+0xa6d7) (0x7dc3c7bc)
13 0x7ec1783c OpenSCManagerW+0xbc() in advapi32 (0x7dc3c8ac)
14 0x7ec188ac OpenSCManagerA+0x15c() in advapi32 (0x7dc3c8dc)
15 0x771c8859 in wininet (+0x18859) (0x7dc3c918)
16 0x771d419a in wininet (+0x2419a) (0x7dc3c934)
17 0x771d4151 in wininet (+0x24151) (0x7dc3c948)
18 0x771bcabb in wininet (+0xcabb) (0x7dc3c960)
19 0x771bccb1 in wininet (+0xccb1) (0x7dc3c978)
20 0x771bc949 in wininet (+0xc949) (0x7dc3c990)
21 0x771bca35 in wininet (+0xca35) (0x7dc3c9c0)
22 0x77f69548 in shlwapi (+0x9548) (0x7dc3c9d8)
23 0x7bc6ed70 in ntdll (+0x5ed70) (0x7dc3ca38)
24 0x7bc6bafe call_thread_entry_point+0xe() in ntdll (0x7dc3ca48)
25 0x7bc6c192 in ntdll (+0x5c192) (0x7dc3cae8)
26 0x7bc6c3c2 in ntdll (+0x5c3c2) (0x7dc3d3d8)
27 0xb7dee4fb start_thread+0xcb() in libpthread.so.0 (0x7dc3d4c8)
0x7b845006: movl 0xfffffffc(%ebp),%ebx
Modules:
Module Address Debug info Name (83 modules)
PE 3d0000- 3e2000 Deferred browselc
PE 400000- 419000 Deferred iexplore
PE 530000- 679000 Deferred shdocvw
PE b90000- c8d000 Deferred browseui
PE e30000- e39000 Deferred normaliz
PE e70000- f94000 Deferred urlmon
PE fe0000- 134f000 Deferred mshtml
PE 10000000-10007000 Deferred rpcltc1
PE 48080000-480a7000 Deferred msls31
PE 5dca0000-5dce5000 Deferred iertutil
PE 63380000-633f8000 Deferred jscript
PE 65340000-653d2000 Deferred oleaut32
PE 65f00000-65fc2000 Deferred ole32
PE 70100000-70153000 Export rpcrt4
PE 70440000-704cf000 Deferred mlang
PE 71840000-718c4000 Deferred shdoclc
PE 771b0000-7727e000 Export wininet
PE 77f60000-77fd6000 Export shlwapi
ELF 7b800000-7b93c000 Export kernel32<elf>
-PE 7b820000-7b93c000 kernel32
ELF 7bc00000-7bca6000 Export ntdll<elf>
-PE 7bc10000-7bca6000 ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7daec000-7db05000 Deferred version<elf>
-PE 7daf0000-7db05000 version
ELF 7db05000-7db1a000 Deferred psapi<elf>
-PE 7db10000-7db1a000 psapi
ELF 7db1a000-7db2d000 Deferred libresolv.so.2
ELF 7dc3e000-7dc57000 Deferred rasapi32<elf>
-PE 7dc40000-7dc57000 rasapi32
ELF 7df8a000-7dfb6000 Deferred ws2_32<elf>
-PE 7df90000-7dfb6000 ws2_32
ELF 7e5f9000-7e60d000 Deferred lz32<elf>
-PE 7e600000-7e60d000 lz32
ELF 7e676000-7e790000 Deferred shell32<elf>
-PE 7e690000-7e790000 shell32
ELF 7e790000-7e7c3000 Deferred uxtheme<elf>
-PE 7e7a0000-7e7c3000 uxtheme
ELF 7e7c3000-7e884000 Deferred comctl32<elf>
-PE 7e7d0000-7e884000 comctl32
ELF 7e884000-7e88d000 Deferred libxcursor.so.1
ELF 7e88d000-7e892000 Deferred libxfixes.so.3
ELF 7e892000-7e895000 Deferred libxcomposite.so.1
ELF 7e895000-7e89b000 Deferred libxrandr.so.2
ELF 7e89b000-7e8a3000 Deferred libxrender.so.1
ELF 7e8a3000-7e8a8000 Deferred libxxf86vm.so.1
ELF 7e8a8000-7e8c8000 Deferred imm32<elf>
-PE 7e8b0000-7e8c8000 imm32
ELF 7e8c8000-7e8cd000 Deferred libxdmcp.so.6
ELF 7e8cd000-7e8e5000 Deferred libxcb.so.1
ELF 7e8e5000-7e9cc000 Deferred libx11.so.6
ELF 7e9cc000-7e9da000 Deferred libxext.so.6
ELF 7e9da000-7e9f2000 Deferred libice.so.6
ELF 7e9f2000-7e9fa000 Deferred libsm.so.6
ELF 7e9fa000-7ea00000 Deferred libnss_dns.so.2
ELF 7ea00000-7ea03000 Deferred libnss_mdns4_minimal.so.2
ELF 7ea08000-7eaa0000 Deferred winex11<elf>
-PE 7ea20000-7eaa0000 winex11
ELF 7eaf1000-7eb12000 Deferred libexpat.so.1
ELF 7eb12000-7eb3c000 Deferred libfontconfig.so.1
ELF 7eb3d000-7eb40000 Deferred libxinerama.so.1
ELF 7eb4a000-7eb5f000 Deferred libz.so.1
ELF 7eb5f000-7ebcc000 Deferred libfreetype.so.6
ELF 7ebda000-7ec2e000 Export advapi32<elf>
-PE 7ebf0000-7ec2e000 advapi32
ELF 7ec2e000-7eccc000 Deferred gdi32<elf>
-PE 7ec40000-7eccc000 gdi32
ELF 7eccc000-7ee15000 Deferred user32<elf>
-PE 7ecf0000-7ee15000 user32
ELF 7ee15000-7ee7f000 Deferred msvcrt<elf>
-PE 7ee30000-7ee7f000 msvcrt
ELF 7efa0000-7efab000 Deferred libnss_files.so.2
ELF 7efab000-7efb5000 Deferred libnss_nis.so.2
ELF 7efb5000-7efcd000 Deferred libnsl.so.1
ELF 7efcd000-7eff2000 Deferred libm.so.6
ELF 7eff2000-7eff4000 Deferred libxcb-xlib.so.0
ELF 7eff4000-7eff7000 Deferred libxau.so.6
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
ELF b7c95000-b7c99000 Deferred libdl.so.2
ELF b7c99000-b7de8000 Deferred libc.so.6
ELF b7de9000-b7e01000 Export libpthread.so.0
ELF b7e0f000-b7f45000 Deferred libwine.so.1
ELF b7f47000-b7f63000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:Program FilesInternet ExplorerIEXPLORE.EXE
00000014 0
00000013 0 <==
00000012 0
00000011 0
00000010 0
00000009 0
0000000e
0000000f 0
Backtrace:
=>1 0x7b845006 in kernel32 (+0x25006) (0x7dc3bfd8)
2 0x7b86633b DelayLoadFailureHook+0x5b() in kernel32 (0x7dc3c018)
3 0x7ec1f7a5 in advapi32 (+0x2f7a5) (0x7dc3c038)
4 0x7ebf59e0 in advapi32 (+0x59e0) (0x7dc3c058)
5 0x7ec146ea in advapi32 (+0x246ea) (0x7dc3c088)
6 0x7bc64f85 call_exception_handler+0x29() in ntdll (0x7dc3c0b8)
7 0x7bc64f57 EXC_CallHandler+0x1b() in ntdll (0x7dc3c0d8)
8 0x7bc3b80e in ntdll (+0x2b80e) (0x7dc3c158)
9 0x7bc3b929 __regs_RtlRaiseException+0x29() in ntdll (0x7dc3c1c8)
10 0x7bc78883 in ntdll (+0x68883) (0x7dc3c524)
11 0x7bc3b046 RtlRaiseException+0x6() in ntdll (0x7dc3c59c)
12 0x7010a6d7 in rpcrt4 (+0xa6d7) (0x7dc3c7bc)
13 0x7ec1783c OpenSCManagerW+0xbc() in advapi32 (0x7dc3c8ac)
14 0x7ec188ac OpenSCManagerA+0x15c() in advapi32 (0x7dc3c8dc)
15 0x771c8859 in wininet (+0x18859) (0x7dc3c918)
16 0x771d419a in wininet (+0x2419a) (0x7dc3c934)
17 0x771d4151 in wininet (+0x24151) (0x7dc3c948)
18 0x771bcabb in wininet (+0xcabb) (0x7dc3c960)
19 0x771bccb1 in wininet (+0xccb1) (0x7dc3c978)
20 0x771bc949 in wininet (+0xc949) (0x7dc3c990)
21 0x771bca35 in wininet (+0xca35) (0x7dc3c9c0)
22 0x77f69548 in shlwapi (+0x9548) (0x7dc3c9d8)
23 0x7bc6ed70 in ntdll (+0x5ed70) (0x7dc3ca38)
24 0x7bc6bafe call_thread_entry_point+0xe() in ntdll (0x7dc3ca48)
25 0x7bc6c192 in ntdll (+0x5c192) (0x7dc3cae8)
26 0x7bc6c3c2 in ntdll (+0x5c3c2) (0x7dc3d3d8)
27 0xb7dee4fb start_thread+0xcb() in libpthread.so.0 (0x7dc3d4c8)
```

---

### Post by jf812 on 2008-09-29
Why are you trying to use IE?

---

### Post by Le-Froid on 2008-09-29
> **jf812 said:**
> Why are you trying to use IE?

Around 65% of the people using web browsers use IE (usually not knowing other browsers exist). IE doesn't comply with web standards and people have to test their website on IE to make sure it works, or to find out how to make their site work on IE.

---

### Post by dangermouse28 on 2008-09-30
Struggled with this one for a while. Ies4linux is probably the closest anyone's got to having IE7 working on linux, but even there, there's a whole load of if's and but's.

I eventually "solved" it by installing Virtualbox and creating a virtual XP machine. Inside that environment I have IE6, 7 and 8 (beta) for testing websites.

Not great, but hey - it gets the job done!

---

### Post by josue on 2010-03-11
I just want to add that I am experiencing this very issue on Karmic.

SEtting up Virtualbox for now but I would love to get around that.

---

