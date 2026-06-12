---
title: "Narbacular Drop"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by i-am-me on 2007-09-27
There's this new game coming out in The Orange Box with Half Life 2 and its called Portal. I found it's predecessor, Narbacular Drop, but while installing under wine, even though the reviews on WineHQ are good, I get this error several times:

CoCreateInstance failed; code 0x80070078

Then after installation, when I run it, it just quits on me. The first it said something about no direct input interface.

I'm running Kubuntu 7.04 with WINE 0.9.45.

---

### Post by cogadh on 2007-09-27
That error is rather cryptic, are there any other error messages produced in the terminal when you try to install it?

---

### Post by i-am-me on 2007-09-27
As a matter of fact it does:

```
$ wine "narbacular_drop.exe"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:advapi:CheckTokenMembership ((nil) 0x144ed8 0x34fe24) stub!
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\Narbacular Drop\\unins000.exe") stub
fixme:reg:RegOpenUserClassesRoot (0x1c, 0x0, 0x2000000, 0x34edec) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34edc0
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34ed6c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {00021401-0000-0000-c000-000000000046} 0x34e6e0
```

---

### Post by i-am-me on 2007-09-27
When running the program:
```
$ wine "~/.wine/drive_c/Program Files/Narbacular Drop/Narbacular Drop.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x34f28c,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x13b188) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_UpdateSurface Surfaces has no allocated memory, but should be an in memory only surface
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e1633c0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e1633c0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e1633c0 ESP:0034f1f4 EBP:00000008 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000008 EBX:7ba1bb08 ECX:00000000 EDX:00000002
 ESI:00000000 EDI:7ba1bb08
Stack dump:
0x0034f1f4:  00000000 7ba1bb08 00000000 00000040
0x0034f204:  7ba1bb08 7dfa36c0 7bc395d6 7bc8cbe0
0x0034f214:  7dc939e6 7ba1bb08 00000000 00000100
0x0034f224:  00000002 00391b00 7e1606c0 0034f2e4
0x0034f234:  00000000 7dc9d48a 7c1e0000 0034f2e4
0x0034f244:  00000000 7ba1bb08 0034f2e4 7ba1af10
Backtrace:
=>1 0x7e1633c0 in libglcore.so.1 (+0x5b93c0) (0x00000008)
  2 0x00000000 (0x00000000)
0x7e1633c0: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (77 modules)
PE        400000-  57c000       Deferred        narbacular drop
PE      10000000-10094000       Deferred        fmod
PE      774e0000-7761d000       Deferred        ole32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c243000-7c258000       Deferred        midimap<elf>
  \-PE  7c250000-7c258000       \               midimap
ELF     7c258000-7c31d000       Deferred        libasound.so.2
ELF     7c31d000-7c353000       Deferred        winealsa<elf>
  \-PE  7c330000-7c353000       \               winealsa
ELF     7d567000-7d57f000       Deferred        msacm32<elf>
  \-PE  7d570000-7d57f000       \               msacm32
ELF     7d5c3000-7d5e0000       Deferred        imm32<elf>
  \-PE  7d5d0000-7d5e0000       \               imm32
ELF     7d5e0000-7d5e8000       Deferred        libxrender.so.1
ELF     7dba8000-7dbaa000       Deferred        libnvidia-tls.so.1
ELF     7dbaa000-7e430000       Export          libglcore.so.1
ELF     7e430000-7e4bc000       Deferred        libgl.so.1
ELF     7e4bc000-7e4c1000       Deferred        libxdmcp.so.6
ELF     7e4c1000-7e4c4000       Deferred        libxau.so.6
ELF     7e4c4000-7e5b5000       Deferred        libx11.so.6
ELF     7e5b5000-7e5c3000       Deferred        libxext.so.6
ELF     7e5c3000-7e5c8000       Deferred        libxxf86vm.so.1
ELF     7e5c8000-7e5e0000       Deferred        libice.so.6
ELF     7e5e0000-7e5e9000       Deferred        libsm.so.6
ELF     7e5e9000-7e5ee000       Deferred        libxfixes.so.3
ELF     7e5ee000-7e5f7000       Deferred        libxcursor.so.1
ELF     7e5f7000-7e5fd000       Deferred        libxrandr.so.2
ELF     7e5ff000-7e689000       Deferred        winex11<elf>
  \-PE  7e610000-7e689000       \               winex11
ELF     7e734000-7e754000       Deferred        libexpat.so.1
ELF     7e754000-7e77f000       Deferred        libfontconfig.so.1
ELF     7e77f000-7e794000       Deferred        libz.so.1
ELF     7e794000-7e803000       Deferred        libfreetype.so.6
ELF     7e803000-7e830000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e830000       \               ws2_32
ELF     7e830000-7e84a000       Deferred        wsock32<elf>
  \-PE  7e840000-7e84a000       \               wsock32
ELF     7e84a000-7e8d8000       Deferred        winmm<elf>
  \-PE  7e860000-7e8d8000       \               winmm
ELF     7e8d8000-7e8fe000       Deferred        msacm32<elf>
  \-PE  7e8e0000-7e8fe000       \               msacm32
ELF     7e8fe000-7e911000       Deferred        libresolv.so.2
ELF     7e911000-7e92f000       Deferred        iphlpapi<elf>
  \-PE  7e920000-7e92f000       \               iphlpapi
ELF     7e92f000-7e988000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e988000       \               rpcrt4
ELF     7e988000-7e9ef000       Deferred        msvcrt<elf>
  \-PE  7e9a0000-7e9ef000       \               msvcrt
ELF     7e9ef000-7ea25000       Deferred        dinput<elf>
  \-PE  7ea00000-7ea25000       \               dinput
ELF     7ea25000-7ea3e000       Deferred        dinput8<elf>
  \-PE  7ea30000-7ea3e000       \               dinput8
ELF     7ea3e000-7eb19000       Deferred        wined3d<elf>
  \-PE  7ea50000-7eb19000       \               wined3d
ELF     7eb19000-7eb48000       Deferred        d3d9<elf>
  \-PE  7eb20000-7eb48000       \               d3d9
ELF     7eb48000-7eb90000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb90000       \               advapi32
ELF     7eb90000-7eb9b000       Deferred        libgcc_s.so.1
ELF     7ec9c000-7ed5d000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed5d000       \               gdi32
ELF     7ed5d000-7ee9b000       Deferred        user32<elf>
  \-PE  7ed80000-7ee9b000       \               user32
ELF     7efad000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d34000-b7d3d000       Deferred        libnss_compat.so.2
ELF     b7d3e000-b7d42000       Deferred        libdl.so.2
ELF     b7d42000-b7e8a000       Deferred        libc.so.6
ELF     b7e8b000-b7ea2000       Deferred        libpthread.so.0
ELF     b7eb8000-b7fcc000       Deferred        libwine.so.1
ELF     b7fce000-b7fec000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Program Files\Narbacular Drop\Narbacular Drop.exe
        00000009    0 <==
```

---

### Post by cogadh on 2007-09-27
Hmmm, I don't get any of the same messages when I install it, but they are all "fixme" messages anyway, which are usually just developer notes and usually mean nothing. I've done some customizing of my Wine setup that may be responsible for eliminating those on my end.

However, when I run the game itself, I get the same exact error that you do. I have been having some problems that are very similar to this with other games while using this latest version of Wine. You could try downgrading to an previous Wine version like 0.9.44 to see if the problem continues. You can get archived .deb packages of prior Wine versions here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

EDIT - Just to confirm, I downloaded and installed 0.9.44 and the game runs fine with it, I highly recommend you give it a shot.

---

### Post by i-am-me on 2007-09-28
Hmmm, interesting. I was actually previously running 0.9.43 before I thought upgrading might help. I'll try it out to see if the middle version works.


Update: No It didn't work. I did get the error back though. It says: "Failed to aquire DirectInpur Interface!" and the terminal says:
```
$ wine "~/.wine/drive_c/Program Files/Narbacular Drop/Narbacular Drop.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2b4,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x13b040) : stub, simulating 64MB for now, returning 64MB left
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:reg:RegOpenUserClassesRoot (0x88, 0x0, 0x2000000, 0x34f404) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {25e609e4-b259-11cf-bfc7-444553540000} 0x34f3d8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {25e609e4-b259-11cf-bfc7-444553540000} 0x34f384
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {25e609e4-b259-11cf-bfc7-444553540000} 0x34ecf8
err:dinput:DirectInput8Create CoCreateInstance failed with hr = -2147024776; Try running wineprefixcreate to fix it.
wine: Unhandled page fault on read access to 0x0000001c at address 0x404317 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000001c in 32-bit code (0x00404317).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00404317 ESP:0034f340 EBP:0034f570 EFLAGS:00210297(   - 00     RISAP1C)
 EAX:00000001 EBX:00000000 ECX:00000020 EDX:0034f635
 ESI:00000001 EDI:00000018
Stack dump:
0x0034f340:  007baa9c 007b99ac 0034f601 004097f8
0x0034f350:  00000000 0034f368 00000001 00000003
0x0034f360:  0034f630 00000001 ffffffff 00000015
0x0034f370:  00000000 00000000 00000000 00000000
0x0034f380:  00000000 00000000 00000000 00000000
0x0034f390:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x00404317 in narbacular drop (+0x4317) (0x0034f570)
  2 0x00406d15 in narbacular drop (+0x6d15) (0x007b99ac)
  3 0x0053f89c in narbacular drop (+0x13f89c) (0x0053f230)
  4 0x00407320 in narbacular drop (+0x7320) (0x004058f0)
0x00404317: movl        0x0(%edi,%esi,4),%eax
Modules:
Module  Address                 Debug info      Name (81 modules)
PE        400000-  57c000       Export          narbacular drop
PE      10000000-10094000       Deferred        fmod
PE      774e0000-7761d000       Deferred        ole32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf7f000-7bf97000       Deferred        usp10<elf>
  \-PE  7bf90000-7bf97000       \               usp10
ELF     7bfb7000-7c000000       Deferred        dsound<elf>
  \-PE  7bfc0000-7c000000       \               dsound
ELF     7c24e000-7c263000       Deferred        midimap<elf>
  \-PE  7c250000-7c263000       \               midimap
ELF     7c263000-7c328000       Deferred        libasound.so.2
ELF     7c328000-7c35d000       Deferred        winealsa<elf>
  \-PE  7c330000-7c35d000       \               winealsa
ELF     7d56c000-7d584000       Deferred        msacm32<elf>
  \-PE  7d570000-7d584000       \               msacm32
ELF     7d5c8000-7d5cd000       Deferred        libxfixes.so.3
ELF     7d5cd000-7d5ea000       Deferred        imm32<elf>
  \-PE  7d5d0000-7d5ea000       \               imm32
ELF     7d5ea000-7d5f2000       Deferred        libxrender.so.1
ELF     7dbb2000-7dbb4000       Deferred        libnvidia-tls.so.1
ELF     7dbb4000-7e43a000       Deferred        libglcore.so.1
ELF     7e43a000-7e4c6000       Deferred        libgl.so.1
ELF     7e4c6000-7e4cb000       Deferred        libxdmcp.so.6
ELF     7e4cb000-7e4ce000       Deferred        libxau.so.6
ELF     7e4ce000-7e5bf000       Deferred        libx11.so.6
ELF     7e5bf000-7e5cd000       Deferred        libxext.so.6
ELF     7e5cd000-7e5d2000       Deferred        libxxf86vm.so.1
ELF     7e5d2000-7e5ea000       Deferred        libice.so.6
ELF     7e5ea000-7e5f3000       Deferred        libsm.so.6
ELF     7e5f7000-7e600000       Deferred        libxcursor.so.1
ELF     7e600000-7e606000       Deferred        libxrandr.so.2
ELF     7e609000-7e693000       Deferred        winex11<elf>
  \-PE  7e620000-7e693000       \               winex11
ELF     7e73b000-7e75b000       Deferred        libexpat.so.1
ELF     7e75b000-7e786000       Deferred        libfontconfig.so.1
ELF     7e786000-7e79b000       Deferred        libz.so.1
ELF     7e79b000-7e80a000       Deferred        libfreetype.so.6
ELF     7e80a000-7e837000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e837000       \               ws2_32
ELF     7e837000-7e851000       Deferred        wsock32<elf>
  \-PE  7e840000-7e851000       \               wsock32
ELF     7e851000-7e8df000       Deferred        winmm<elf>
  \-PE  7e860000-7e8df000       \               winmm
ELF     7e8df000-7e905000       Deferred        msacm32<elf>
  \-PE  7e8f0000-7e905000       \               msacm32
ELF     7e905000-7e918000       Deferred        libresolv.so.2
ELF     7e918000-7e936000       Deferred        iphlpapi<elf>
  \-PE  7e920000-7e936000       \               iphlpapi
ELF     7e936000-7e98f000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e98f000       \               rpcrt4
ELF     7e98f000-7e9f6000       Deferred        msvcrt<elf>
  \-PE  7e9a0000-7e9f6000       \               msvcrt
ELF     7e9f6000-7ea2c000       Deferred        dinput<elf>
  \-PE  7ea00000-7ea2c000       \               dinput
ELF     7ea2c000-7ea45000       Deferred        dinput8<elf>
  \-PE  7ea30000-7ea45000       \               dinput8
ELF     7ea45000-7eb1a000       Deferred        wined3d<elf>
  \-PE  7ea60000-7eb1a000       \               wined3d
ELF     7eb1a000-7eb49000       Deferred        d3d9<elf>
  \-PE  7eb20000-7eb49000       \               d3d9
ELF     7eb49000-7eb91000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb91000       \               advapi32
ELF     7eb91000-7eb9c000       Deferred        libgcc_s.so.1
ELF     7ec9d000-7ed5d000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed5d000       \               gdi32
ELF     7ed5d000-7ee9b000       Deferred        user32<elf>
  \-PE  7ed80000-7ee9b000       \               user32
ELF     7efad000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c86000-b7c8f000       Deferred        libnss_compat.so.2
ELF     b7c90000-b7c94000       Deferred        libdl.so.2
ELF     b7c94000-b7ddc000       Deferred        libc.so.6
ELF     b7ddd000-b7df4000       Deferred        libpthread.so.0
ELF     b7e0a000-b7f1e000       Deferred        libwine.so.1
ELF     b7f20000-b7f3e000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Narbacular Drop\Narbacular Drop.exe
        00000010    2
        0000000f   15
        0000000e    0
        0000000d   15
        00000009    0 <==
```

---

### Post by cogadh on 2007-09-28
err:dinput:DirectInput8Create CoCreateInstance failed with hr = -2147024776; **Try running wineprefixcreate to fix it.**

Did you try this?

---

### Post by i-am-me on 2007-09-28
Yep. This is what it said, but running the program still said the same thing.

```
$ wineprefixcreate
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:reg:RegOpenUserClassesRoot (0x8c, 0x0, 0x2000000, 0x34d448) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d41c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d3c8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34cd3c
err:devenum:DEVENUM_RegisterQuartz Failed to register Quartz. Error was 0x80070078)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:reg:RegOpenUserClassesRoot (0x8c, 0x0, 0x2000000, 0x34d588) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d55c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d508
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34ce7c
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:reg:RegOpenUserClassesRoot (0x90, 0x0, 0x2000000, 0x34d538) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d50c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d4b8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34ce2c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb2-524f-11ce-9f53-0020af0ba770} 0x34d50c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb2-524f-11ce-9f53-0020af0ba770} 0x34d4b8
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {e436ebb2-524f-11ce-9f53-0020af0ba770} 0x34ce2c
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:reg:RegOpenUserClassesRoot (0x90, 0x0, 0x2000000, 0x34d4a8) semi-stub
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d47c
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34d428
fixme:actctx:FindActCtxSectionGuid 00000001 (null) 4 {cda42200-bd88-11d0-bd4e-00a0c911ce86} 0x34cd9c
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:setupapi:create_fake_dll failed to create L"c:\\windows\\system32\\ole32.dll" (error=80)
/home/[username]/.wine updated successfully.
```

---

### Post by cogadh on 2007-09-28
Its beginning to look like there is something not quite right with either your Wine configuration or your .wine directory. What are your winecfg settings, most importantly the settings on the Graphics tab? 

Also, just for troubleshooting purposes, try renaming you .wine directory (to something like .wine-old) and create a new one. Then try installing and running the game again. If it doesn't do anything, then you can just delete the new .wine directory and rename the old one back to the original.

---

### Post by i-am-me on 2007-09-28
Here are the first five screenshots of my settings. I'm reinstalling Narbacular Drop with a new wine directory right now

---

### Post by i-am-me on 2007-09-28
Last one.


Update: It turns out it works with the new directory. If only I knew what was wrong with the old one. I still get white boxes for the menus though, but I'll hope an upgrade will fix that. Now, what part of my config was bad...............

Update2:The upgrade to 0.9.45 didnt fix the menu problem........ great.

---

### Post by cogadh on 2007-09-29
Is there a particular reason for those two library overrides?

---

### Post by i-am-me on 2007-09-29
i don't really remember. It was for something I installed, but I don't really remember what or if I still use it. I'll get rid of them and try again.

Update: I get a new error in both the new and old directories. Something to do with sound. It starts the debugger, then quits:
```

err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=63304, mixpos=17744/17832 (16300/16384), primary_mixpos=10056, writepos=12288, mixlen=8192
```

---

