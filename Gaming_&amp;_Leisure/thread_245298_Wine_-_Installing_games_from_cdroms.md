---
title: "Wine - Installing games from cdroms"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by Sopranosmainman on 2006-08-27
Hey guys i just finally got wine, and i tried a few windows apps just ot see if it works. Firefox worked fine and i was happy. THen i tried good old skifree... no problem..

Now i wanted to try some older 3d games just to see how they ran. I tried Empire Earth, and my brother's copy of Starship Troopers. Both of which crashed after just barely beginning the setup process. THis is the error i got back from starship troopers, from running the setup.exe.... can anyone tell me how to get it working. THANKS!

fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: Unhandled page fault on read access to 0x00000000 at address 0x404b07 (thr
ead 0028), starting debugger...
WineDbg starting on pid 0x27
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0
0404b07).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00404b07 ESP:0034f050 EBP:0034f1cc EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:0034fe58 ECX:0034f8f4 EDX:00169e28
 ESI:0034f8f4 EDI:00000000
Stack dump:
0x0034f050:  00000000 00000000 000002d2 0034f8f8
0x0034f060:  0034f8f4 00000000 7efb73bc 00110020
0x0034f070:  00110000 00000002 7eff5280 7eeccb20
0x0034f080:  00000000 0034f0a4 7ee92dad 00000000
0x0034f090:  00110000 00000002 7e9ee484 0016d68c
0x0034f0a0:  00000000 0034f0e4 7e9b3cf5 00110000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00404b07 in setup (+0x4b07) (0x00404b07)
  2 0x00402925 in setup (+0x2925) (0x00402925)
  3 0x0040241a in setup (+0x241a) (0x0040241a)
  4 0x004020da in setup (+0x20da) (0x004020da)
  5 0x00401c3c in setup (+0x1c3c) (0x00401c3c)
  6 0x7ee92edf in kernel32 (+0x52edf) (0x7ee92edf)
  7 0xb7e66287 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7e66287)
0x00404b07: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (59 modules)
PE      400000-410000   Export          setup
ELF     41b65000-41b80000       Deferred        ld-linux.so.2
ELF     41ba7000-41baf000       Deferred        libxrender.so.1
ELF     41bb1000-41bcf000       Deferred        libexpat.so.1
ELF     41bd1000-41bda000       Deferred        libxcursor.so.1
ELF     41bdc000-41c0a000       Deferred        libfontconfig.so.1
ELF     41c0c000-41c0f000       Deferred        libxrandr.so.2
ELF     41c16000-41c1b000       Deferred        libxfixes.so.3
ELF     41cba000-41ccd000       Deferred        libresolv.so.2
ELF     42286000-4229c000       Deferred        libnsl.so.1
ELF     423e7000-423ec000       Deferred        libxxf86vm.so.1
ELF     423f9000-4252d000       Deferred        libc.so.6
ELF     4252f000-42533000       Deferred        libdl.so.2
ELF     42535000-4255b000       Deferred        libm.so.6
ELF     4255d000-42571000       Deferred        libz.so.1
ELF     42573000-42586000       Deferred        libpthread.so.0
ELF     42588000-4258d000       Deferred        libxdmcp.so.6
ELF     4258f000-42592000       Deferred        libxau.so.6
ELF     42594000-4265d000       Deferred        libx11.so.6
ELF     4265f000-4266c000       Deferred        libxext.so.6
ELF     4266e000-42677000       Deferred        libsm.so.6
ELF     42679000-42691000       Deferred        libice.so.6
ELF     42693000-426fa000       Deferred        libfreetype.so.6
ELF     426fc000-42707000       Deferred        libgcc_s.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e518000-7e54a000       Deferred        uxtheme<elf>
  \-PE  7e520000-7e54a000       \               uxtheme
ELF     7e55a000-7e55c000       Deferred        xlcutf8load.so.2
ELF     7e567000-7e607000       Deferred        libgl.so.1
ELF     7e6fa000-7e77c000       Deferred        winex11<elf>
  \-PE  7e710000-7e77c000       \               winex11
ELF     7e843000-7e8d5000       Deferred        oleaut32<elf>
  \-PE  7e850000-7e8d5000       \               oleaut32
ELF     7e8fa000-7e919000       Deferred        iphlpapi<elf>
  \-PE  7e900000-7e919000       \               iphlpapi
ELF     7e919000-7e968000       Deferred        rpcrt4<elf>
  \-PE  7e920000-7e968000       \               rpcrt4
ELF     7e968000-7e9f8000       Deferred        ole32<elf>
  \-PE  7e980000-7e9f8000       \               ole32
ELF     7e9f8000-7ea0c000       Deferred        lz32<elf>
  \-PE  7ea00000-7ea0c000       \               lz32
ELF     7ea0c000-7ea25000       Deferred        version<elf>
  \-PE  7ea10000-7ea25000       \               version
ELF     7ea25000-7ea69000       Deferred        advapi32<elf>
  \-PE  7ea30000-7ea69000       \               advapi32
ELF     7eb4d000-7ebff000       Deferred        gdi32<elf>
  \-PE  7eb60000-7ebff000       \               gdi32
ELF     7ebff000-7ed31000       Deferred        user32<elf>
  \-PE  7ec20000-7ed31000       \               user32
ELF     7ed31000-7edf3000       Deferred        comctl32<elf>
  \-PE  7ed40000-7edf3000       \               comctl32
ELF     7ee26000-7ef28000       Export          kernel32<elf>
  \-PE  7ee40000-7ef28000       \               kernel32
ELF     7ef28000-7ef33000       Deferred        libnss_files.so.2
ELF     7ef33000-7ef3d000       Deferred        libnss_nis.so.2
ELF     7ef53000-7ef5c000       Deferred        libnss_compat.so.2
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7e5f000-b7f6f000       Export          libwine.so.1
Threads:
process  tid      prio (all id:s are in hex)
00000027 (D) D:\Setup.exe
        0000002b    0
        00000028    0 <==
0000000e
        0000002f    0
        0000002e    0
        0000002d    0
        0000002c    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
0000000a
        0000000b    0

---

### Post by croak77 on 2006-08-27
Not every game/program runs in wine. Search here and see what works.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

