---
title: "World of Warcraft crashes under Wine"
date: 2006-04-26
forum: Gaming &amp; Leisure
---

### Post by eqisow on 2006-04-26
I've been playing WoW under Cedega for awhile now; however, I've heard rumblings that WoW actually performs better under Wine. Wanting to see if this was true, I proceeded to compile Wine from source following the directions on the [Ubuntu Wiki]("https://wiki.ubuntu.com/WorldofWarcraft").

After everything compiled and I installed the new .deb, I ran WoW in Wine from the Cedega install directory. Everything looked great, however the game hard locks while loading into the game world (after character selection) and my only option is to ctrl+alt+backspace and restart X. Sometimes, instead of hardlocking it simply dumps me to the desktop without reseting my desktop res or gamma back to normal. I have tried running WoW in both OpenGL and Direct3D modes.

Thanks in advance for your replies. :)

---

### Post by eqisow on 2006-04-26
Just an additional note, there didn't seem to be any discernable error message upon crashing. As such, I thought it might be helpful to post the full output from whnen wine starts to when it crashes.

```
wine: Unhandled page fault on read access to 0x00000000 at address 0x7ed42ac7 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d560000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d560000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbceedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbcf158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbce4e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fbce53c,0x00000000), stub!
0x7fdb067a: movl        %edi,0x0(%esp)
Modules:
Module  Address                 Debug info      Name (82 modules)
PE      0x00400000-004ae000     Deferred        backgrounddownloader
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e897000-7e89b000     Deferred        libgpg-error.so.0
ELF     0x7e89b000-7e8e7000     Deferred        libgcrypt.so.11
ELF     0x7e8e7000-7e8f7000     Deferred        libtasn1.so.2
ELF     0x7e8f7000-7e924000     Deferred        libcrypt.so.1
ELF     0x7e93a000-7e9a3000     Deferred        libgnutls.so.12
ELF     0x7e9a3000-7e9d0000     Deferred        libcups.so.2
ELF     0x7ea02000-7ea33000     Deferred        uxtheme<elf>
  \-PE  0x7ea10000-7ea33000     \               uxtheme
ELF     0x7ea35000-7ea39000     Deferred        libxfixes.so.3
ELF     0x7ea39000-7ea42000     Deferred        libxcursor.so.1
ELF     0x7ea42000-7ea5e000     Deferred        imm32<elf>
  \-PE  0x7ea50000-7ea5e000     \               imm32
ELF     0x7ea5e000-7ea61000     Deferred        libxrandr.so.2
ELF     0x7ea61000-7ea69000     Deferred        libxrender.so.1
ELF     0x7ea6b000-7f22c000     Deferred        libglcore.so.1
ELF     0x7f22c000-7f2b1000     Deferred        libgl.so.1
ELF     0x7f2b1000-7f2b4000     Deferred        libxau.so.6
ELF     0x7f2b4000-7f39a000     Deferred        libx11.so.6
ELF     0x7f39a000-7f3a7000     Deferred        libxext.so.6
ELF     0x7f3a7000-7f3ac000     Deferred        libxxf86vm.so.1
ELF     0x7f3ac000-7f3c4000     Deferred        libice.so.6
ELF     0x7f3c4000-7f3cc000     Deferred        libsm.so.6
ELF     0x7f3cc000-7f44f000     Deferred        winex11<elf>
  \-PE  0x7f3e0000-7f44f000     \               winex11
ELF     0x7f44f000-7f46e000     Deferred        libexpat.so.1
ELF     0x7f46e000-7f49c000     Deferred        libfontconfig.so.1
ELF     0x7f49c000-7f4b0000     Deferred        libz.so.1
ELF     0x7f4b0000-7f519000     Deferred        libfreetype.so.6
ELF     0x7f519000-7f5b0000     Deferred        oleaut32<elf>
  \-PE  0x7f530000-7f5b0000     \               oleaut32
ELF     0x7f5b0000-7f5de000     Deferred        winspool<elf>
  \-PE  0x7f5c0000-7f5de000     \               winspool
ELF     0x7f5de000-7f67f000     Deferred        comdlg32<elf>
  \-PE  0x7f5f0000-7f67f000     \               comdlg32
ELF     0x7f67f000-7f6a9000     Deferred        ws2_32<elf>
  \-PE  0x7f690000-7f6a9000     \               ws2_32
ELF     0x7f6a9000-7f6c2000     Deferred        version<elf>
  \-PE  0x7f6b0000-7f6c2000     \               version
ELF     0x7f6c2000-7f783000     Deferred        comctl32<elf>
  \-PE  0x7f6d0000-7f783000     \               comctl32
ELF     0x7f783000-7f856000     Deferred        shell32<elf>
  \-PE  0x7f7a0000-7f856000     \               shell32
ELF     0x7f856000-7f8a1000     Deferred        rpcrt4<elf>
  \-PE  0x7f870000-7f8a1000     \               rpcrt4
ELF     0x7f8a1000-7f932000     Deferred        ole32<elf>
  \-PE  0x7f8c0000-7f932000     \               ole32
ELF     0x7f932000-7f98e000     Deferred        shlwapi<elf>
  \-PE  0x7f950000-7f98e000     \               shlwapi
ELF     0x7f98e000-7f998000     Deferred        libgcc_s.so.1
ELF     0x7fa6d000-7fb1e000     Deferred        gdi32<elf>
  \-PE  0x7fa80000-7fb1e000     \               gdi32
ELF     0x7fb1e000-7fc4a000     Deferred        user32<elf>
  \-PE  0x7fb40000-7fc4a000     \               user32
ELF     0x7fc4a000-7fc69000     Deferred        mpr<elf>
  \-PE  0x7fc50000-7fc69000     \               mpr
ELF     0x7fc69000-7fcb0000     Deferred        wininet<elf>
  \-PE  0x7fc70000-7fcb0000     \               wininet
ELF     0x7fcb0000-7fcf1000     Deferred        advapi32<elf>
  \-PE  0x7fcc0000-7fcf1000     \               advapi32
ELF     0x7fcf1000-7fd10000     Deferred        iphlpapi<elf>
  \-PE  0x7fd00000-7fd10000     \               iphlpapi
ELF     0x7fd43000-7fe45000     Export          kernel32<elf>
  \-PE  0x7fd60000-7fe45000     \               kernel32
ELF     0x7fe45000-7fe4f000     Deferred        libnss_files.so.2
ELF     0x7fe4f000-7fe58000     Deferred        libnss_nis.so.2
ELF     0x7fe58000-7fe6d000     Deferred        libnsl.so.1
ELF     0x7fe6d000-7fe8f000     Deferred        libm.so.6
ELF     0x7fe8f000-7ff85000     Deferred        libwine_unicode.so.1
ELF     0x7ff85000-80000000     Deferred        ntdll<elf>
  \-PE  0x7ffa0000-80000000     \               ntdll
ELF     0xb7e21000-b7e26000     Deferred        libxxf86dga.so.1
ELF     0xb7e26000-b7e2f000     Deferred        libnss_compat.so.2
ELF     0xb7e30000-b7e33000     Deferred        libdl.so.2
ELF     0xb7e33000-b7f62000     Deferred        libc.so.6
ELF     0xb7f62000-b7f74000     Deferred        libpthread.so.0
ELF     0xb7f75000-b7f77000     Deferred        libnvidia-tls.so.1
ELF     0xb7f77000-b7f8b000     Deferred        lz32<elf>
  \-PE  0xb7f80000-b7f8b000     \               lz32
ELF     0xb7f8b000-b7fa5000     Deferred        libwine.so.1
ELF     0xb7fa8000-b7fbe000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001c (D) I:\.cedega\World of Warcraft\c_drive\Program Files\World of Warcraft\BackgroundDownloader.exe
        0000001d    0 <==
0000000a
        0000000b    0
00000008 (D) I:\.cedega\World of Warcraft\c_drive\Program Files\World of Warcraft\WoW.exe
        0000001a    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    2
        00000011   15
        00000010    0
        0000000f    0
        0000000e    1
        00000009    0
```

---

### Post by eqisow on 2006-04-26
OK, I've done a bit of fiddling and made some progress. I tried reinstalling from the CD using Wine, it went smoothly but I still had the same problem. After that I moved the .reg files from the Cedega directory and overwrote the ones in the Wine directory. WoW now runs under Wine with only a few problems. These include a stuttering sound in laggy areas as well as sometimes not resetting res and gamma to desktop defaults upon exiting. Also, the WoW Updater opens up every time I start the game. Not in the normal way, but it just pops up in front of the log on screen. I can close it and continue as normal, but it is a bit odd.

I think that Wine seems generally faster but is also a bit more rough around the edges that Cedega. (barring the fact that in Cedega alt+tab doesn't work and going to Windowed mode freezes the game) Anyway, are these issues fairly normal? If so, I don't really know what I'm going to do. A less laggy experience versus a seemingly more stable and smooth experience...

---

### Post by Toxicity999 on 2006-04-28
In that printout its a movie error... possibly the original character movie? are you just creating your character? I know I hate saying pay pay pay buttry the cedega time demo with some tweaks around, see if it's any better. When I get home I'll post my wtf (to those unknowing thats the file ext. for WoW config files.) Try running in false windowed mode also to avoid hardlock issues... it is probable an issue with sound... sound can lockup wine all the time. You get echo chop that shave off a fraction of a second each time until it's gone... meanign a long sound that's executed poorly could presumably go on for a veeeery long time...

Edit: Blah I didn't see the success you had...as for the updater... they use that to check in their retarded way for program modifications, and such.... basicalyl they load the opening loader thang even if you choose to skip it
though it should kill itself... but hey whatever. it works. Try removing 'BackgroundDownloader.exe" and youll get better performance.

---

