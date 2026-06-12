---
title: "War3 Lastest patch??"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by Hack4ev3r on 2005-10-21
Hey, i'm useing Cedega 4.4.2-1 and i installed warcraft3 everything works but i want to play on bnet so i downloaded the patch and the patch just wont open :'( 

running cedega War3ROC_120a_English

gave me this

```

tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  40380260 00000017 40380260 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 403802c0 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 40380260
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  40380260 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$ cedega
usage: cedega [-use-pthreads <yes/no>] [[-]-winver <version>] [[-]-debugmsg <debug>] [[-]-version] [[-]-use-dos-cwd <dir>] [[-]monitor-cdrom-eject] <application> [application parameters]

If you require additional help, please refer the HOWTO guide in the downloads section of the subscribers area.
tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English -opengl
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  403802a4 00000017 403802a4 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 40380304 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 403802a4
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  403802a4 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English -clasic
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  403802a4 00000017 403802a4 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 40380304 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 403802a4
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  403802a4 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English -win98
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  403802a0 00000017 403802a0 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 40380300 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 403802a0
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  403802a0 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$ ckear
bash: ckear: command not found
tommy@bzq-82-81-196-144:~/Desktop$ clear

tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English -win98
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  403802a0 00000017 403802a0 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 40380300 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 403802a0
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  403802a0 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$ clear

tommy@bzq-82-81-196-144:~/Desktop$ cedega War3ROC_120a_English -win98
wine: Unhandled exception, starting debugger...
Warning: Language 'en_IL' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000ba41
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40019000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022d000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x4035b000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x4036d000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in 32bit DLL 'D:\Desktop\War3ROC_120a_English.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40057000)
Unhandled exception: page fault on read access to 0x0041e1c8 in 32-bit code (0x4008cfa8).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:4008cfa8 ESP:407f2174 EBP:407f21b8 EFLAGS:00010246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40104428 ECX:00400000 EDX:400fee92
 ESI:0041e1bc EDI:0041e1bc
Stack dump:
0x407f2174 (NTDLL.DLL.memcpy+0x559954):  00000000 40380000 40380000 40104428
0x407f2184 (NTDLL.DLL.memcpy+0x559964):  403802a0 00000017 403802a0 00000017
0x407f2194 (NTDLL.DLL.memcpy+0x559974):  40089519 40380300 0000005c 00000001
0x407f21a4 (NTDLL.DLL.memcpy+0x559984):  00000000 00400000 40104428 00000000
0x407f21b4 (NTDLL.DLL.memcpy+0x559994):  004000f8 407f224c 4008dbae 403802a0
0x407f21c4 (NTDLL.DLL.memcpy+0x5599a4):  403802a0 00000000 00000000 00000000
0x407f21d4 (NTDLL.DLL.memcpy+0x5599b4):

Backtrace:
=>0 0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so) (ebp=407f21b8)
  1 0x4008dbae (NTDLL.DLL.__wine_call_from_32_regs+0x1c16a in libntdll.so) (ebp=407f224c)
  2 0x400cb352 (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=407f2304)  3 0x400cb553 (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2438)  4 0x40360361 (NTDLL.DLL.memcpy+0xc7b41 in libpthread.so.0) (ebp=407f24b8)
  5 0x402f5bde (NTDLL.DLL.memcpy+0x5d3be in libc.so.6) (ebp=00000000)

0x4008cfa8 (NTDLL.DLL.__wine_call_from_32_regs+0x1b564 in libntdll.so): movl   0xc(%edi),%eax
Modules:
Address                 Module  Name
0x00400000-00433000     (PE)    D:\Desktop\War3ROC_120a_English.exe
0x40057000-40059000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) D:\Desktop\War3ROC_120a_English.exe
        00000002    0 <==
WineDbg terminated on pid 1
tommy@bzq-82-81-196-144:~/Desktop$

```

does anyone know how to solve this?
P.S in my cedega config its told to emulate XP so cdprotect works
tried in 98 tho it still doesn't work

Thanks,
tommy.

---

### Post by Hairy_Palms on 2005-10-21
all works fine for me, im using cedega 4.3 though and i dont use point2play

---

### Post by Hack4ev3r on 2005-10-21
[QUOTE=Hairy_Palms]all works fine for me, im using cedega 4.3 though and i dont use point2play[/QUOTE]
I don't use point2play too..

i would downgrade but in this version the b.net bug got fixed in diablo2 :'(
any way i can solve this :'((((((((((((((((((((((((((((((((((

---

