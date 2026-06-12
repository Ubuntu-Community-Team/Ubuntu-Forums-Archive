---
title: "HELP: I cant install games with Cedega"
date: 2005-06-02
forum: Gaming &amp; Leisure
---

### Post by i-tech on 2005-06-02
Hi all;
When i try to install a game it gives me the error below? I couldnt fgure it out please help
is it about LANG?? if so how will i set it to correct one?? 
>  cedega /media/cdrom0/install.exe
wine: Unhandled exception, starting debugger...
Warning: Language 'en_TR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40131000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020b000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022c000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40359000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40369000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0x40803000)
No debug information in 32bit DLL 'F:\install.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40056000)
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0041d5ff).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:0041d5ff ESP:407f28f0 EBP:407f2994 EFLAGS:00210246(  R- 00  I  Z- -P1 )
 EAX:00000000 EBX:40103368 ECX:00000600 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x407f28f0 (NTDLL.DLL.memcpy+0x54efc0):  400ca3cc 00000000 401186e0 407f2918
0x407f2900 (NTDLL.DLL.memcpy+0x54efd0):  4011b880 90000000 00406864 0041d5ff
0x407f2910 (NTDLL.DLL.memcpy+0x54efe0):  00000000 005c3a46 00000000 00000000
0x407f2920 (NTDLL.DLL.memcpy+0x54eff0):  00000000 00000001 00406864 90000000
0x407f2930 (NTDLL.DLL.memcpy+0x54f000):  00000001 900090ec bffff390 00000001
0x407f2940 (NTDLL.DLL.memcpy+0x54f010):  bffff374 bffff3d8 0000000e 9004a8ec
0x407f2950 (NTDLL.DLL.memcpy+0x54f020):

Backtrace:
=>0 0x0041d5ff (install.exe.EntryPoint in F:\install.exe) (ebp=407f2994)
  1 0x400ca4df (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2ac8)  2 0x4035dae0 (NTDLL.DLL.memcpy+0xba1b0 in libpthread.so.0) (ebp=407f2b3c)
  3 0x402fec9a (NTDLL.DLL.memcpy+0x5b36a in libc.so.6) (ebp=00000000)

0x0041d5ff (install.exe.EntryPoint in F:\install.exe): addb     %al,0x0(%eax)
Modules:
Address                 Module  Name
0x00400000-00457000     (PE)    F:\install.exe
0x40056000-40058000     (PE)    NTDLL.DLL
Threads:
process  tid      prio
00000001 (D) F:\install.exe
        00000002    0 <==
WineDbg terminated on pid 1


---

### Post by Technoviking on 2005-06-02
No problem here, other than I play way to much City of Heroes:). Did the Cedega or Point2Play deb? I suggest using the point2play deb and installing Cedega from within that. Seems to work the best for me.

Mike

---

### Post by i-tech on 2005-06-02
it's a debian pakage dont know much about pointtoplay :( where can i find it?

---

