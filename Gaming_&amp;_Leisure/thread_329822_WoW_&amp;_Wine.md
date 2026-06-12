---
title: "WoW &amp; Wine"
date: 2007-01-02
forum: Gaming &amp; Leisure
---

### Post by MemoryDump on 2007-01-02
Hi all, 

I just recently just install a fresh copy of Edgy along with all the latest updates.

I updated my Nvidia drivers using the excellent guide located here: [http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)
(everything loaded and is running nicely)

Now, using the guide located here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
 I managed to get Wine and WoW installed (along with all the WoW patches) without any hassles.

Now to my problem/issue.. I setup Wine to use the OSS Driver (using winecfg).
I can load WoW, however I get all kinds of "crackling sounds" when the game is running.
I can login, get to my character selection screen and start loading... however the game crashes/disapears once it's about %75 loaded the load up screen.
If I run WoW using the -d3d option I can get in the game OK and the sound seems to be OK as well.

I followed the instructions like I mentioned from that WoW help page and modified my Config.wtf and Registry settings as instructed.

Any idea/suggestions?

Thanks
-MD

btw: I'm using an IBM Pro M Intellistation system. P4 512MB with a 128MB Nvidia card. (Quatro4 Pro I think)

---

### Post by MemoryDump on 2007-01-02
anybody?
I'd really like to get this working! :D

---

### Post by MemoryDump on 2007-01-02
here's the complete output of when WoW starts in a terminal and ends up crashing:
```
~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c250000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c250000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033f8a4 EBP:0033f8b4 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0033f8bc EBX:00000000 ECX:010dc008 EDX:010de874
 ESI:0c416428 EDI:00d6fab4
Stack dump:
0x0033f8a4:  005c7b51 00000001 0033f8bc 010dc008
0x0033f8b4:  0033f8c8 005c7bee 0c416428 00000001
0x0033f8c4:  0087eda0 0033f8fc 005c396f 00d6fab4
0x0033f8d4:  00000000 00d6fab0 008383f2 00000001
0x0033f8e4:  0085117c 00000008 0033f8ec 0033f8ed
0x0033f8f4:  00000000 00000201 0033f920 00719baf
Backtrace:
=>1 0x00000000 (0x0033f8b4)
  2 0x005c7bee in wow (+0x1c7bee) (0x0033f8c8)
  3 0x005c396f in wow (+0x1c396f) (0x0033f8fc)
  4 0x00719baf in wow (+0x319baf) (0x0033f920)
  5 0x006d8cda in wow (+0x2d8cda) (0x0033f93c)
  6 0x0040193b in wow (+0x193b) (0x0033f958)
  7 0x0046f7f2 in wow (+0x6f7f2) (0x0033fdac)
  8 0x004250a0 in wow (+0x250a0) (0x0033fde0)
  9 0x004219ca in wow (+0x219ca) (0x0033fe04)
  10 0x00421758 in wow (+0x21758) (0x0033fe60)
  11 0x004215e1 in wow (+0x215e1) (0x0033fe78)
  12 0x0040448e in wow (+0x448e) (0x0033ff08)
  13 0x7b8702ce in kernel32 (+0x502ce) (0x0033ffe8)
  14 0xb7ead587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (97 modules)
PE      340000-3d0000   Deferred        fmod
PE      400000-d8d000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7a3db000-7a3ef000       Deferred        mswsock<elf>
  \-PE  7a3e0000-7a3ef000       \               mswsock
ELF     7b800000-7b91b000       Export          kernel32<elf>
  \-PE  7b820000-7b91b000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bfb9000-7c000000       Deferred        dbghelp<elf>
  \-PE  7bfc0000-7c000000       \               dbghelp
ELF     7c255000-7c26a000       Deferred        midimap<elf>
  \-PE  7c260000-7c26a000       \               midimap
ELF     7c26a000-7c2a6000       Deferred        wineoss<elf>
  \-PE  7c270000-7c2a6000       \               wineoss
ELF     7c2c6000-7c2f8000       Deferred        uxtheme<elf>
  \-PE  7c2d0000-7c2f8000       \               uxtheme
ELF     7d20a000-7d21f000       Deferred        psapi<elf>
  \-PE  7d210000-7d21f000       \               psapi
ELF     7d282000-7d288000       Deferred        libnss_dns.so.2
PE      7d410000-7d418000       --none--        msacm32
ELF     7d427000-7d42c000       Deferred        libxfixes.so.3
ELF     7d42c000-7d435000       Deferred        libxcursor.so.1
ELF     7d435000-7d453000       Deferred        ximcp.so.2
ELF     7d453000-7d455000       Deferred        xlcutf8load.so.2
ELF     7d455000-7d458000       Deferred        libxrandr.so.2
ELF     7d458000-7d460000       Deferred        libxrender.so.1
ELF     7d460000-7d463000       Deferred        libxinerama.so.1
ELF     7d989000-7da16000       Deferred        winex11<elf>
  \-PE  7d9a0000-7da16000       \               winex11
ELF     7da16000-7da34000       Deferred        libexpat.so.1
ELF     7da34000-7da63000       Deferred        libfontconfig.so.1
ELF     7da63000-7da77000       Deferred        libz.so.1
ELF     7da77000-7dae1000       Deferred        libfreetype.so.6
ELF     7dae1000-7db00000       Deferred        mpr<elf>
  \-PE  7daf0000-7db00000       \               mpr
ELF     7db00000-7db47000       Deferred        wininet<elf>
  \-PE  7db10000-7db47000       \               wininet
ELF     7db47000-7dbab000       Deferred        msvcrt<elf>
  \-PE  7db60000-7dbab000       \               msvcrt
ELF     7dbab000-7dbd1000       Deferred        msacm32<elf>
ELF     7dbd1000-7dbe5000       Deferred        lz32<elf>
  \-PE  7dbe0000-7dbe5000       \               lz32
ELF     7dbe5000-7dbfe000       Deferred        version<elf>
  \-PE  7dbf0000-7dbfe000       \               version
ELF     7dbfe000-7dc8c000       Deferred        winmm<elf>
  \-PE  7dc10000-7dc8c000       \               winmm
ELF     7dc8c000-7dca8000       Deferred        imm32<elf>
  \-PE  7dc90000-7dca8000       \               imm32
ELF     7dd0d000-7e593000       Deferred        libglcore.so.1
ELF     7e593000-7e598000       Deferred        libxdmcp.so.6
ELF     7e598000-7e612000       Deferred        libglu.so.1
ELF     7e612000-7e69e000       Deferred        libgl.so.1
ELF     7e69e000-7e767000       Deferred        libx11.so.6
ELF     7e767000-7e774000       Deferred        libxext.so.6
ELF     7e774000-7e779000       Deferred        libxxf86vm.so.1
ELF     7e779000-7e791000       Deferred        libice.so.6
ELF     7e791000-7e80a000       Deferred        opengl32<elf>
  \-PE  7e7b0000-7e80a000       \               opengl32
ELF     7e80a000-7e836000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e836000       \               ws2_32
ELF     7e836000-7e850000       Deferred        wsock32<elf>
  \-PE  7e840000-7e850000       \               wsock32
ELF     7e850000-7e863000       Deferred        libresolv.so.2
ELF     7e863000-7e881000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e881000       \               iphlpapi
ELF     7e881000-7e8d5000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d5000       \               rpcrt4
ELF     7e8d5000-7e96d000       Deferred        ole32<elf>
  \-PE  7e8e0000-7e96d000       \               ole32
ELF     7e96d000-7e9c5000       Deferred        shlwapi<elf>
  \-PE  7e980000-7e9c5000       \               shlwapi
ELF     7e9c5000-7eab7000       Deferred        shell32<elf>
  \-PE  7e9e0000-7eab7000       \               shell32
ELF     7eab7000-7eac2000       Deferred        libgcc_s.so.1
ELF     7eac3000-7eac6000       Deferred        libxau.so.6
ELF     7eac6000-7eacf000       Deferred        libsm.so.6
ELF     7ebae000-7ec64000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec64000       \               gdi32
ELF     7ec64000-7ed9c000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9c000       \               user32
ELF     7ed9c000-7ee5c000       Deferred        comctl32<elf>
  \-PE  7edb0000-7ee5c000       \               comctl32
ELF     7ee5c000-7eea2000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea2000       \               advapi32
ELF     7efac000-7efb7000       Deferred        libnss_files.so.2
ELF     7efb7000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff3000       Deferred        libm.so.6
ELF     7eff3000-7eff5000       Deferred        libnvidia-tls.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d43000-b7d4c000       Deferred        libnss_compat.so.2
ELF     b7d4d000-b7d51000       Deferred        libdl.so.2
ELF     b7d51000-b7e85000       Deferred        libc.so.6
ELF     b7e86000-b7e99000       Deferred        libpthread.so.0
ELF     b7ea6000-b7fb7000       Export          libwine.so.1
ELF     b7fb9000-b7fd4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        0000001a    0
        00000018    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    2
        00000011   15
        00000010   15
        0000000f    0
        0000000e    0
        0000000d    1
        00000009    0 <==

```

---

### Post by Sammi on 2007-01-03
I'm a bit stumped. You've tried all the obvious things, exept one that I can think of.

Do you have Beryl/Compiz installed? I fo then try disabling it, or even uninstalling it.



The howto found on WoW's WineHQ Appdb page, might give you more insight:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

---

### Post by willskills on 2007-01-03
You could also try installing aoss, that fixed my sound issues in WoW.

sudo apt-get install aoss

:)

---

### Post by Sammi on 2007-01-03
Yes aoss is good. Directions on how to use aoss with Wine and WoW is explained in the community howto :)

---

### Post by MemoryDump on 2007-01-03
I don't have Beryl or Compiz installed. This is a fresh install like I mentioned with the latest official patches/updates.
I already tried using "aoss" and there's absolutely no difference in what happens. Like I mentioned, the game will load completly if I use the "-d3d" flag. (doesn't crash)
I'll also add that this is a fresh install of WoW (from a DvD) and I've yet to install any addons.

Makes no sense to me at all as to why this ain't working :(

---

### Post by Sammi on 2007-01-03
Can you run this command in a terminal, and post the output?
```
glxinfo | grep rendering
```

You can laso try to add this line to config.wtf:
```
SET ffxDeath "0"
```

---

### Post by MemoryDump on 2007-01-03
> **Sammi said:**
> Can you run this command in a terminal, and post the output?
```
glxinfo | grep rendering
```
direct rendering: Yes

You can laso try to add this line to config.wtf:
```
SET ffxDeath "0"
```
no change.. still crashing at the same spot :confused:

---

### Post by MemoryDump on 2007-01-03
here's my Config.WTF file:

```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET trilinear "1"
SET farclip "357"
SET specular "1"
SET particleDensity "0.600000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET realmName "Ysera"
SET gameTip "13"
SET accountName ""
SET gxCursor "0"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "0.79999995231628"
SET useUiScale "1"
SET M2UseShaders "0"
SET useWeatherShaders "0"
SET ffxDeath "0"

```

---

### Post by Sammi on 2007-01-03
Run this command in a terminal and show me the output:
```
glxgears -printfps
```

---

### Post by MemoryDump on 2007-01-04
```
glxgears -printfps
5011 frames in 5.0 seconds = 1002.023 FPS
4904 frames in 5.0 seconds = 980.688 FPS
8126 frames in 5.0 seconds = 1625.183 FPS
12674 frames in 5.0 seconds = 2534.605 FPS
13236 frames in 5.0 seconds = 2646.107 FPS
5003 frames in 5.0 seconds = 1000.563 FPS
5002 frames in 5.0 seconds = 1000.277 FPS
4996 frames in 5.0 seconds = 999.004 FPS

```
when I minimized the window the FPS's went up naturally :P
seems to me that the FPS's are fine :)

---

### Post by MemoryDump on 2007-01-07
well.. I guess for now I'll stick to Windoze since it's working in there still :D
perhaps 1 day I'll get it working under Linux again
thanks all for the help ;)

---

### Post by bjamesv on 2007-01-13
i have the exact same error for 'wine WoW.exe -opengl',
is there a solution someone's found yet?

```

err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 000e), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033f8a4 EBP:0033f8b4 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0033f8bc EBX:00000000 ECX:01110008 EDX:01112874
 ESI:08d996a8 EDI:00d7dea4
Stack dump:
0x0033f8a4:  005d1cb1 00000001 0033f8bc 01110008
0x0033f8b4:  0033f8c8 005d1d4e 08d996a8 00000000
0x0033f8c4:  008928e0 0033f8fc 005cdacf 00d7dea4
0x0033f8d4:  00000000 00d7dea0 0084ab26 00000001
0x0033f8e4:  00863224 00000008 0033f8ec 0033f8ed
0x0033f8f4:  00000000 00000201 0033f920 0072ae8f
Backtrace:
=>1 0x00000000 (0x0033f8b4)
  2 0x005d1d4e in wow (+0x1d1d4e) (0x0033f8c8)
  3 0x005cdacf in wow (+0x1cdacf) (0x0033f8fc)
  ... etc.

```

this is wine-0.9.29 from the budgetdedicated Edgy repo
winecfg set to 'windows xp' all the full screen flash/etc. effects turned off in -d3d (which works fine, just with garbled icons, etc.)

this is on a perfectly fine Geforce2, using the nvidia xorg driver out of the repos

past login, past character select, load bar reaches 100%..
..how can us ubuntu people make wine stop crashing?](*,)

---

### Post by Sammi on 2007-01-13
Please post the output of these commands:
```
glxinfo | grep vendor[LEFT]glxinfo | grep 'OpenGL version'[/LEFT]

```[LEFT] 
[/LEFT]
 
And let this command run for a while, say 30 seconds, then post the output:
         [LEFT]```
glxgears -printfps

```

Have you tried comparing how the game runs in -opengl and -d3d?
[/LEFT]

---

### Post by bjamesv on 2007-01-13
yes, i have run it in both -d3d and -opengl

d3d: playable at reasonable fps, nice textures/text, all skill or item icons are blacked out or garbled (makes actually playing a pain), minimap works fine.

opengl: i hear all graphics should work in opengl (so i can see my backpack:rolleyes:)
have not found a config that doesnt crash wine though, (character select load bar hits 100% then wine crashes with that error)

results from your questions:
```

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
```
```

OpenGL version string: 1.5.6 NVIDIA 87.76
```
```

5061 frames in 5.0 seconds = 1012.020 FPS
5106 frames in 5.0 seconds = 1021.033 FPS
5071 frames in 5.0 seconds = 1014.039 FPS
```
would be nice to know why opengl cant start with ubuntu.:confused:

---

### Post by blakedev on 2007-01-30
I keep getting a similar error (if you can call it that). The game used to lock the entire system up at runtime, but ceased after I fixed the background downloader and the OSS option in winecfg.
Now, it only does that as soon as I log on to my character, particularly if they are in the Barrens or a starting area. I'm running Edgy with the latest versions of wine and fglrx drivers.
As far as I know there isn't any output as I immediately have to reboot to be able to do anything.

---

### Post by Hylton on 2007-01-31
Same problem, same output as James above (NVidia, Open GL Version 1.5.6, NVIDIA 87.76).
When I try to go in in OpenGL mode, the game crashes at the loading screen with ERROR #132 (Fatal Exception) ... access violation ... The memory could not be "read."

The terminal output says this at the end: 
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

Hylton

---

### Post by Hylton on 2007-01-31
When I run WoW with sudo (i.e. sudo wine WoW.exe) I get different terminal output (and no error message window pops up):

```

err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033f8a4 EBP:0033f8b4 EFLAGS:00210202(   - 00      - -RI1)
 EAX:0033f8bc EBX:00000000 ECX:014b0008 EDX:014b2874
 ESI:0eb647e8 EDI:00d7de3c
Stack dump:
0x0033f8a4:  005d1af1 00000001 0033f8bc 014b0008
0x0033f8b4:  0033f8c8 005d1b8e 0eb647e8 00000212
0x0033f8c4:  00892928 0033f8fc 005cd90f 00d7de3c
0x0033f8d4:  00000000 00d7de38 0084ab16 00000001
0x0033f8e4:  0086324c 00000008 0033f8ec 0033f8ed
0x0033f8f4:  00000000 00000201 0033f920 0072ae0f
Backtrace:
=>1 0x00000000 (0x0033f8b4)
  2 0x005d1b8e in wow (+0x1d1b8e) (0x0033f8c8)
  3 0x005cd90f in wow (+0x1cd90f) (0x0033f8fc)
  4 0x0072ae0f in wow (+0x32ae0f) (0x0033f920)
  5 0x006e95aa in wow (+0x2e95aa) (0x0033f93c)
  6 0x0040198c in wow (+0x198c) (0x0033f958)
  7 0x00471ba4 in wow (+0x71ba4) (0x0033fdac)
  8 0x00426b60 in wow (+0x26b60) (0x0033fde0)
  9 0x0042348a in wow (+0x2348a) (0x0033fe04)
  10 0x00423218 in wow (+0x23218) (0x0033fe60)
  11 0x004230a1 in wow (+0x230a1) (0x0033fe78)
  12 0x00404b0e in wow (+0x4b0e) (0x0033ff08)
  13 0x7b8702be in kernel32 (+0x502be) (0x0033ffe8)
  14 0xb7e9d587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (97 modules)
PE      340000-3d0000   Deferred        fmod
PE      400000-d9b000   Export          wow
PE      10000000-10069000       Deferred        divxdecoder
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7b996000-7b9de000       Deferred        dbghelp<elf>
  \-PE  7b9a0000-7b9de000       \               dbghelp
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf17000-7bf2c000       Deferred        psapi<elf>
  \-PE  7bf20000-7bf2c000       \               psapi
ELF     7c295000-7c2a9000       Deferred        mswsock<elf>
  \-PE  7c2a0000-7c2a9000       \               mswsock
ELF     7cc0a000-7cc10000       Deferred        libnss_dns.so.2
ELF     7cef1000-7cf06000       Deferred        midimap<elf>
  \-PE  7cf00000-7cf06000       \               midimap
PE      7cf10000-7cf1e000       --none--        msacm32
ELF     7cf1e000-7cf5a000       Deferred        wineoss<elf>
  \-PE  7cf30000-7cf5a000       \               wineoss
ELF     7d00f000-7d041000       Deferred        uxtheme<elf>
  \-PE  7d020000-7d041000       \               uxtheme
ELF     7d77d000-7d782000       Deferred        libxfixes.so.3
ELF     7d782000-7d78b000       Deferred        libxcursor.so.1
ELF     7d78b000-7d7a9000       Deferred        ximcp.so.2
ELF     7d7a9000-7d7ab000       Deferred        xlcutf8load.so.2
ELF     7d7ab000-7d7ae000       Deferred        libxrandr.so.2
ELF     7d7ae000-7d7b6000       Deferred        libxrender.so.1
ELF     7d7b6000-7d7b9000       Deferred        libxinerama.so.1
ELF     7da50000-7dadd000       Deferred        winex11<elf>
  \-PE  7da60000-7dadd000       \               winex11
ELF     7dadd000-7dafb000       Deferred        libexpat.so.1
ELF     7dafb000-7db2a000       Deferred        libfontconfig.so.1
ELF     7db2a000-7db3e000       Deferred        libz.so.1
ELF     7db3e000-7dba8000       Deferred        libfreetype.so.6
ELF     7dba8000-7dbc7000       Deferred        mpr<elf>
  \-PE  7dbb0000-7dbc7000       \               mpr
ELF     7dbc7000-7dc0e000       Deferred        wininet<elf>
  \-PE  7dbd0000-7dc0e000       \               wininet
ELF     7dc0e000-7dc72000       Deferred        msvcrt<elf>
  \-PE  7dc20000-7dc72000       \               msvcrt
ELF     7dc72000-7dc98000       Deferred        msacm32<elf>
ELF     7dc98000-7dcac000       Deferred        lz32<elf>
  \-PE  7dca0000-7dcac000       \               lz32
ELF     7dcac000-7dcc5000       Deferred        version<elf>
  \-PE  7dcb0000-7dcc5000       \               version
ELF     7dcc5000-7dd53000       Deferred        winmm<elf>
  \-PE  7dcd0000-7dd53000       \               winmm
ELF     7dd53000-7dd6f000       Deferred        imm32<elf>
  \-PE  7dd60000-7dd6f000       \               imm32
ELF     7ddd2000-7ddd4000       Deferred        libnvidia-tls.so.1
ELF     7ddd4000-7e597000       Deferred        libglcore.so.1
ELF     7e597000-7e59c000       Deferred        libxdmcp.so.6
ELF     7e59c000-7e59f000       Deferred        libxau.so.6
ELF     7e59f000-7e619000       Deferred        libglu.so.1
ELF     7e619000-7e69e000       Deferred        libgl.so.1
ELF     7e69e000-7e767000       Deferred        libx11.so.6
ELF     7e767000-7e774000       Deferred        libxext.so.6
ELF     7e774000-7e779000       Deferred        libxxf86vm.so.1
ELF     7e779000-7e791000       Deferred        libice.so.6
ELF     7e791000-7e80b000       Deferred        opengl32<elf>
  \-PE  7e7b0000-7e80b000       \               opengl32
ELF     7e80b000-7e837000       Deferred        ws2_32<elf>
  \-PE  7e810000-7e837000       \               ws2_32
ELF     7e837000-7e851000       Deferred        wsock32<elf>
  \-PE  7e840000-7e851000       \               wsock32
ELF     7e851000-7e864000       Deferred        libresolv.so.2
ELF     7e864000-7e882000       Deferred        iphlpapi<elf>
  \-PE  7e870000-7e882000       \               iphlpapi
ELF     7e882000-7e8d7000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8d7000       \               rpcrt4
ELF     7e8d7000-7e970000       Deferred        ole32<elf>
  \-PE  7e8f0000-7e970000       \               ole32
ELF     7e970000-7e9c8000       Deferred        shlwapi<elf>
  \-PE  7e980000-7e9c8000       \               shlwapi
ELF     7e9c8000-7eaba000       Deferred        shell32<elf>
  \-PE  7e9e0000-7eaba000       \               shell32
ELF     7eaba000-7eac5000       Deferred        libgcc_s.so.1
ELF     7eac6000-7eacf000       Deferred        libsm.so.6
ELF     7ebae000-7ec65000       Deferred        gdi32<elf>
  \-PE  7ebc0000-7ec65000       \               gdi32
ELF     7ec65000-7ed9e000       Deferred        user32<elf>
  \-PE  7ec80000-7ed9e000       \               user32
ELF     7ed9e000-7ee5e000       Deferred        comctl32<elf>
  \-PE  7edb0000-7ee5e000       \               comctl32
ELF     7ee5e000-7eea4000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea4000       \               advapi32
ELF     7efaf000-7efba000       Deferred        libnss_files.so.2
ELF     7efba000-7efd0000       Deferred        libnsl.so.1
ELF     7efd0000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d36000-b7d3f000       Deferred        libnss_compat.so.2
ELF     b7d40000-b7d44000       Deferred        libdl.so.2
ELF     b7d44000-b7e78000       Deferred        libc.so.6
ELF     b7e79000-b7e8c000       Deferred        libpthread.so.0
ELF     b7e96000-b7fa7000       Export          libwine.so.1
ELF     b7fa9000-b7fc4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\World of Warcraft\WoW.exe
        0000001b    0
        00000019    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000012    0
        00000011    2
        00000010   15
        0000000f   15
        0000000e    0
        0000000d    1
        00000009    0 <==

```

I saw a suggestions in a different thread, and tried this on the WoW folder:
chmod 777 Z:\media\hda3\World of Warcraft\ -R

After doing this, I ran it with 'wine WoW.exe" and got this output:

```

fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
err:wgl:X11DRV_wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
err:wgl:X11DRV_wglCreatePbufferARB ((nil)): unexpected iPixelFormat(0) <= 0, returns NULL
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]

```

So it seems that the OpenGL crash is due to an unhandled page fault on read access...?

---

### Post by dewm_solo on 2007-01-31
I get the same error so I am actively looking for an answer...if I may help in any way let me know.

---

### Post by Hylton on 2007-02-02
I've been looking around a lot for a way to address this problem, and I've seen a number of people complaining about it, but no solutions yet...
I did see a mention that Wine x.x.25 doesn't generate this bug, and it was only after someone updated to 29 (or 30) that it started happening... they recommended installing 25 and starting again, but I haven't been able to check it yet. Have any of you verified this?

---

### Post by hazen on 2007-06-10
Im seeing the same behavior as OP: D3D seems to work ok (on login no bad textures present, but framerate is low), while OpenGL causes freeze at ~70% load after character select page. After about 5 minutes at the frozen loading screen WoW.exe crashes with ERROR #132. I've tried playing with many of the Config.wtf options for graphics, but nothing seems to help. Here's some system info:

Geforce2 GTS AGP 64 MB
Ubuntu 6.06 LTS (Dapper Drake)
wine 0.9.38
nvidia-glx-legacy 1.0.7174+2.6.15.12-28.1

```

$ glxinfo | grep rendering
direct rendering: Yes

```

```

$ glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

```

$ glxinfo | grep 'OpenGL version'
OpenGL version string: 1.5.3 NVIDIA 71.74

```

```

$ glxgears -info
GL_RENDERER   = GeForce2 GTS/AGP/3DNOW!
GL_VERSION    = 1.5.3 NVIDIA 71.74
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
6428 frames in 5.0 seconds = 1285.419 FPS
6450 frames in 5.0 seconds = 1289.840 FPS
6502 frames in 5.0 seconds = 1300.329 FPS
6485 frames in 5.0 seconds = 1296.959 FPS
6492 frames in 5.0 seconds = 1298.299 FPS
6505 frames in 5.0 seconds = 1300.982 FPS
6516 frames in 5.0 seconds = 1303.113 FPS
6491 frames in 5.0 seconds = 1298.117 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

Any ideas? Is the Geforce2 just too old? 64 MB not enough graphics memory for OpenGL mode?

---

### Post by hazen on 2007-06-11
At this point i suspect some AGP-related problem after reading through the appendicies of the nvidia-glx-legacy driver release notes here:

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-7185/README/readme.txt](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-7185/README/readme.txt)

I have an ASUS mobo with AMD Athlon chipset which is what is discussed in appendix F (Configuring AGP) in the doc linked above. I'll perform a bit more investigation and post back here with findings.

---

### Post by hazen on 2007-06-12
I've tried modifying the AGP related settings of the nvidia driver, but still no change in the freeze @ load screen 70% problem. For those interested, these were the steps I took:

[LIST]
[*]updated my ASUS A7V133 Mobo bios from 1001c to 1009
[*]blacklisted the via_agp kernel module
[*]edited xorg.conf to include `Option "NvAGP" "1"`
[/LIST]

After these actions, `cat /proc/driver/nvidia/agp/status` shows this:

```

Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

```

Although `Fast Writes` seem to be supported by my hardware, I've read that various users have had conflicting reports about whether or not enabling this mode helps or hinders performance of AGP graphics.

One other thing to note; when I add `Option "RenderAccel" "true"` to my xorg.conf file, starting Firefox seems to crash the entire system.. I have to hard reboot to get it back to a working state. I thought perhaps this was also due to some AGP issue with my mobo/gfx card combination, but haven't been able to stabilize the system..

My last hope is this: Update from Dapper to Feisty and get the latest nvidia-glx-legacy driver. Aparently the latest release (7185) isn't available through Ubuntu package repositories for Dapper, though I'm not sure why this is...

---

### Post by hazen on 2007-06-12
I forgot to mention-- It seems as though forcing a lower AGP Rate may lend greater stability to the system. I haven't tried this, but unforunately, there is no driver setting which allows simple configuration of the rate. The nvidia driver module must be recompiled from source and installed independently. This makes me a little edgy, because I don't know enough about how the package management on Ubuntu works, so it's likely I'd mess something up and break it.

Can anyone comment who has attempted manual nvidia driver installation?

Also, can anyone comment on the use of `Option "RenderAccel" "true"` with older nvidia cards or the nvidia-glx-legacy driver? Do others have stability issues with this option enabled?

---

### Post by MalGaniz on 2007-07-13
I have the same problem, i've been reading a few threads on many foruns around the network, but i didn't find any solutions.
Anyway, i did read on this thread something interesting about Compiz/Beryl. I have Beryl installed on my Ubuntu, but i don't use it with the XFCE, i can only use it with Gnome, and so, i think that beryl is absolutely disabled on XFCE. How about the Beryl's configuration on the xorg.conf? can it be the reason of all this trouble?:confused:

Repeat: The XFCE isn't configured to run with Beryl, but the xorg.conf still the same

---

