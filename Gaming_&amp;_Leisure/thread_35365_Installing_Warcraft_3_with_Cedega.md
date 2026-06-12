---
title: "Installing Warcraft 3 with Cedega"
date: 2005-05-18
forum: Gaming &amp; Leisure
---

### Post by i-tech on 2005-05-18
Hi all;
Firstly,I dont know anything about cedega so if you can help me with the problem please explain in detail. I tried to install war 3 with cedega i simply did > cedega /media/cdrom0/install.exe but i gave me the error below. i guess its about language but i tried to change LANG to us_ENG it didnt work.
 ```
wine: Unhandled exception, starting debugger...
Warning: Language 'en_TR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=us_ENG
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40131000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020a000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022b000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40358000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40368000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0x40803000)
No debug information in 32bit DLL 'F:\install.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40056000)
Unhandled exception: illegal instruction in 32-bit code (0x0041d601).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:0041d601 ESP:407f28f0 EBP:407f2994 EFLAGS:00210206(  R- 00  I   - -P1 )
 EAX:00000000 EBX:40106668 ECX:00000600 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x407f28f0 (NTDLL.DLL.memcpy+0x54ffc0):  400ca3cc 00000000 401186e0 407f2918
0x407f2900 (NTDLL.DLL.memcpy+0x54ffd0):  4011b880 90000000 00406870 0041d5ff
0x407f2910 (NTDLL.DLL.memcpy+0x54ffe0):  00000000 005c3a46 00000000 00000000
0x407f2920 (NTDLL.DLL.memcpy+0x54fff0):  00000000 00000001 00406870 90000000
0x407f2930 (NTDLL.DLL.memcpy+0x550000):  00000001 900090ec bffff420 00000001
0x407f2940 (NTDLL.DLL.memcpy+0x550010):  bffff404 bffff468 0000000e 9000dcdc
0x407f2950 (NTDLL.DLL.memcpy+0x550020):

Backtrace:
=>0 0x0041d601 (install.exe.EntryPoint+0x2 in F:\install.exe) (ebp=407f2994)
1 0x400ca4df (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=407f2ac:cool: 2 0x4035cae0 (NTDLL.DLL.memcpy+0xba1b0 in libpthread.so.0) (ebp=407f2b3c)
  3 0x402fdc9a (NTDLL.DLL.memcpy+0x5b36a in libc.so.6) (ebp=00000000)

0x0041d601 (install.exe.EntryPoint+0x2 in F:\install.exe):
Modules:
Address				 Module  Name
0x00400000-00457000	 (PE)	F:\install.exe
0x40056000-40058000	 (PE)	NTDLL.DLL
Threads:
process  tid	  prio
00000001 (D) F:\install.exe
		00000002	0 <==
WineDbg terminated on pid 1

```

---

### Post by gil-galad on 2005-05-19
Which version of cedega are you running?

---

### Post by i-tech on 2005-05-20
I'm using cedega_4.3.1-1_i386

---

### Post by sethmahoney on 2005-05-20
[QUOTE=i-tech]I'm using cedega_4.3.1-1_i386[/QUOTE]

Try setting LANG to en_US

---

### Post by i-tech on 2005-05-21
I just did LANG = en_US at the konsole but it didnt worked out.

---

