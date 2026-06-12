---
title: "Starcraft crashes when try to log into battle.net"
date: 2006-06-28
forum: Gaming &amp; Leisure
---

### Post by glasyalabolis on 2006-06-28
Hi, I have the latest wine and I have the latest patch from blizard. When I click on OK after selecting U.S. East it goes to the "connecting.." screen then Starcraft crashes leaving my resolution at 640x480.
This is what wine outputs in the terminal,

```
ron@the-glass-machine:~$ wine .wine/drive_c/Program\ Files/Starcraft/starcraft.exe
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7fd48728) : stub, emulating 64MB for now, returning 64MB
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x7fd480d0)->(0x10024,00000013)fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8wine: Unhandled page fault on write access to 0x7cf7b000 at address 0x7db101a4 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x7cf7b000 in 32-bit code (0x7db101a4).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7db101a4 ESP:7fb8ecdc EBP:7fb8ed90 EFLAGS:00210206(   - 00      - RIP1) EAX:c7c7c7c7 EBX:7db1019c ECX:00000000 EDX:00000019
 ESI:71e10014 EDI:7cf7b000
Stack dump:
0x7fb8ecdc:  00000000 7cf7b000 7cf7b000 00000000
0x7fb8ecec:  71e10010 7d0c4566 7fd97670 7fb8ed28
0x7fb8ecfc:  00000000 00000001 0000000b 7c046a60
0x7fb8ed0c:  00000084 7f1091d8 7c03dff8 7f1ac760
0x7fb8ed1c:  7fd975c8 7f1046f4 7c03e548 00000280
0x7fb8ed2c:  7cf30000 7fb8eeac 00000040 15047b88
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7db101a4 (0x7db101a4)
  2 0x15007d08 in storm (+0x7d08) (0x15007d08)
  3 0x00000000 (0x00000000)
0x7db101a4: movl        %eax,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (102 modules)
PE      0x00400000-006d5000     Deferred        starcraft
PE      0x02000000-02011000     Deferred        local
PE      0x10000000-1001a000     Deferred        smackw32
PE      0x15000000-15054000     Export          storm
PE      0x19000000-19083000     Deferred        battle.snp
ELF     0x724b6000-724e0000     Deferred        ws2_32<elf>
  \-PE  0x724c0000-724e0000     \               ws2_32
ELF     0x736d6000-736f0000     Deferred        wsock32<elf>
  \-PE  0x736e0000-736f0000     \               wsock32
ELF     0x73b9b000-73bb0000     Deferred        midimap<elf>
  \-PE  0x73ba0000-73bb0000     \               midimap
ELF     0x73cf6000-73dab000     Deferred        libasound.so.2
ELF     0x73dab000-73dd4000     Deferred        winealsa<elf>
  \-PE  0x73db0000-73dd4000     \               winealsa
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7bf0f000-7bf97000     Deferred        winmm<elf>
  \-PE  0x7bf20000-7bf97000     \               winmm
ELF     0x7bf97000-7bfe0000     Deferred        dsound<elf>
  \-PE  0x7bfa0000-7bfe0000     \               dsound
ELF     0x7cef8000-7cf10000     Deferred        msacm32<elf>
  \-PE  0x7cf00000-7cf10000     \               msacm32
ELF     0x7cf81000-7cff7000     Deferred        libglu.so.1
ELF     0x7cff7000-7d098000     Deferred        wined3d<elf>
  \-PE  0x7d000000-7d098000     \               wined3d
ELF     0x7d098000-7d0e0000     Deferred        ddraw<elf>
  \-PE  0x7d0a0000-7d0e0000     \               ddraw
ELF     0x7dc06000-7dc0a000     Deferred        libgpg-error.so.0
ELF     0x7dc0a000-7dc56000     Deferred        libgcrypt.so.11
ELF     0x7dc56000-7dc83000     Deferred        libcrypt.so.1
ELF     0x7dc9a000-7dd03000     Deferred        libgnutls.so.12
ELF     0x7dd03000-7dd30000     Deferred        libcups.so.2
ELF     0x7dd70000-7dd80000     Deferred        libtasn1.so.2
ELF     0x7dd9d000-7ddce000     Deferred        uxtheme<elf>
  \-PE  0x7dda0000-7ddce000     \               uxtheme
ELF     0x7ddce000-7ddd7000     Deferred        libxcursor.so.1
ELF     0x7e657000-7e65f000     Deferred        librt.so.1
ELF     0x7e661000-7e665000     Deferred        libxfixes.so.3
ELF     0x7e730000-7f02b000     Deferred        fglrx_dri.so
ELF     0x7f02b000-7f0cb000     Deferred        libgl.so.1
ELF     0x7f0cb000-7f1b1000     Deferred        libx11.so.6
ELF     0x7f1b1000-7f1be000     Deferred        libxext.so.6
ELF     0x7f1be000-7f1d6000     Deferred        libice.so.6
ELF     0x7f1d6000-7f259000     Deferred        winex11<elf>
  \-PE  0x7f1f0000-7f259000     \               winex11
ELF     0x7f259000-7f278000     Deferred        libexpat.so.1
ELF     0x7f278000-7f2a6000     Deferred        libfontconfig.so.1
ELF     0x7f2a6000-7f30f000     Deferred        libfreetype.so.6
ELF     0x7f30f000-7f32b000     Deferred        imm32<elf>
  \-PE  0x7f320000-7f32b000     \               imm32
ELF     0x7f32b000-7f33f000     Deferred        lz32<elf>
  \-PE  0x7f330000-7f33f000     \               lz32
ELF     0x7f33f000-7f358000     Deferred        version<elf>
  \-PE  0x7f350000-7f358000     \               version
ELF     0x7f358000-7f387000     Deferred        winspool<elf>
  \-PE  0x7f360000-7f387000     \               winspool
ELF     0x7f387000-7f449000     Deferred        comctl32<elf>
  \-PE  0x7f390000-7f449000     \               comctl32
ELF     0x7f449000-7f468000     Deferred        iphlpapi<elf>
  \-PE  0x7f450000-7f468000     \               iphlpapi
ELF     0x7f468000-7f4b5000     Deferred        rpcrt4<elf>
  \-PE  0x7f470000-7f4b5000     \               rpcrt4
ELF     0x7f58a000-7f63b000     Deferred        gdi32<elf>
  \-PE  0x7f5a0000-7f63b000     \               gdi32
ELF     0x7f63b000-7f76d000     Deferred        user32<elf>
  \-PE  0x7f660000-7f76d000     \               user32
ELF     0x7f76d000-7f7fc000     Deferred        ole32<elf>
  \-PE  0x7f780000-7f7fc000     \               ole32
ELF     0x7f7fc000-7f852000     Deferred        shlwapi<elf>
  \-PE  0x7f810000-7f852000     \               shlwapi
ELF     0x7f852000-7f929000     Deferred        shell32<elf>
  \-PE  0x7f860000-7f929000     \               shell32
ELF     0x7f929000-7f9c4000     Deferred        comdlg32<elf>
  \-PE  0x7f930000-7f9c4000     \               comdlg32
ELF     0x7f9c4000-7fa05000     Deferred        advapi32<elf>
  \-PE  0x7f9d0000-7fa05000     \               advapi32
ELF     0x7fa05000-7fa66000     Deferred        msvcrt<elf>
  \-PE  0x7fa10000-7fa66000     \               msvcrt
ELF     0x7fa66000-7fa80000     Deferred        crtdll<elf>
  \-PE  0x7fa70000-7fa80000     \               crtdll
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
ELF     0x7fb9b000-7fba0000     Deferred        libxxf86vm.so.1
ELF     0x7fba4000-7fbac000     Deferred        libsm.so.6
ELF     0x7fbdf000-7fce0000     Deferred        kernel32<elf>
  \-PE  0x7fc00000-7fce0000     \               kernel32
ELF     0x7fdf2000-7fdfc000     Deferred        libgcc_s.so.1
ELF     0x7fdfc000-7fe11000     Deferred        libnsl.so.1
ELF     0x7fe11000-7fe1a000     Deferred        libnss_compat.so.2
ELF     0x7fe1a000-7fe1d000     Deferred        libxrandr.so.2
ELF     0x7fe1d000-7fe31000     Deferred        libz.so.1
ELF     0x7fe31000-7fe53000     Deferred        libm.so.6
ELF     0x7fe53000-7fe5d000     Deferred        libnss_files.so.2
ELF     0x7fe5d000-7fe66000     Deferred        libnss_nis.so.2
ELF     0x7fe6a000-7ff62000     Deferred        libwine_unicode.so.1
ELF     0x7ff62000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff70000-7ffe0000     \               ntdll
ELF     0xb7d92000-b7d97000     Deferred        libxxf86dga.so.1
ELF     0xb7d98000-b7d9b000     Deferred        libdl.so.2
ELF     0xb7d9b000-b7eca000     Deferred        libc.so.6
ELF     0xb7eca000-b7edc000     Deferred        libpthread.so.0
ELF     0xb7ef1000-b7ef4000     Deferred        libxau.so.6
ELF     0xb7ef4000-b7f0e000     Deferred        libwine.so.1
ELF     0xb7f11000-b7f27000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b
        0000000c    0
00000008 (D) H:\.wine\drive_c\Program Files\Starcraft\starcraft.exe
        0000000f    2
        0000000e    0
        0000000d   15
        0000000a    1
        00000009    0 <==

```

any help would be appreciated, thx.

---

### Post by Somenoob on 2006-06-28
A little unrelated, but how does Starcraft run on your wine? i heard it lags quite much under wine.

---

### Post by andb on 2006-06-29
You may first want to try just playing starcraft single player vs. computer before you put time into this. I've found wine very dissapointing, especially playing against good competitors. Move between windows and the performance is terrible. I began experimenting with qemu-kqemu and am more satisfied. You have to set up networking via a bridge and tun/tap, but once setup it works well. Plus with -snapshot you know you always start with a perfect machine. I have a p4 2.8, 512mb, so nothing too special. kqemu is really needed, so with an AMD, you'll need more juice. 

This will help to set it up:
[http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto](http://ubuntuforums.org/showthread.php?t=187413&highlight=qemu+howto)

The following link will help with networking though its not totally complete:
[http://ubuntuforums.org/showthread.php?t=66694&highlight=qemu+bridge](http://ubuntuforums.org/showthread.php?t=66694&highlight=qemu+bridge)

Could be done with VMware, but I prefer the non-comercial product. Im hoping to make a nice howto soon, the setup is much better than wine, and if this works for you, you wont have to debug your issue ;)

---

### Post by lord_zerg on 2006-07-09
same problem here.
game runs ok on single player, and i can also play on a lan.
but trying to connect to battle.net crashes wine

---

