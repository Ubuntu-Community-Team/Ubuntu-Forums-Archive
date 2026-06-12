---
title: "wine not opening any application"
date: 2009-02-03
forum: General Help
---

### Post by stmartin on 2009-02-03
Hello!

I used wine on Ubuntu 8.04 and it worked perfectly.

But now, on fresh install of Ubuntu 8.10 I can't get any application start using wine.

For example simple application as mspaint.exe

here is the output from the terminal:

```
fixme:advapi:RegisterEventSourceA ((null),"System"): stub
fixme:advapi:RegisterEventSourceW (L"",L"System"): stub
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.KeInitializeSemaphore, aborting
wine: Unimplemented function ntoskrnl.exe.KeInitializeSemaphore called at address 0x7b845450 (thread 0023), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.KeInitializeSemaphore called in 32-bit code (0x7b8454c3).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b8454c3 ESP:7ec29840 EBP:7ec298a4 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecb9 EBX:7b8b7ff4 ECX:00000000 EDX:7ec298cc
 ESI:7ec298cc EDI:7edeb7a8
Stack dump:
0x7ec29840:  7ec298cc 00000008 0000003c 80000100
0x7ec29850:  00000001 00000000 7b845450 00000002
0x7ec29860:  7edf1b40 7edf4a94 001117e0 00000000
0x7ec29870:  00110000 00000002 00000000 00000000
0x7ec29880:  00000000 00110014 7edfbff4 00000000
0x7ec29890:  000001fc 7ec298c4 7b84545a 7fffffff
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec298a4)
  2 0x7edf1ad5 in ntoskrnl (+0x11ad5) (0x7ec298d4)
  3 0x7edeb7cc in ntoskrnl (+0xb7cc) (0x7ec29918)
  4 0x7ee6ef79 in winedevice (+0xef79) (0x7ec299d8)
  5 0x7ee45aa4 in advapi32 (+0x25aa4) (0x7ec29a28)
  6 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec29a38)
  7 0x7bc6df42 in ntdll (+0x5df42) (0x7ec29ad8)
  8 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec2a3c8)
  9 0xb7e9150f start_thread+0xbf() in libpthread.so.0 (0x7ec2a4c8)
  10 0xb7e0d7ee __clone+0x5e() in libc.so.6 (0x00000000)
0x7b8454c3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  454580	Deferred        ckldrv.sys
ELF	7b800000-7b93d000	Export          kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Export          ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7ea98000-7eaae000	Deferred        hal<elf>
  \-PE	7eaa0000-7eaae000	\               hal
ELF	7eaae000-7eb1a000	Deferred        msvcrt<elf>
  \-PE	7eac0000-7eb1a000	\               msvcrt
ELF	7ec2b000-7ec3f000	Deferred        libresolv.so.2
ELF	7ec3f000-7ec5e000	Deferred        iphlpapi<elf>
  \-PE	7ec50000-7ec5e000	\               iphlpapi
ELF	7ec5e000-7ecc1000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecc1000	\               rpcrt4
ELF	7edd2000-7ee0a000	Export          ntoskrnl<elf>
  \-PE	7ede0000-7ee0a000	\               ntoskrnl
ELF	7ee0a000-7ee5d000	Export          advapi32<elf>
  \-PE	7ee20000-7ee5d000	\               advapi32
ELF	7ee5d000-7ee72000	Export          winedevice<elf>
  \-PE	7ee60000-7ee72000	\               winedevice
ELF	7ee72000-7ee7e000	Deferred        libnss_files.so.2
ELF	7ee7e000-7ee97000	Deferred        libnsl.so.1
ELF	7ee97000-7eea0000	Deferred        libnss_compat.so.2
ELF	7efcd000-7eff3000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d28000-b7d2c000	Deferred        libdl.so.2
ELF	b7d2c000-b7e8a000	Export          libc.so.6
ELF	b7e8b000-b7ea4000	Export          libpthread.so.0
ELF	b7eb1000-b7fe8000	Deferred        libwine.so.1
ELF	b7fea000-b8007000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000022    0
	0000001c    0
	00000015    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	0000001a    0
	00000019    0
	00000018    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001e    0
	0000001d    0
	0000001b    0
	00000017    0
0000001f (D) C:\windows\system32\winedevice.exe
	00000023    0 <==
	00000021    0
	00000020    0
Backtrace:
=>1 0x7b8454c3 in kernel32 (+0x254c3) (0x7ec298a4)
  2 0x7edf1ad5 in ntoskrnl (+0x11ad5) (0x7ec298d4)
  3 0x7edeb7cc in ntoskrnl (+0xb7cc) (0x7ec29918)
  4 0x7ee6ef79 in winedevice (+0xef79) (0x7ec299d8)
  5 0x7ee45aa4 in advapi32 (+0x25aa4) (0x7ec29a28)
  6 0x7bc6c91e call_thread_entry_point+0xe() in ntdll (0x7ec29a38)
  7 0x7bc6df42 in ntdll (+0x5df42) (0x7ec29ad8)
  8 0x7bc6e13d in ntdll (+0x5e13d) (0x7ec2a3c8)
  9 0xb7e9150f start_thread+0xbf() in libpthread.so.0 (0x7ec2a4c8)
  10 0xb7e0d7ee __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.KeInsertByKeyDeviceQueue, aborting
wine: Call from 0x7b845450 to unimplemented function ntoskrnl.exe.KeInsertDeviceQueue, aborting
wine: could not load L"C:\\windows\\system32\\mspaint.exe": Module not found

```

I am using Vista dual boot with Ubuntu.

Does that makes any difference?

Where does the Ubuntu takes the .dlls from?

Thanks in advance.

Regards.

---

### Post by stmartin on 2009-02-04
Bump!

---

