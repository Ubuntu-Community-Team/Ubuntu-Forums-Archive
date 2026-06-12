---
title: "cedega fails to install games"
date: 2005-04-09
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2005-04-09
Hi,

I have just did a fresh install of Ubuntu 5.04. I also installed cedega 4.3-1. When I want to install starcraft, I get these messages:

eric@ubuntu:/media/cdrom$ cedega install.exe
wine: Unhandled exception, starting debugger...
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c195
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40131000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x40206000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x40227000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40354000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40364000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libversion.so' (0x40833000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/liblz32.so' (0x4083d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0x40844000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0x408c5000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0x4091b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0x40a43000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0x40aba000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0x40ae1000)
No debug information in 32bit DLL 'F:\install.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40056000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x40877000)
No debug information in 32bit DLL 'LZ32.DLL' (0x40840000)
No debug information in 32bit DLL 'VERSION.DLL' (0x40836000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x40acc000)
No debug information in 32bit DLL 'GDI32.DLL' (0x40a62000)
No debug information in 32bit DLL 'USER32.DLL' (0x40952000)
No debug information in 32bit DLL 'WINMM.DLL' (0x408d3000)
Unhandled exception: page fault on read access to 0x00016b1c in 32-bit code (0x00016b1c).
In 32-bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00016b1c ESP:40822114 EBP:40822120 EFLAGS:00010216(  R- 00  I   -A-P1 )
 EAX:40b44e7c EBX:40b45360 ECX:00000001 EDX:780033f8
 ESI:7800a8d0 EDI:7800a8d0
Stack dump:
0x40822114 (NTDLL.DLL.memcpy+0x5837e4):  40af4a3c 40b44e7c 40b45360 40822140
0x40822124 (NTDLL.DLL.memcpy+0x5837f4):  40af0f6b 40015778 4035643c 4035643c
0x40822134 (NTDLL.DLL.memcpy+0x583804):  7800a8d0 00000002 40aeefd4 40822170
0x40822144 (NTDLL.DLL.memcpy+0x583814):  4000bc1c 00000007 bffff5b4 bffff5d4
0x40822154 (NTDLL.DLL.memcpy+0x583824):  00000000 4022a98c 00000000 00000000
0x40822164 (NTDLL.DLL.memcpy+0x583834):  40015778 00000000 7800a8d0 408221b0
0x40822174 (NTDLL.DLL.memcpy+0x583844):

Backtrace:
=>0 0x00016b1c (ebp=40822120)
  1 0x40af0f6b (ADVAPI32.DLL.IsTextUnicode+0x11ac3 in libcomdlg32.so) (ebp=40822140)
  2 0x4000bc1c (NTDLL.DLL.wine_dbg_printf+0x100b218 in ld-linux.so.2) (ebp=40822170)
  3 0x4000bd02 (NTDLL.DLL.wine_dbg_printf+0x100b2fe in ld-linux.so.2) (ebp=408221b0)
  4 0x40327959 (NTDLL.DLL.memcpy+0x89029 in libc.so.6) (ebp=40822220)
  5 0x4000ba80 (NTDLL.DLL.wine_dbg_printf+0x100b07c in ld-linux.so.2) (ebp=40822320)
  6 0x4032759a (NTDLL.DLL.memcpy+0x88c6a in libc.so.6) (ebp=40822390)
  7 0x40364ff0 (NTDLL.DLL.memcpy+0xc66c0 in libdl.so.2) (ebp=408223b0)
  8 0x4000ba80 (NTDLL.DLL.wine_dbg_printf+0x100b07c in ld-linux.so.2) (ebp=408224b0)
  9 0x403653f9 (NTDLL.DLL.memcpy+0xc6ac9 in libdl.so.2) (ebp=408224e0)
  10 0x40364fa4 (NTDLL.DLL.memcpy+0xc6674 in libdl.so.2) (ebp=40822500)
  11 0x401f9b82 (NTDLL.DLL.NlsMbOemCodePageTag+0xf994d in libwine_port.so) (ebp=4082251c)
  12 0x4011d773 (NTDLL.DLL.NlsMbOemCodePageTag+0x1d53e in libwine.so) (ebp=4082255c)
  13 0x400c5898 (USER32.DLL.GetAppCompatFlags+0x34d8c in libntdll.so) (ebp=4082267c)
  14 0x400c5b8f (USER32.DLL.GetAppCompatFlags+0x35083 in libntdll.so) (ebp=408227a4)
  15 0x4008af43 (KERNEL32.DLL.__wine_call_from_16_regs+0x4997 in libntdll.so) (ebp=408227f0)
  16 0x4008bfd7 (KERNEL32.DLL.__wine_call_from_16_regs+0x5a2b in libntdll.so) (ebp=40822848)
  17 0x4008cb3a (KERNEL32.DLL.__wine_call_from_16_regs+0x658e in libntdll.so) (ebp=408228dc)
  18 0x400ca2de (NTDLL.DLL.wine_server_call+0x1d86 in libntdll.so) (ebp=40822994)
  19 0x400ca4df (NTDLL.DLL.wine_server_call+0x1f87 in libntdll.so) (ebp=40822ac8)
  20 0x40358ae0 (NTDLL.DLL.memcpy+0xba1b0 in libpthread.so.0) (ebp=40822b3c)
  21 0x402f9c9a (NTDLL.DLL.memcpy+0x5b36a in libc.so.6) (ebp=00000000)

0x00016b1c: addb        %al,0x0(%eax)
Modules:
Address                 Module  Name
0x00400000-0044d000     (PE)    F:\install.exe
0x40056000-40058000     (PE)    NTDLL.DLL
0x40836000-40838000     (PE)    VERSION.DLL
0x40840000-40842000     (PE)    LZ32.DLL
0x40877000-40879000     (PE)    KERNEL32.DLL
0x408d3000-408d5000     (PE)    WINMM.DLL
0x40952000-40954000     (PE)    USER32.DLL
0x40a62000-40a64000     (PE)    GDI32.DLL
0x40acc000-40ace000     (PE)    ADVAPI32.DLL
Threads:
process  tid      prio
00000001 (D) F:\install.exe
        00000002    0 <==
WineDbg terminated on pid 1
eric@ubuntu:/media/cdrom$



Any idea what is wrong?
Thanks

---

### Post by Muchacho_Gasolino on 2005-04-09
If you are running 64 bit,
I had to do [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot) to get any games at all to work with cedega

---

### Post by Neo40 on 2005-04-09
[QUOTE=Muchacho_Gasolino]If you are running 64 bit,
I had to do [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot) to get any games at all to work with cedega[/QUOTE]

Hi,

thanks for your reply. I have downloaded "ubuntu-5.04-install-i386.iso". Not sure, but I think I'm not running 64 bit...??

---

### Post by Muchacho_Gasolino on 2005-04-09
the i386 part of that means you are not
i dont know very much about this kind of problem
one thing i would reccomend though is posting or looking around on the forums at [www.transgaming.org](www.transgaming.org)
i have seen many people report problems with errors that look like yours, and most of them have gotten them solved
it could be the case that starcraft isn't officially supported by Cedega, though it should work even if it isn't because all the other blizz games do

---

### Post by Neo40 on 2005-04-09
[QUOTE=Muchacho_Gasolino]the i386 part of that means you are not
i dont know very much about this kind of problem
one thing i would reccomend though is posting or looking around on the forums at [www.transgaming.org](www.transgaming.org)
i have seen many people report problems with errors that look like yours, and most of them have gotten them solved
it could be the case that starcraft isn't officially supported by Cedega, though it should work even if it isn't because all the other blizz games do[/QUOTE]

Hi!,

It should work because with an another distro (archlinux)  I have no problem!

---

### Post by Muchacho_Gasolino on 2005-04-10
well then starcraft isn't your problem, it is getting ubuntu configured right to run cedega

---

### Post by Neo40 on 2005-04-10
Hi again,

I found if I use a old version of cedega ( winex 3.1 ) it works fine. However, I need  the latest one to play on bnet.... :(

---

