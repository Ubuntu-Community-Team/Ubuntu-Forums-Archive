---
title: "WINE won't work for second user"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Grimmy on 2006-03-18
Hi, 

I'm having problems getting wine working for one of the user accounts on my Breezy install.   If I log in as myself it works fine, but if I try and run anything, or even just type wine in the other account I get the following:

```

yoko@numpty:~$ wine
wine: creating configuration directory '/home/yoko/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ea8e13f (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image C:\windows\rundll32.exe
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7ea8e13f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7ea8e13f ESP:7f95fc2c EBP:7f95fc68 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c5447f8 ECX:b7f78900 EDX:7c04a890
 ESI:7c04a890 EDI:7c04a890
Stack dump:
0x7f95fc2c:  7c04a890 7eac39a0 7c04a890 7ea8cab6
0x7f95fc3c:  7c04a890 7c04a890 7eb947d0 7c544810
0x7f95fc4c:  7eae9883 7c04a890 7c544814 00000001
0x7f95fc5c:  7ec320ac 7ec3aeb4 00000000 7f95fc88
0x7f95fc6c:  7ebfdfc7 7c04a890 7ec320ac 7f95fc88
0x7f95fc7c:  7ebfdfb6 7ec320ac 00000001 7f95fdc8
0200: sel=1007 base=7fec4000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ea8e13f in libgl.so.1 (+0x3613f) (0x7ea8e13f)
  2 0x7ebfdfc7 X11DRV_GDI_Finalize+0x27 in winex11 (0x7ebfdfc7)
  3 0x7ec14711 DllMain+0x41 in winex11 (0x7ec14711)
  4 0x7ec2377c in winex11 (+0x5377c) (0x7ec2377c)
  5 0x7bebb105 call_dll_entry_point+0x15 in ntdll (0x7bebb105)
  6 0x7bebbf1a in ntdll (+0x1bf1a) (0x7bebbf1a)
  7 0x7bebc1fa in ntdll (+0x1c1fa) (0x7bebc1fa)
  8 0x7fcdc6a9 ExitProcess+0x19 in kernel32 (0x7fcdc6a9)
  9 0x7f97eb36 in rundll32 (+0xeb36) (0x7f97eb36)
  10 0x7fcddd6f in kernel32 (+0x4dd6f) (0x7fcddd6f)
  11 0xb7f9e177 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f9e177)
0x7ea8e13f: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (95 modules)
ELF     0x7bc78000-7bc90000     Deferred        advpack<elf>
  \-PE  0x7bc80000-7bc90000     \               advpack
ELF     0x7bd68000-7bdc0000     Deferred        shlwapi<elf>
  \-PE  0x7bd80000-7bdc0000     \               shlwapi
ELF     0x7bdc0000-7be86000     Deferred        shell32<elf>
  \-PE  0x7bde0000-7be86000     \               shell32
ELF     0x7be86000-7bf00000     Export          ntdll<elf>
  \-PE  0x7bea0000-7bf00000     \               ntdll
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7bf4b000-7c000000     Deferred        comctl32<elf>
  \-PE  0x7bf50000-7c000000     \               comctl32
ELF     0x7c5a3000-7c5d4000     Deferred        uxtheme<elf>
  \-PE  0x7c5b0000-7c5d4000     \               uxtheme
ELF     0x7c5d4000-7c625000     Deferred        dsound<elf>
  \-PE  0x7c5f0000-7c625000     \               dsound
ELF     0x7c625000-7c680000     Deferred        quartz<elf>
  \-PE  0x7c640000-7c680000     \               quartz
ELF     0x7c7a0000-7c7b5000     Deferred        midimap<elf>
  \-PE  0x7c7b0000-7c7b5000     \               midimap
ELF     0x7c7b5000-7c7cc000     Deferred        msacm<elf>
  \-PE  0x7c7c0000-7c7cc000     \               msacm
ELF     0x7c7cc000-7c80f000     Deferred        wineoss<elf>
  \-PE  0x7c7e0000-7c80f000     \               wineoss
ELF     0x7c833000-7c858000     Deferred        msvfw32<elf>
  \-PE  0x7c840000-7c858000     \               msvfw32
ELF     0x7c858000-7c8e9000     Deferred        oleaut32<elf>
  \-PE  0x7c870000-7c8e9000     \               oleaut32
ELF     0x7c8e9000-7c975000     Deferred        ole32<elf>
  \-PE  0x7c900000-7c975000     \               ole32
ELF     0x7c975000-7c9fc000     Deferred        winmm<elf>
  \-PE  0x7c980000-7c9fc000     \               winmm
ELF     0x7c9fc000-7ca20000     Deferred        msacm32<elf>
  \-PE  0x7ca00000-7ca20000     \               msacm32
ELF     0x7cb3a000-7cb4e000     Deferred        avicap32<elf>
  \-PE  0x7cb40000-7cb4e000     \               avicap32
ELF     0x7cb4e000-7cb75000     Deferred        devenum<elf>
  \-PE  0x7cb60000-7cb75000     \               devenum
ELF     0x7cb75000-7cb93000     Deferred        iphlpapi<elf>
  \-PE  0x7cb80000-7cb93000     \               iphlpapi
ELF     0x7cb93000-7cbdb000     Deferred        rpcrt4<elf>
  \-PE  0x7cba0000-7cbdb000     \               rpcrt4
ELF     0x7cbdb000-7cbef000     Deferred        lz32<elf>
  \-PE  0x7cbe0000-7cbef000     \               lz32
ELF     0x7cbef000-7cc08000     Deferred        version<elf>
  \-PE  0x7cc00000-7cc08000     \               version
ELF     0x7cc08000-7cc5b000     Deferred        setupapi<elf>
  \-PE  0x7cc10000-7cc5b000     \               setupapi
ELF     0x7db2f000-7db38000     Deferred        xomgeneric.so.2
ELF     0x7e2a2000-7e2a6000     Deferred        libxfixes.so.3
ELF     0x7e2a6000-7e2af000     Deferred        libxcursor.so.1
ELF     0x7e2af000-7e2cb000     Deferred        imm32<elf>
  \-PE  0x7e2c0000-7e2cb000     \               imm32
ELF     0x7e2cb000-7e2e7000     Deferred        ximcp.so.2
ELF     0x7e2e7000-7e2ef000     Deferred        libxrender.so.1
ELF     0x7e2ef000-7ea58000     Deferred        libglcore.so.1
ELF     0x7ea58000-7ead7000     Export          libgl.so.1
ELF     0x7ead7000-7eb97000     Deferred        libx11.so.6
ELF     0x7eb97000-7eba4000     Deferred        libxext.so.6
ELF     0x7eba4000-7ebbd000     Deferred        libice.so.6
ELF     0x7ebbd000-7ec3c000     Export          winex11<elf>
  \-PE  0x7ebd0000-7ec3c000     \               winex11
ELF     0x7ec3c000-7ec5b000     Deferred        libexpat.so.1
ELF     0x7ec5b000-7ec89000     Deferred        libfontconfig.so.1
ELF     0x7ec89000-7ec9d000     Deferred        libz.so.1
ELF     0x7ec9d000-7ed07000     Deferred        libfreetype.so.6
ELF     0x7ed07000-7ed45000     Deferred        advapi32<elf>
  \-PE  0x7ed10000-7ed45000     \               advapi32
ELF     0x7ee2b000-7f72e000     Deferred        gdi32<elf>
  \-PE  0x7ee70000-7f72e000     \               gdi32
ELF     0x7f72e000-7f850000     Deferred        user32<elf>
  \-PE  0x7f750000-7f850000     \               user32
ELF     0x7f961000-7f963000     Deferred        xlcutf8load.so.2
ELF     0x7f963000-7f966000     Deferred        libxrandr.so.2
ELF     0x7f968000-7f96c000     Deferred        libxdmcp.so.6
PE      0x7f96c000-7f980000     Export          rundll32
PE      0x7f970000-7f980000     Export          rundll32
ELF     0x7f981000-7f984000     Deferred        libxau.so.6
ELF     0x7f984000-7f98f000     Deferred        libgcc_s.so.1
ELF     0x7fc72000-7fd70000     Export          kernel32<elf>
  \-PE  0x7fc90000-7fd70000     \               kernel32
ELF     0x7fe80000-7fe82000     Deferred        libnvidia-tls.so.1
ELF     0x7fe82000-7fe87000     Deferred        libxxf86vm.so.1
ELF     0x7fe87000-7fe91000     Deferred        libnss_files.so.2
ELF     0x7fe91000-7fe9a000     Deferred        libnss_nis.so.2
ELF     0x7fe9a000-7feaf000     Deferred        libnsl.so.1
ELF     0x7feaf000-7feb8000     Deferred        libnss_compat.so.2
ELF     0x7feb8000-7febd000     Deferred        libxxf86dga.so.1
ELF     0x7febd000-7fec4000     Deferred        libsm.so.6
ELF     0x7fec7000-7fee9000     Deferred        libm.so.6
ELF     0x7fee9000-7ffe0000     Deferred        libwine_unicode.so.1
ELF     0xb7e4a000-b7e4d000     Deferred        libdl.so.2
ELF     0xb7e4d000-b7f7b000     Deferred        libc.so.6
ELF     0xb7f7b000-b7f8d000     Deferred        libpthread.so.0
ELF     0xb7f99000-b7fb3000     Export          libwine.so.1
ELF     0xb7fb6000-b7fcc000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==

```

Is this a permissioning issue or something else I am doing wrong?

---

### Post by YokoZar on 2006-03-18
[QUOTE=Grimmy]Hi, 

I'm having problems getting wine working for one of the user accounts on my Breezy install.   If I log in as myself it works fine, but if I try and run anything, or even just type wine in the other account I get the following:

Is this a permissioning issue or something else I am doing wrong?[/QUOTE]Hmm, Wine crashing on first run doesn't sound right at all.  What version of Wine are you running, and how did you install it?

---

### Post by Grimmy on 2006-03-18
Wine 0.9.10

using 

```

deb http://wine.sourceforge.net/apt/ binary/ 

```

in /etc/apt/sources.list and using apt-get install wine

it seems to work fine with my primary user too.  strange.

---

### Post by dcstar on 2006-03-18
Rename the hidden .wine directory for that user, and try winecfg again.

---

### Post by Gnowm on 2006-03-19
Hi all,

I found this error message too, well its not exact, but close enough. This top is the same

> wine: creating configuration directory '/home/allan/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address [COLOR="Red"]0x7ec2e13f [/COLOR](thread 0009), starting debugger... 
WineDbg starting on pid 0x8

The red coloured text is the bits that differ.
Anyways, installed a clean version of Ubuntu 5.10, used the how-to on this forum to update using automatix. Kudos to Arnieboy btw  :+)

Relevant updates were the nVidia drivers (geforce4 MX) and Wine. I get that error listed above when I ran winecfg. Also when just typing wine at the commandline. 
Display seems to be working fine, I can watch DVD, *.avi MPEG  etc.

Have uninstalled it a few times in case it was a once off, tried the install with both Automatix and apt-get (not concurrently).

Edit bit -- I should add, that its from my only account, not second user.

Version is Unpacking wine (from .../wine_0.9.10~winehq1-1_i386.deb) ...

Anyone have a clue please?

---

### Post by Grimmy on 2006-03-19
[QUOTE=dcstar]Rename the hidden .wine directory for that user, and try winecfg again.[/QUOTE]

Each time it names the .wine directory with a random looking extention e.g .wine-T6f59b

I get the same error for the second user when I run winecfg too.

---

### Post by Grimmy on 2006-03-19
[QUOTE=Gnowm]
Relevant updates were the nVidia drivers (geforce4 MX) and Wine. [/QUOTE]

I am also using a Geforce4 MX, I wonder if there is a connection here.

---

### Post by Gnowm on 2006-03-19
Even tried removing the new nvidia drivers. still same error.
Mmm geForce4 MX is a common enough card, but you never know, may have something to do with it.

---

### Post by Grimmy on 2006-03-21
I managed to fix it.

I Got a new monitor for my main PC today, so I put my old monitor on my second PC (the one with this problem) and when I was reconfiguring xorg I noticed some settings were wrong.

I had 

Load "dri"
Load &#8220;GLcore&#8221;

still enabled whilst using the "nvidia" driver with Load "GLX".... doh!

I commented out these, and now Wine works perfectly.  Very strange.

I also discovered that the reason it was working for the first user, is I was accessing the desktop via VNC, I guess it isn't using the Nvidia driver in that case.

---

### Post by Gnowm on 2006-03-21
Strange you say that, I tried a windows executable (WinMX, for the chat only---) just out of frustration, and even though it coughs up some errors, it still worked. 
All i needed was one mozilla activeX plugin. It does not connect to the network, but i dont care i can still access chat.

> when I was reconfiguring xorg I noticed some settings were wrong.

Where is this file located, is it just called xorg.conf?

And gratz on the resolution, its always better when you fix it yourself  \\:D/

---

### Post by Grimmy on 2006-03-21
/etc/X11/xorg.conf

Although I changed it using dpkg-reconfigure xserver-xorg

---

