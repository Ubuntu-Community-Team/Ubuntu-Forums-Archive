---
title: "Cedega 4.2 cannot launch iKernel.exe"
date: 2005-02-08
forum: Gaming &amp; Leisure
---

### Post by Flea on 2005-02-08
Trying to run Setup.exe on cdrom results in

The InstallShield Engine (iKernel.exe) could not be launched. (0x800401fe)

I found something online about prelink and Exec-shield causing these errors but I don't have prelink installed, does Ubuntu have this Exec-shield? I also checked for noexec in fstab in case that was to blame, nothing there.

Running Warty, free ubuntu CD off Linux Format magazine and Cedega 4.2.1-1. 

Has anyone else experienced these problems and know of a solution? Any help much appreciated.

---------------------
Dave

---

### Post by Flea on 2005-02-09
I know there isn't a lot of info there, sorry, there just isn't much information to give, I'm stumped on this one. I'll try my best.

Its Medal of Honor Allied Assault that I'm trying to install. I know there is a native port but it just doesn't work well enough for me. I just recently moved from Slackware 10.0 and Cedega worked fine there.
There is a file called ikernel.ex_ on the CD, I'm guessing that this is a compressed file used by the installshield wizard. I tried several other games, most just freeze with wine: Unhandled exception, starting debugger... and go no further. The only exception was the autorun.exe on Medal of Honor Pacific Assault which came back with...

> wine: Unhandled exception, starting debugger...
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c191
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40017000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x40118000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x4012d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f5000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x40200000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x40223000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40356000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40366000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0x406f3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0x40774000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0x4089c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0x40913000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0x4093a000)
No debug information in 32bit DLL 'F:\autorun\Autorun.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40054000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x40726000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x40925000)
No debug information in 32bit DLL 'GDI32.DLL' (0x408bb000)
No debug information in 32bit DLL 'USER32.DLL' (0x407ab000)
Unhandled exception: page fault on read access to 0x000164dc in 32-bit code (0x000164dc).
In 32-bit mode.
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:000164dc ESP:406e2118 EBP:406e2124 EFLAGS:00010212( R- 00 I -A- 1 )
EAX:4099e4bc EBX:4099e998 ECX:00000001 EDX:0804d3d8
ESI:080540b0 EDI:080540b0
Stack dump:
0x406e2118 (NTDLL.DLL.memcpy+0x445b98): 4094d400 4099e4bc 4099e998 406e2144
0x406e2128 (NTDLL.DLL.memcpy+0x445ba8): 40949f6b 400157b8 40358414 40358414
0x406e2138 (NTDLL.DLL.memcpy+0x445bb8): 080540b0 00000002 40947fd4 406e2174
0x406e2148 (NTDLL.DLL.memcpy+0x445bc8): 4000bc1c 00000007 bffff664 bffff684
0x406e2158 (NTDLL.DLL.memcpy+0x445bd8): 00000000 4022698c 00000000 00000000
0x406e2168 (NTDLL.DLL.memcpy+0x445be8): 400157b8 00000000 080540b0 406e21b4
0x406e2178 (NTDLL.DLL.memcpy+0x445bf8):

Backtrace:
=>0 0x000164dc (ebp=406e2124)
1 0x40949f6b (ADVAPI32.DLL.IsTextUnicode+0x11da3 in libcomdlg32.so) (ebp=406e2144)
2 0x4000bc1c (NTDLL.DLL.wine_dbg_printf+0x37fc3480 in ld-linux.so.2) (ebp=406e2174)
3 0x4000bd02 (NTDLL.DLL.wine_dbg_printf+0x37fc3566 in ld-linux.so.2) (ebp=406e21b4)
4 0x40329632 (NTDLL.DLL.memcpy+0x8d0b2 in libc.so.6) (ebp=406e2224)
5 0x4000ba80 (NTDLL.DLL.wine_dbg_printf+0x37fc32e4 in ld-linux.so.2) (ebp=406e2324)
6 0x40329252 (NTDLL.DLL.memcpy+0x8ccd2 in libc.so.6) (ebp=406e23b4)
7 0x40366fc4 (NTDLL.DLL.memcpy+0xcaa44 in libdl.so.2) (ebp=406e24c4)
8 0x403673e8 (NTDLL.DLL.memcpy+0xcae68 in libdl.so.2) (ebp=406e24ec)
9 0x00000002 (ebp=08053059)
10 0x6c646d6f (ADVAPI32.DLL.IsTextUnicode+0x2bd0eba7) (ebp=6362696c)
*** Invalid address 0x6362696c (ADVAPI32.DLL.IsTextUnicode+0x22cee7a4)

0x000164dc: *** Invalid address 0x000164dc
-- no code --
Modules:
Address Module Name
0x00400000-0050a000 (PE) F:\autorun\Autorun.exe
0x40054000-40056000 (PE) NTDLL.DLL
0x40726000-40728000 (PE) KERNEL32.DLL
0x407ab000-407ad000 (PE) USER32.DLL
0x408bb000-408bd000 (PE) GDI32.DLL
0x40925000-40927000 (PE) ADVAPI32.DLL
Threads:
process tid prio
00000001 (D) F:\autorun\Autorun.exe
00000002 0 <==
WineDbg terminated on pid 1

This is just gibberish to me though, anybody understand this?

I'm running kernel 2.6.8.1-4-686.

---

### Post by Flea on 2005-02-09
Doesn't matter now, have moved back to Slackware, Don't know why I keep trying other distro's really, Slackware does everything I want. I was hoping to enjoy the easy updates/patches etc. of apt but no good really if I can't run Cedega.

Lots of people go on and on about how Slackware is hard to configure, use etc. but in all honesty I find Slackware "just works" I never have these sort of problems with it?! Fedora, Ubuntu, Mandrake they all... well... suck in comparison  :wink: 

One day I'm hoping to try Debian out, maybe that will knock Slackware off my top spot... till then though...  :-| 

Don't wish to start a flame, just my personal opinion. Overall Ubuntu has a lot of potential, I just can't put up with problems like this when there are other distro's that will do what I wan't without complaining.  :-| 

------------------
Dave

---

