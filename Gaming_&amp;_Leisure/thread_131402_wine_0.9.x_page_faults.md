---
title: "wine 0.9.x page faults"
date: 2006-02-16
forum: Gaming &amp; Leisure
---

### Post by damiencc on 2006-02-16
Dear All,

I run wine 0.9.7 with fglrx 8.22.5 driver, tls disabled.

When I start wine for the first time, it crashes with the following messages:

wine: creating configuration directory '/home/damien/.wine'...
wine: Unhandled page fault on read access to 0x1008002f at address 0x7bebd5be (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x1008002f in 32-bit code (0x7bebd5be).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:ffff GS:0033
 EIP:7bebd5be ESP:7fc1d5c0 EBP:7fc1d5d8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7bef37f0 ECX:00000002 EDX:ffffffff
 ESI:1007ffff EDI:7ff2d740
Stack dump:
0x00000000:  00000000 00000000 00000000 00000000
0x00000010:  00000000 00000000 00000000 00000000
0x00000020:  00000000 00000000 00000000 00000000
0x00000030:  00000000 00000000 00000000 00000000
0x00000040:  00000000 00000000 00000000 00000000
0x00000050:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x7bebd5be in ntdll (+0x1d5be) (0x7bebd5be)
  2 0x7bebfd87 LdrLoadDll+0x87 in ntdll (0x7bebfd87)
  3 0x7fdef1a0 in kernel32 (+0x3f1a0) (0x7fdef1a0)
  4 0x7fdef32f LoadLibraryExW+0x4f in kernel32 (0x7fdef32f)
  5 0x7e61f918 in setupapi (+0xf918) (0x7e61f918)
  6 0x7e61e938 in setupapi (+0xe938) (0x7e61e938)
  7 0x7e61eb9d SetupInstallFromInfSectionW+0x11d in setupapi (0x7e61eb9d)
  8 0x7e61f5ae InstallHinfSectionW+0x1de in setupapi (0x7e61f5ae)
  9 0x7fc3e5c4 main+0x334 in rundll32 (0x7fc3e5c4)
  10 0x7fc3eb7e in rundll32 (+0xeb7e) (0x7fc3eb7e)
  11 0x7fdfc114 in kernel32 (+0x4c114) (0x7fdfc114)
  12 0x4f37ee67 wine_switch_to_stack+0x17 in libwine.so.1 (0x4f37ee67)
0x7bebd5be: movl        0x30(%esi),%eax

and then many deffered messages.

This kind of crash happens also whenever I run a program that uses opengl, such as BillardGL. And yes, if I set a version in winecfg, wine still crashes in the same way. Any idea ?

Thanks

Damien

---

### Post by davy2002a on 2006-08-24
I too have that problem, don't seem related to audio tab either since winecfg itself crashes on execution, but I have that gut feeling its GL-related since I lost at least partially my GL (some reason Tremulous don't want to use GL anymore) so there must be some corrolation...

---

### Post by damiencc on 2006-08-25
I have solved the problem by adding 

        Option      "UseFastTLS" "2"

to xorg.conf.

---

