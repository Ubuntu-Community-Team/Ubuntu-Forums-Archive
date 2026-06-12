---
title: "Panzers - Phase 1"
date: 2005-11-30
forum: Gaming &amp; Leisure
---

### Post by Cuppa-Chino on 2005-11-30
Hi,

anybody tried running Panzers Phase 1 on a Ubuntu-box? I tried and it installed very nicely (including the patches) - output from wine installation was:
```
penguin@penguin-ubuntu:~$ wine "G:\Setup.exe"
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\PANZERS - Phase1\\Misc\\cdv.ico") failed, error 193
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\PANZERS - Phase1\\Misc\\PANZERS - Phase1.ico") failed, error 193
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\PANZERS - Phase1\\Misc\\gamespy.ico") failed, error 193
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\windows\\system32\\notepad.exe \"C:\\Program Files\\PANZERS - Phase1\\ReadMe.txt\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\Program Files\\PANZERS - Phase1\\Misc\\cdv.ico") failed, error 193
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
penguin@penguin-ubuntu:~$
penguin@penguin-ubuntu:~$ wine "c:\Panzers_Patch_V1_10_INTERNATIONAL.exe"
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
penguin@penguin-ubuntu:~$ wine "c:\Panzers_MODpatch_V1_10_INTERNATIONAL.exe" err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:extract_icon32 LoadLibraryExW (L"c:\\windows\\system32\\notepad.exe \"C:\\Program Files\\PANZERS - Phase1\\ReadMe_MODpatch.txt\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
penguin@penguin-ubuntu:~$
```

but as far as I can see the only complaints are about the UnloadNow stub



 but during startup I got the following errors:

```
penguin@penguin-ubuntu:~$ wine "c:\Program Files\Panzers - Phase1\Run\Panzers.exe" wine: Unhandled page fault on read access to 0x00000000 at address 0x7e762692 (t hread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7 e762692).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7e762692 ESP:7fb2f9a0 EBP:7fb2f9b4 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7fb2fad8 ECX:0000001d EDX:7fb2fad8
 ESI:7fde09e0 EDI:00000000
Stack dump:
0x7fb2f9a0:  00000000 7fde09e0 7fb2fad8 0000001d
0x7fb2f9b0:  0000001d 7fb2fbe0 7e76265f 00000000
0x7fb2f9c0:  7eaf926c 00000001 00000005 00000002
0x7fb2f9d0:  7379535c 526d6574 5c746f6f 74737953
0x7fb2f9e0:  32336d65 6972645c 73726576 6f72705c
0x7fb2f9f0:  636e7973 79732e31 7bec0073 7fb2fa08
0200: sel=1007 base=7fee4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7e762692 in protect (+0x2692) (0x7e762692)
  2 0x7e76265f in protect (+0x265f) (0x7e76265f)
  3 0x7e762515 in protect (+0x2515) (0x7e762515)
  4 0x7e761956 in protect (+0x1956) (0x7e761956)
  5 0x7e76189c in protect (+0x189c) (0x7e76189c)
  6 0x7bebecd2 call_dll_entry_point+0x12 in ntdll (0x7bebecd2)
  7 0x7bebfaaa in ntdll (+0x1faaa) (0x7bebfaaa)
  8 0x7bec03ac in ntdll (+0x203ac) (0x7bec03ac)
  9 0x7bec0382 in ntdll (+0x20382) (0x7bec0382)
  10 0x7bec2955 LdrInitializeThunk+0x345 in ntdll (0x7bec2955)
  11 0x7fcfb35d in kernel32 (+0x4b35d) (0x7fcfb35d)
  12 0xb7f42c11 wine_switch_to_stack+0x11 in libwine.so.1 (0xb7f42c11)
0x7e762692: cmpb        %al,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (79 modules)
PE      0x00400000-007d4000     Deferred        panzers
PE      0x21100000-2115f000     Deferred        mss32
PE      0x30000000-30072000     Deferred        binkw32
PE      0x65f00000-65fc2000     Deferred        ole32
ELF     0x7397c000-7397e000     Deferred        xlcutf8load.so.2
ELF     0x7be8d000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7db8b000-7dba0000     Deferred        midimap<elf>
  \-PE  0x7db90000-7dba0000     \               midimap
ELF     0x7dcbb000-7dcdc000     Deferred        msacm32<elf>
  \-PE  0x7dcc0000-7dcdc000     \               msacm32
ELF     0x7dcdc000-7dcf3000     Deferred        msacm.drv<elf>
  \-PE  0x7dce0000-7dcf3000     \               msacm.drv
ELF     0x7dcf3000-7dd35000     Deferred        wineoss.drv<elf>
  \-PE  0x7dd00000-7dd35000     \               wineoss.drv
ELF     0x7dd79000-7dd82000     Deferred        libxcursor.so.1
ELF     0x7dd82000-7dd9e000     Deferred        imm32<elf>
  \-PE  0x7dd90000-7dd9e000     \               imm32
ELF     0x7dd9e000-7ddba000     Deferred        ximcp.so.2
ELF     0x7de74000-7e5e2000     Deferred        fglrx_dri.so
ELF     0x7e5e2000-7e65d000     Deferred        winex11.drv<elf>
  \-PE  0x7e5f0000-7e65d000     \               winex11.drv
ELF     0x7e65d000-7e67c000     Deferred        libexpat.so.1
ELF     0x7e67c000-7e6aa000     Deferred        libfontconfig.so.1
ELF     0x7e6ae000-7e6b6000     Deferred        libxrender.so.1
ELF     0x7e6b6000-7e6ca000     Deferred        libz.so.1
ELF     0x7e6ca000-7e734000     Deferred        libfreetype.so.6
ELF     0x7e734000-7e748000     Deferred        lz32<elf>
  \-PE  0x7e740000-7e748000     \               lz32
ELF     0x7e748000-7e760000     Deferred        version<elf>
  \-PE  0x7e750000-7e760000     \               version
PE      0x7e760000-7eb11000     Export          protect
ELF     0x7eb13000-7eb17000     Deferred        libxfixes.so.3
ELF     0x7eb17000-7eb1f000     Deferred        librt.so.1
ELF     0x7eb1f000-7eb3a000     Deferred        wsock32<elf>
  \-PE  0x7eb30000-7eb3a000     \               wsock32
ELF     0x7eb3a000-7ebbf000     Deferred        wined3d<elf>
  \-PE  0x7eb50000-7ebbf000     \               wined3d
ELF     0x7ebbf000-7ebc3000     Deferred        libxdmcp.so.6
ELF     0x7ebc3000-7ec39000     Deferred        libglu.so.1
ELF     0x7ec39000-7ecd8000     Deferred        libgl.so.1
ELF     0x7ecd8000-7ed98000     Deferred        libx11.so.6
ELF     0x7ed98000-7eda5000     Deferred        libxext.so.6
ELF     0x7eda5000-7edbe000     Deferred        libice.so.6
ELF     0x7edbe000-7edeb000     Deferred        d3d9<elf>
  \-PE  0x7edd0000-7edeb000     \               d3d9
ELF     0x7edeb000-7ee36000     Deferred        dsound<elf>
  \-PE  0x7ee00000-7ee36000     \               dsound
ELF     0x7ee36000-7ee53000     Deferred        iphlpapi<elf>
  \-PE  0x7ee40000-7ee53000     \               iphlpapi
ELF     0x7ee53000-7ee7d000     Deferred        ws2_32<elf>
  \-PE  0x7ee60000-7ee7d000     \               ws2_32
ELF     0x7ee7d000-7eefa000     Deferred        winmm<elf>
  \-PE  0x7ee90000-7eefa000     \               winmm
ELF     0x7efe0000-7f8e0000     Deferred        gdi32<elf>
  \-PE  0x7f030000-7f8e0000     \               gdi32
ELF     0x7f8e0000-7f9f6000     Deferred        user32<elf>
  \-PE  0x7f900000-7f9f6000     \               user32
ELF     0x7f9f6000-7fa30000     Deferred        advapi32<elf>
  \-PE  0x7fa00000-7fa30000     \               advapi32
ELF     0x7fb33000-7fb36000     Deferred        libxau.so.6
ELF     0x7fb36000-7fb3b000     Deferred        libxxf86vm.so.1
ELF     0x7fb3b000-7fb40000     Deferred        libxxf86dga.so.1
ELF     0x7fb42000-7fb4d000     Deferred        libgcc_s.so.1
ELF     0x7fc95000-7fd90000     Export          kernel32<elf>
  \-PE  0x7fcb0000-7fd90000     \               kernel32
ELF     0x7fea0000-7fea7000     Deferred        libsm.so.6
ELF     0x7fea7000-7feb1000     Deferred        libnss_files.so.2
ELF     0x7feb1000-7feba000     Deferred        libnss_nis.so.2
ELF     0x7feba000-7fecf000     Deferred        libnsl.so.1
ELF     0x7fecf000-7fed8000     Deferred        libnss_compat.so.2
ELF     0x7fee7000-7ff09000     Deferred        libm.so.6
ELF     0x7ff09000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7dfa000-b7dfd000     Deferred        libdl.so.2
ELF     0xb7dfd000-b7f2b000     Deferred        libc.so.6
ELF     0xb7f2c000-b7f3e000     Deferred        libpthread.so.0
ELF     0xb7f3e000-b7f58000     Export          libwine.so.1
ELF     0xb7f67000-b7f7d000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Panzers - Phase1\Run\Panzers.exe
        00000009    0 <==

```

and the attached pic:

the latter points me towards a copy protection mechanism I think, from recollection it was a bit picky in windo$ which drive the cd's where in... any ideas?

---

### Post by ltmon on 2005-11-30
I have almost always had to use a "nocd" crack to get windows programs (e.g. Warcraft III) to work under wine.  The copy protection systems just don't seem to find the CD correctly.

L.

---

### Post by Zeroedout on 2005-11-30
[quote=ltmon]I have almost always had to use a "nocd" crack to get windows programs (e.g. Warcraft III) to work under wine. The copy protection systems just don't seem to find the CD correctly.

L.[/quote]

That's why their is cedega. I personally do not like cedega, but the reason the comercial version is closed source is because they are implementing alot of the copy protection. Try it with cedega, and it may work.

---

