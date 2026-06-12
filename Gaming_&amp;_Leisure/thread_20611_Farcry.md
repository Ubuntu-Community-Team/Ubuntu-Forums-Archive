---
title: "Farcry"
date: 2005-03-17
forum: Gaming &amp; Leisure
---

### Post by Drakx on 2005-03-17
After finding a installer for farcry from [here](http://liflg.org/)  i start it by using the supplied shell script and i run it in  a terminal i find it wont start and im getting this problem any one else got problem
im using Cedega 4.3

```
wine: Unhandled exception, starting debugger...
WineDbg starting on pid 3
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c191
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40017000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40130000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f8000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x4020c000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x4022f000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40362000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40372000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0x40703000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0x40784000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0x408ac000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0x40923000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0x4094a000)
No debug information in 32bit DLL 'D:\Games\farcry\Bin32\FarCryConfigurator.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40055000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x40736000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x40935000)
No debug information in 32bit DLL 'GDI32.DLL' (0x408cb000)
No debug information in 32bit DLL 'USER32.DLL' (0x407bb000)
Unhandled exception: page fault on read access to 0x00016b1c in 32-bit code (0x00016b1c).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00016b1c ESP:406f2114 EBP:406f2120 EFLAGS:00210216(  R- 00  I   -A-P1 )
 EAX:409ade7c EBX:409ae360 ECX:00000001 EDX:780033f8
 ESI:78009eb0 EDI:78009eb0
Stack dump:
0x406f2114 (NTDLL.DLL.memcpy+0x449b94):  4095da3c 409ade7c 409ae360 406f2140
0x406f2124 (NTDLL.DLL.memcpy+0x449ba4):  40959f6b 400157b8 40364414 40364414
0x406f2134 (NTDLL.DLL.memcpy+0x449bb4):  78009eb0 00000002 40957fd4 406f2170
0x406f2144 (NTDLL.DLL.memcpy+0x449bc4):  4000bc1c 00000004 bffff718 bffff72c
0x406f2154 (NTDLL.DLL.memcpy+0x449bd4):  00000000 4023298c 00000000 00000000
0x406f2164 (NTDLL.DLL.memcpy+0x449be4):  400157b8 00000000 78009eb0 406f21b0
0x406f2174 (NTDLL.DLL.memcpy+0x449bf4):

Backtrace:
=>0 0x00016b1c (ebp=406f2120)
  1 0x40959f6b (ADVAPI32.DLL.IsTextUnicode+0x11ac3 in libcomdlg32.so) (ebp=406f2140)
  2 0x4000bc1c (NTDLL.DLL.wine_dbg_printf+0x100b218 in ld-linux.so.2) (ebp=406f2170)
  3 0x4000bd02 (NTDLL.DLL.wine_dbg_printf+0x100b2fe in ld-linux.so.2) (ebp=406f21b0)
  4 0x40335632 (NTDLL.DLL.memcpy+0x8d0b2 in libc.so.6) (ebp=406f2220)
  5 0x4000ba80 (NTDLL.DLL.wine_dbg_printf+0x100b07c in ld-linux.so.2) (ebp=406f2320)
  6 0x40335252 (NTDLL.DLL.memcpy+0x8ccd2 in libc.so.6) (ebp=406f23b0)
  7 0x40372fc4 (NTDLL.DLL.memcpy+0xcaa44 in libdl.so.2) (ebp=406f24c0)
  8 0x403733e8 (NTDLL.DLL.memcpy+0xcae68 in libdl.so.2) (ebp=406f24e8)
  9 0x00000002 (ebp=78009031)
  10 0x6c646d6f (ADVAPI32.DLL.IsTextUnicode+0x2bcfe8c7) (ebp=6362696c)
*** Invalid address 0x6362696c (ADVAPI32.DLL.IsTextUnicode+0x22cde4c4)

0x00016b1c: addb        %al,0x0(%eax)
Modules:
Address                 Module  Name
0x00400000-00469000     (PE)    D:\Games\farcry\Bin32\FarCryConfigurator.exe
0x40055000-40057000     (PE)    NTDLL.DLL
0x40736000-40738000     (PE)    KERNEL32.DLL
0x407bb000-407bd000     (PE)    USER32.DLL
0x408cb000-408cd000     (PE)    GDI32.DLL
0x40935000-40937000     (PE)    ADVAPI32.DLL
Threads:
process  tid      prio
00000003 (D) D:\Games\farcry\Bin32\FarCryConfigurator.exe
        00000004    0 <==
00000001
        00000002    0
WineDbg terminated on pid 3
```

---

### Post by Drakx on 2005-03-18
Ok i fixed the problem but now performance is very slow and jerkey can any one tell/know why?


Thanks

---

### Post by saik0 on 2005-03-24
Can you tell me what you did to resolve that probelm, I am havving a very similar issue

---

### Post by Drakx on 2005-03-26
Yea it was a dependacy that cedega has if i remember it was libpng i think uninstall wine/cedega and then install it again doing sudo dpkg -i package name.deb

and it should tell you the dependance it requires

---

