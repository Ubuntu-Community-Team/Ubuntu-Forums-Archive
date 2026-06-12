---
title: "Wine rollercoaster tycoon 2 help"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by CanonD on 2006-08-28
Hello, if anyone can help me get this game to install it would be great. when  cd ing and entering wine setup.exe, the installer exits. this is what shows in the terminal

```
fixme:ole:ITypeInfo_fnRelease destroy child objects
err:ole:marshal_object Failed to create an IRpcStubBuffer from IPSFactory for {91814ec1-b5f0-11d2-80b9-00104b1f6cea}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002err:ole:CoMarshalInterface Failed to marshal the interface {91814ec1-b5f0-11d2-80b9-00104b1f6cea}, 80004002
err:ole:_marshal_interface Marshalling interface {91814ec1-b5f0-11d2-80b9-00104b1f6cea} failed with 80004002
err:ole:TMStubImpl_Invoke Failed to stuballoc param, hres 80004002
wine: Unhandled page fault on read access to 0x00000000 at address 0x405564 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00405564).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:00405564 ESP:0033eff0 EBP:0033f16c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:0033fe58 ECX:0033f894 EDX:00186ad0
 ESI:0033f894 EDI:00000000
Stack dump:
0x0033eff0:  00000000 00000000 000002b0 0033f898
0x0033f000:  0033f894 000003ff 7efb73bc 00110020
0x0033f010:  00110000 00000002 7eff5280 7eeccb20
0x0033f020:  00000000 0033f044 7ee92dad 00000000
0x0033f030:  00110000 00000002 7e9f3484 0018b53c
0x0033f040:  00000000 0033f084 7e9b8cf5 00110000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00405564 in setup (+0x5564) (0x00405564)
  2 0x00403259 in setup (+0x3259) (0x00403259)
  3 0x00402d4e in setup (+0x2d4e) (0x00402d4e)
  4 0x00402a07 in setup (+0x2a07) (0x00402a07)
  5 0x0040254e in setup (+0x254e) (0x0040254e)
  6 0x7ee92edf in kernel32 (+0x52edf) (0x7ee92edf)
  7 0xb7e47287 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7e47287)
0x00405564: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (61 modules)
PE      400000-411000   Export          setup
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dd50000-7dd82000       Deferred        uxtheme<elf>
  \-PE  7dd60000-7dd82000       \               uxtheme
ELF     7dd84000-7dd88000       Deferred        libxfixes.so.3
ELF     7dd88000-7dd91000       Deferred        libxcursor.so.1
ELF     7dd91000-7ddad000       Deferred        imm32<elf>
  \-PE  7dda0000-7ddad000       \               imm32
ELF     7ddad000-7ddb0000       Deferred        libxrandr.so.2
ELF     7ddb0000-7ddb8000       Deferred        libxrender.so.1
ELF     7ddba000-7ddbc000       Deferred        libnvidia-tls.so.1
ELF     7ddbc000-7e57e000       Deferred        libglcore.so.1
ELF     7e57e000-7e603000       Deferred        libgl.so.1
ELF     7e603000-7e6e9000       Deferred        libx11.so.6
ELF     7e6e9000-7e6f6000       Deferred        libxext.so.6
ELF     7e6f6000-7e70e000       Deferred        libice.so.6
ELF     7e70e000-7e790000       Deferred        winex11<elf>
  \-PE  7e720000-7e790000       \               winex11
ELF     7e790000-7e7af000       Deferred        libexpat.so.1
ELF     7e7af000-7e7dd000       Deferred        libfontconfig.so.1
ELF     7e7dd000-7e7f1000       Deferred        libz.so.1
ELF     7e7f1000-7e85a000       Deferred        libfreetype.so.6
ELF     7e85a000-7e8ec000       Deferred        oleaut32<elf>
  \-PE  7e870000-7e8ec000       \               oleaut32
ELF     7e8ec000-7e8ff000       Deferred        libresolv.so.2
ELF     7e8ff000-7e91e000       Deferred        iphlpapi<elf>
  \-PE  7e910000-7e91e000       \               iphlpapi
ELF     7e91e000-7e96d000       Deferred        rpcrt4<elf>
  \-PE  7e930000-7e96d000       \               rpcrt4
ELF     7e96d000-7e9fd000       Deferred        ole32<elf>
  \-PE  7e980000-7e9fd000       \               ole32
ELF     7e9fd000-7ea11000       Deferred        lz32<elf>
  \-PE  7ea00000-7ea11000       \               lz32
ELF     7ea11000-7ea2a000       Deferred        version<elf>
  \-PE  7ea20000-7ea2a000       \               version
ELF     7ea2a000-7ea6e000       Deferred        advapi32<elf>
  \-PE  7ea40000-7ea6e000       \               advapi32
ELF     7ea6e000-7ea78000       Deferred        libgcc_s.so.1
ELF     7eb4d000-7ebff000       Deferred        gdi32<elf>
  \-PE  7eb60000-7ebff000       \               gdi32
ELF     7ebff000-7ed31000       Deferred        user32<elf>
  \-PE  7ec20000-7ed31000       \               user32
ELF     7ed31000-7edf3000       Deferred        comctl32<elf>
  \-PE  7ed40000-7edf3000       \               comctl32
ELF     7ee26000-7ef28000       Export          kernel32<elf>
  \-PE  7ee40000-7ef28000       \               kernel32
ELF     7ef28000-7ef32000       Deferred        libnss_files.so.2
ELF     7ef32000-7ef3b000       Deferred        libnss_nis.so.2
ELF     7ef3b000-7ef50000       Deferred        libnsl.so.1
ELF     7ef50000-7ef72000       Deferred        libm.so.6
ELF     7ef72000-7ef75000       Deferred        libxau.so.6
ELF     7ef75000-7ef7a000       Deferred        libxxf86vm.so.1
ELF     7ef7a000-7ef82000       Deferred        libsm.so.6
ELF     7ef82000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7ce1000-b7cea000       Deferred        libnss_compat.so.2
ELF     b7ceb000-b7cee000       Deferred        libdl.so.2
ELF     b7cee000-b7e1d000       Deferred        libc.so.6
ELF     b7e1d000-b7e2f000       Deferred        libpthread.so.0
ELF     b7e40000-b7f50000       Export          libwine.so.1
ELF     b7f53000-b7f69000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
0000000a
        0000000b    0
00000008 (D) F:\Setup.exe
        00000014    0
        00000009    0 <==

```

any help would be great :-d

---

