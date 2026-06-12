---
title: "Mechwarrior 3 through wine"
date: 2013-07-14
forum: Gaming &amp; Leisure
---

### Post by colmeweb on 2013-07-14
So I am running Wine 1.4.1 on Ubuntu 13.04 and a few days ago I decided that I wan't to try out Mechwarrior 3. 
After a little fidgeting I got it to install perfectly but every time I try to play it I get an error message.
I put the details below. 
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00424252).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00424252 ESP:0033d9dc EBP:0033da28 EFLAGS:00010247(  R- --  I  Z- -P-C)
 EAX:81df4000 EBX:00000018 ECX:0033da50 EDX:0033db1f
 ESI:00000000 EDI:00000001
Stack dump:
0x0033d9dc:  00000001 00400000 0033da28 0033d9fc
0x0033d9ec:  00000018 0033db1f 0033da50 00001010
0x0033d9fc:  00000001 00400000 00000018 00001010
0x0033da0c:  7bc80023 00400000 40000fff 003381df
0x0033da1c:  00000000 07f3e6d0 00000003 0033daec
0x0033da2c:  0042444f 00001010 0033da50 00000001
Backtrace:
=>0 0x00424252 in mech3 (+0x24252) (0x0033da28)
0x00424252: movl    0x0(%esi),%edi
Modules:
Module    Address            Debug info    Name (55 modules)
PE      400000-  441000    Export          mech3
ELF    7b800000-7ba44000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba44000    \               kernel32
ELF    7bc00000-7bce4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e42c000-7e433000    Deferred        libxfixes.so.3
ELF    7e433000-7e43e000    Deferred        libxcursor.so.1
ELF    7e4bc000-7e4e4000    Deferred        libexpat.so.1
ELF    7e4e4000-7e51d000    Deferred        libfontconfig.so.1
ELF    7e51d000-7e52d000    Deferred        libxi.so.6
ELF    7e52d000-7e531000    Deferred        libxcomposite.so.1
ELF    7e531000-7e53c000    Deferred        libxrandr.so.2
ELF    7e53c000-7e546000    Deferred        libxrender.so.1
ELF    7e546000-7e54c000    Deferred        libxxf86vm.so.1
ELF    7e54c000-7e550000    Deferred        libxinerama.so.1
ELF    7e550000-7e574000    Deferred        imm32<elf>
  \-PE    7e560000-7e574000    \               imm32
ELF    7e574000-7e57b000    Deferred        libxdmcp.so.6
ELF    7e57b000-7e59d000    Deferred        libxcb.so.1
ELF    7e59d000-7e5a3000    Deferred        libuuid.so.1
ELF    7e5a3000-7e5bd000    Deferred        libice.so.6
ELF    7e5bd000-7e6f4000    Deferred        libx11.so.6
ELF    7e6f4000-7e706000    Deferred        libxext.so.6
ELF    7e706000-7e70f000    Deferred        libsm.so.6
ELF    7e70f000-7e7c0000    Deferred        winex11<elf>
  \-PE    7e720000-7e7c0000    \               winex11
ELF    7e7c0000-7e7d9000    Deferred        libz.so.1
ELF    7e7d9000-7e874000    Deferred        libfreetype.so.6
ELF    7e893000-7e8a8000    Deferred        comm.drv16.so
PE    7e8a0000-7e8a8000    Deferred        comm.drv16
ELF    7e8a8000-7e8bd000    Deferred        system.drv16.so
PE    7e8b0000-7e8bd000    Deferred        system.drv16
ELF    7e8bd000-7e983000    Deferred        krnl386.exe16.so
PE    7e8d0000-7e983000    Deferred        krnl386.exe16
ELF    7e983000-7e9f5000    Deferred        advapi32<elf>
  \-PE    7e990000-7e9f5000    \               advapi32
ELF    7e9f5000-7ead6000    Deferred        gdi32<elf>
  \-PE    7ea00000-7ead6000    \               gdi32
ELF    7ead6000-7ec46000    Deferred        user32<elf>
  \-PE    7eaf0000-7ec46000    \               user32
ELF    7ec46000-7ec53000    Deferred        libnss_files.so.2
ELF    7ec53000-7ec6c000    Deferred        libnsl.so.1
ELF    7ef9e000-7efe1000    Deferred        libm.so.6
ELF    7efe1000-7efe5000    Deferred        libxau.so.6
ELF    7efe5000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7473000-f747f000    Deferred        libnss_nis.so.2
ELF    f7480000-f7485000    Deferred        libdl.so.2
ELF    f7485000-f7638000    Deferred        libc.so.6
ELF    f7639000-f7654000    Deferred        libpthread.so.0
ELF    f7657000-f7660000    Deferred        libnss_compat.so.2
ELF    f7673000-f77b7000    Dwarf           libwine.so.1
ELF    f77b9000-f77db000    Deferred        ld-linux.so.2
ELF    f77db000-f77dc000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
    0000001f    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001e    0
    0000001c    0
00000022 explorer.exe
    00000023    0
00000024 (D) C:\MechWarrior3\mech3.exe
    00000025    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.8.0-26-generic



```

I tried looking at some other posts but most of them are from 2007 so I'm not sure if there is any real help there. If anybody has experience with this or a similar problem the help would be great. 

Thanks.

---

### Post by oldrocker99 on 2013-07-14
Here's what winehq.org said about it:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3124](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3124)

This was with wine 1.2, but if it was "garbage" then, it's likely still one Windows program that wine just won't run.

It's why I dual-boot, myself.

---

### Post by colmeweb on 2013-07-19
So I figured it out. In order to get the game working I had to install a patch that takes the game to version 1.2. But in order to install the patch I had to burn the iso onto a disc. But now the game is working great now. I'm not sure how to put this onto the wine forums if anybody wants to feel free.

---

