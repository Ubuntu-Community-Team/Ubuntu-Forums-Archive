---
title: "wine problems"
date: 2009-05-31
forum: General Help
---

### Post by padeco on 2009-05-31
hi there,
i'm running ubuntu 8.04, and updated wine to 1.1.22. when i try to run winecfg i get the following errors below. also, i have tried to run a modelling program and have had no luck. i can post that also.

any help would be much appreciated,
cheers,
padeco

winecfg
wine: Unhandled page fault on write access to 0x00650170 at address 0x7eea0922 (thread 0014), starting debugger...
Unhandled exception: page fault on write access to 0x00650170 in 32-bit code (0x7eea0922).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eea0922 ESP:0064e6b0 EBP:0064e748 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:006500d0 EBX:7eea210c ECX:00000000 EDX:00001000
 ESI:0065002a EDI:00650000
Stack dump:
0x0064e6b0:  00650000 00001000 00000002 00000000
0x0064e6c0:  00113f90 00000000 00000001 0064e738
0x0064e6d0:  0064e734 00113ea2 006500d0 00001000
0x0064e6e0:  00250000 00650000 0065002a 7bc34cc1
0x0064e6f0:  00000000 0064e730 00110014 7bc3466f
0x0064e700:  00110014 7bc91448 0064e748 7bc43ecf
Backtrace:
=>0 0x7eea0922 in winedevice (+0x10922) (0x0064e748)
  1 0x7eea0f7b in winedevice (+0x10f7b) (0x0064e9e8)
  2 0x7ee55277 in advapi32 (+0x25277) (0x0064ea38)
  3 0x7bc7100e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71362 in ntdll (+0x61362) (0x0064eae8)
  5 0x7bc72405 in ntdll (+0x62405) (0x0064f3d8)
  6 0xb7e784fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
0x7eea0922: movl	$0x0,0xa0(%eax)
Modules:
Module	Address			Debug info	Name (26 modules)
PE	  650000-  6ab000	Deferred        aksfridge.sys
ELF	7b800000-7b944000	Deferred        kernel32<elf>
  \-PE	7b820000-7b944000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ed60000-7ed76000	Deferred        hal<elf>
  \-PE	7ed70000-7ed76000	\               hal
ELF	7ed76000-7ede0000	Deferred        rpcrt4<elf>
  \-PE	7ed80000-7ede0000	\               rpcrt4
ELF	7ede0000-7ee19000	Deferred        ntoskrnl<elf>
  \-PE	7edf0000-7ee19000	\               ntoskrnl
ELF	7ee19000-7ee6d000	Export          advapi32<elf>
  \-PE	7ee30000-7ee6d000	\               advapi32
ELF	7ee6d000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee82000	Deferred        libnss_nis.so.2
ELF	7ee82000-7ee8b000	Deferred        libnss_compat.so.2
ELF	7ee8f000-7eea3000	Export          winedevice<elf>
  \-PE	7ee90000-7eea3000	\               winedevice
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	b7d1f000-b7d23000	Deferred        libdl.so.2
ELF	b7d23000-b7e72000	Deferred        libc.so.6
ELF	b7e73000-b7e8b000	Export          libpthread.so.0
ELF	b7ea3000-b7fde000	Deferred        libwine.so.1
ELF	b7fe0000-b7ffc000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f (D) C:\windows\system32\winedevice.exe
	00000014    0 <==
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x7eea0922 in winedevice (+0x10922) (0x0064e748)
  1 0x7eea0f7b in winedevice (+0x10f7b) (0x0064e9e8)
  2 0x7ee55277 in advapi32 (+0x25277) (0x0064ea38)
  3 0x7bc7100e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71362 in ntdll (+0x61362) (0x0064eae8)
  5 0x7bc72405 in ntdll (+0x62405) (0x0064f3d8)
  6 0xb7e784fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
wine: Call from 0x7b843b46 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeMutex called at address 0x7b843b46 (thread 001d), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeMutex called in 32-bit code (0x7b843b46).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b843b46 ESP:0064e5c4 EBP:0064e628 EFLAGS:00000212(   - --  I   -A- - )
 EAX:7b82eb11 EBX:7b8b37f8 ECX:00000000 EDX:0064e64c
 ESI:0064e64c EDI:0064e724
Stack dump:
0x0064e5c4:  0064e64c 00000008 00003000 006dc3c0
0x0064e5d4:  80000100 00000001 00000000 7b843b46
0x0064e5e4:  00000002 7ee00ce0 7ee03a99 0064e71c
0x0064e5f4:  006dd750 006dc008 0064e648 00003000
0x0064e604:  006de34c 006de34c 006dde20 0000004c
0x0064e614:  0064e614 006da8ae 0064e71c 006da930
Backtrace:
=>0 0x7b843b46 in kernel32 (+0x23b46) (0x0064e628)
  1 0x7ee00c86 in ntoskrnl (+0x10c86) (0x0064e658)
  2 0x7edf9a54 in ntoskrnl (+0x9a54) (0x0064e748)
  3 0x7eea1074 in winedevice (+0x11074) (0x0064e9e8)
  4 0x7ee55277 in advapi32 (+0x25277) (0x0064ea38)
  5 0x7bc7100e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  6 0x7bc71362 in ntdll (+0x61362) (0x0064eae8)
  7 0x7bc72405 in ntdll (+0x62405) (0x0064f3d8)
  8 0xb7e094fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
0x7b843b46: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (26 modules)
PE	  650000-  6df000	Deferred        hardlock.sys
ELF	7b800000-7b944000	Export          kernel32<elf>
  \-PE	7b820000-7b944000	\               kernel32
ELF	7bc00000-7bcad000	Export          ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ed60000-7ed76000	Deferred        hal<elf>
  \-PE	7ed70000-7ed76000	\               hal
ELF	7ed76000-7ede0000	Deferred        rpcrt4<elf>
  \-PE	7ed80000-7ede0000	\               rpcrt4
ELF	7ede0000-7ee19000	Export          ntoskrnl<elf>
  \-PE	7edf0000-7ee19000	\               ntoskrnl
ELF	7ee19000-7ee6d000	Export          advapi32<elf>
  \-PE	7ee30000-7ee6d000	\               advapi32
ELF	7ee6d000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee82000	Deferred        libnss_nis.so.2
ELF	7ee82000-7ee8b000	Deferred        libnss_compat.so.2
ELF	7ee8f000-7eea3000	Export          winedevice<elf>
  \-PE	7ee90000-7eea3000	\               winedevice
ELF	7efc3000-7efe8000	Deferred        libm.so.6
ELF	7efe8000-7f000000	Deferred        libnsl.so.1
ELF	b7cb0000-b7cb4000	Deferred        libdl.so.2
ELF	b7cb4000-b7e03000	Deferred        libc.so.6
ELF	b7e04000-b7e1c000	Export          libpthread.so.0
ELF	b7e34000-b7f6f000	Deferred        libwine.so.1
ELF	b7f71000-b7f8d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	0000001e    0
	0000001c    0
	00000013    0
	0000000e    0
	0000000d    0
00000017 
	00000018    0
00000019 (D) C:\windows\system32\winedevice.exe
	0000001d    0 <==
	0000001b    0
	0000001a    0
Backtrace:
=>0 0x7b843b46 in kernel32 (+0x23b46) (0x0064e628)
  1 0x7ee00c86 in ntoskrnl (+0x10c86) (0x0064e658)
  2 0x7edf9a54 in ntoskrnl (+0x9a54) (0x0064e748)
  3 0x7eea1074 in winedevice (+0x11074) (0x0064e9e8)
  4 0x7ee55277 in advapi32 (+0x25277) (0x0064ea38)
  5 0x7bc7100e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  6 0x7bc71362 in ntdll (+0x61362) (0x0064eae8)
  7 0x7bc72405 in ntdll (+0x62405) (0x0064f3d8)
  8 0xb7e094fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
wine: Call from 0x7b843b46 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
wine: Call from 0x7b843b46 to unimplemented function ntoskrnl.exe.KeInitializeMutex, aborting
fixme:vxd:VXD_Open Unknown/unsupported VxD L"usbpdcom.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:win:RegisterDeviceNotificationA (hwnd=0x127cb0, filter=0xdae8c0,flags=0x00000001),
	returns a fake device notification handle!
fixme:advapi:RegisterEventSourceA ((null),"hasplms"): stub
fixme:advapi:RegisterEventSourceW (L"",L"hasplms"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x40070001,(nil),0x0002,0x00000000,0xdae7a8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x40070001,(nil),0x0002,0x00000000,0x1320e0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"fentedev.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"aksdf.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"aksfridge.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"aksfridge.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:advapi:RegisterEventSourceA ((null),"hasplms"): stub
fixme:advapi:RegisterEventSourceW (L"",L"hasplms"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x40070001,(nil),0x0002,0x00000000,0xeae3e0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x40070001,(nil),0x0002,0x00000000,0x12d670,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"aksfridge.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"aksfridge.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:winsock:WS_setsockopt Unknown level: 0x00000029

---

