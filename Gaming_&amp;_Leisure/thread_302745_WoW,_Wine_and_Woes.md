---
title: "WoW, Wine and Woes"
date: 2006-11-19
forum: Gaming &amp; Leisure
---

### Post by montag451 on 2006-11-19
My attempt to get WoW to work with Wine on my Dapper installation has gone anything but smoothly. Originally, I tried the following guide that used Wine 0.9.6: [http://www.ubuntuforums.org/showthread.php?t=120615](http://www.ubuntuforums.org/showthread.php?t=120615)

This was wrought with problems, but I eventually got it to work without crashing at startup, with sound working properly, and with a framerate of about 9-10 fps, although I couldn't interact with anything in-game other than my visible interface.

That was the most progress I've made so far. A few times, people suggested I try 0.9.25, and I've seen more than one success story that had it running out of the box. So, I tried 0.9.25 and got some good results, but this continually crashed every time I logged into the world. The WoW-dedicated Wine page lists 0.9.24 with an NVIDIA patch as the most stable release so far, so I tried that. This gave me the worst results yet, with WoW crashing the moment it starts up.

I have done the DisabledExtentions trick in the registry, re-installed my video drivers, and scoured the forums and Wine WoW page for information, but there doesn't seem to be much. Mostly just success stories or small problems, so I wonder what I'm doing wrong.

I've done about as much research as I can on these problems, so now I'm turning to some human beings. Each time I uninstall wine I use 'sudo make uninstall', then install the new version with './configure', 'make depend && make', and 'make install'. I'm not sure if there are artifacts being left over from previous installations and if this is affecting my attempts. I'm also unaware of any problems WoW/Wine might have with certain Addons, but I do have plenty of them.

I'm currently running Dapper on a laptop with built-in ATI Radeon Mobility X1600. I'm using fglrx version 8.29.6 running WoW on opengl graphics. Config.wtf has most of the quality levels turned up to full, but I have turned off the glow effect, the death effect, trilineral filtering, and all pixel shaders.

I'm relatively new to linux, so the more detailed you can be in any explaination you give, the better.

---

### Post by Sammi on 2006-11-19
I recomend getting a pristine deb of Wine 0.9.25 from the official Ubuntu Wine repositories.

See here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

This worked almost out of the box for me. Just needed to  add these lines in  config.wtf:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
```
The thing is, that different from you, I am using a Nvidia video card :twisted:

---

### Post by Ferrat on 2006-11-20
> **Sammi said:**
> I recomend getting a pristine deb of Wine 0.9.25 from the official Ubuntu Wine repositories.

See here: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

This worked almost out of the box for me. Just needed to  add these lines in  config.wtf:
```
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxApi "OpenGL"
```
The thing is, that different from you, I am using a Nvidia video card :twisted:

There is no diffirence in setup if he already got the graficcard running with 3d rendering, the installation for WoW and Wine doesn't change but he has to turnoff death and glow effects inside WoW but that takes about 2sec and Gloweffects you should turn of anyway so you don't get the blur effect for ex. in ZG by the spiders ;P

---

### Post by montag451 on 2006-11-22
Glow and Death effects are off for me.

I have recently tried installing Wine 0.9.25 from Synaptic. WoW crashes at startup, just as with the compiled version of 0.9.25. I've searched around and can't find a definitive answer to the problem since most people report 0.9.25 as being fine with WoW out of the box.

The following is my Config.wtf:
```

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxMultisampleQuality "0.000000"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET mouseSpeed "1.1000000238419"
SET Gamma "1.000000"
SET MusicVolume "0.5"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmName "Balnazzar"
SET cameraYawMoveSpeed "230"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET gameTip "74"
SET ChatBubblesParty "1"
SET AmbienceVolume "0.80000001192093"
SET uiScale "0.63999998569489"
SET useUiScale "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET spamFilter "0"
SET ffxGlow "0"
SET guildMemberNotify "1"
SET checkAddonVersion "0"
SET profanityFilter "0"
SET shadowLevel "0"
SET weatherDensity "3"
SET scriptMemory "97280"
SET movieSubtitle "1"
SET PreferedLocale "enUS"
SET minimapZoom "2"
SET minimapInsideZoom "2"
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET ffxDeath "0"

```

**Edit:** Also, in 0.9.25, I've gotten no sound on 1, 2, 4, and 6 values for SoundOutputSystem.

**Edit:** I recently tried a couple of things and found out some interesting but still unsuccessful results. First, I deleted all my addons (except the Blizzard ones) which, instead of crashing my X server on logging into the world, simply crashed the WoW program and gave me the normal "I crashed" debug screen I've seen in Windows. After that, I deleted the World of Warcraft directory and did a fresh install. This gave me the same result: Crashing the WoW program upon logging into the world.

---

### Post by Sammi on 2006-11-22
> **montag451 said:**
> ...This gave me the same result: Crashing the WoW program upon **logging into the world.**

You're saying that you can launch the game and log in, but when you choose a character and press the key to enter the world it crashes?

---

### Post by justin whitaker on 2006-11-22
Yeah, Sammi, that's what I think he is saying.

First: Blizzard is tinkering with the servers, logins, etc. the past day or so-they are beginning to preload the expansion. That's going to break some stuff.

Next: Did you try setting SET gxApi "opengl" to "D3D"?

No idea about sound. Will look into it.

---

### Post by Ferrat on 2006-11-22
> **montag451 said:**
> Glow and Death effects are off for me.

I have recently tried installing Wine 0.9.25 from Synaptic. WoW crashes at startup, just as with the compiled version of 0.9.25. I've searched around and can't find a definitive answer to the problem since most people report 0.9.25 as being fine with WoW out of the box.

The following is my Config.wtf:
```

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1680x1050"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET frillDensity "48"
SET farclip "777"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxMultisampleQuality "0.000000"
SET anisotropic "16"
SET M2UsePixelShaders "1"
SET mouseSpeed "1.1000000238419"
SET Gamma "1.000000"
SET MusicVolume "0.5"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmName "Balnazzar"
SET cameraYawMoveSpeed "230"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET gameTip "74"
SET ChatBubblesParty "1"
SET AmbienceVolume "0.80000001192093"
SET uiScale "0.63999998569489"
SET useUiScale "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET spamFilter "0"
SET ffxGlow "0"
SET guildMemberNotify "1"
SET checkAddonVersion "0"
SET profanityFilter "0"
SET shadowLevel "0"
SET weatherDensity "3"
SET scriptMemory "97280"
SET movieSubtitle "1"
SET PreferedLocale "enUS"
SET minimapZoom "2"
SET minimapInsideZoom "2"
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET ffxDeath "0"

```

**Edit:** Also, in 0.9.25, I've gotten no sound on 1, 2, 4, and 6 values for SoundOutputSystem.

**Edit:** I recently tried a couple of things and found out some interesting but still unsuccessful results. First, I deleted all my addons (except the Blizzard ones) which, instead of crashing my X server on logging into the world, simply crashed the WoW program and gave me the normal "I crashed" debug screen I've seen in Windows. After that, I deleted the World of Warcraft directory and did a fresh install. This gave me the same result: Crashing the WoW program upon logging into the world.

Could you please post that debug msg?

---

### Post by montag451 on 2006-11-23
**On crashes.** To clarify, I can load WoW.exe with no problems. After logging into the server and selecting a character, I then press "Enter World." After everything finished loading, WoW crashes and I get a debug error. This is different from the old WoW install (installed under 0.9.6) which crashed my X server. (I was able to SSH in and restart X.) Now I just get a debug error where WoW seems to be trying to access null memory.

**On sound.** With the clean install, sound surprisingly works fine even though it's using the same Config.wtf file. Right now, my priority is getting WoW to work with no AddOns, then with AddOns, and then with AddOns and sound.

The text of the **debug report** follows:
```

==============================================================================
World of WarCraft (build 5875)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Nov 23, 2006  1:36:32.376 AM
User:     xxxx
Computer: xxxx
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7DE5E6ED

The instruction at "0x7DE5E6ED" referenced memory at "0x00000000".
The memory could not be "written".


WoWBuild: 5875
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000001  EBX=00000001  ECX=00000002  EDX=00000000  ESI=00000008
EDI=000024B0  EBP=0033F978  ESP=0033F960  EIP=7DE5E6ED  FLG=00210297
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

7DE5E6ED 0033F978 0000:00000000 <unknown>
7DE88AC5 0033F9B8 0000:00000000 <unknown>
7E7FF252 0033F9E8 0001:0002E252 c:\windows\system32\opengl32.dll
0059F130 0033FA00 0001:0019E130 C:\Program Files\World of Warcraft\WoW.exe
0059F62C 0033FA30 0001:0019E62C C:\Program Files\World of Warcraft\WoW.exe
0059F5C2 0033FA40 0001:0019E5C2 C:\Program Files\World of Warcraft\WoW.exe
00594C2F 0033FA6C 0001:00193C2F C:\Program Files\World of Warcraft\WoW.exe
0058ACF3 0033FA80 0001:00189CF3 C:\Program Files\World of Warcraft\WoW.exe
0058ACA8 0033FA9C 0001:00189CA8 C:\Program Files\World of Warcraft\WoW.exe
006B0023 0033FAC0 0001:002AF023 C:\Program Files\World of Warcraft\WoW.exe
006AF6D3 0033FAE0 0001:002AE6D3 C:\Program Files\World of Warcraft\WoW.exe
006C29AB 0033FB10 0001:002C19AB C:\Program Files\World of Warcraft\WoW.exe
006986EB 0033FB40 0001:002976EB C:\Program Files\World of Warcraft\WoW.exe
006983C7 0033FB5C 0001:002973C7 C:\Program Files\World of Warcraft\WoW.exe
0066FE92 0033FB78 0001:0026EE92 C:\Program Files\World of Warcraft\WoW.exe
0048329C 0033FC1C 0001:0008229C C:\Program Files\World of Warcraft\WoW.exe
00482E73 0033FCA8 0001:00081E73 C:\Program Files\World of Warcraft\WoW.exe
0076FC31 0033FCC4 0001:0036EC31 C:\Program Files\World of Warcraft\WoW.exe
007658E7 0033FCE8 0001:003648E7 C:\Program Files\World of Warcraft\WoW.exe
0076434C 0033FCF4 0001:0036334C C:\Program Files\World of Warcraft\WoW.exe
0044264E 0033FDBC 0001:0004164E C:\Program Files\World of Warcraft\WoW.exe
004246B0 0033FDF0 0001:000236B0 C:\Program Files\World of Warcraft\WoW.exe
0042106F 0033FE60 0001:0002006F C:\Program Files\World of Warcraft\WoW.exe
00420BF1 0033FE78 0001:0001FBF1 C:\Program Files\World of Warcraft\WoW.exe
0040411E 0033FF08 0001:0000311E C:\Program Files\World of Warcraft\WoW.exe
7B86C6BF 0033FFE8 0001:0004B6BF c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

****  Couldn't load DBGHELP.DLL, error: 193


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 7DE5E6ED)

7DE5E6ED: C7 02 01 00  00 00 83 C4  0C 5B 5E 5F  5D C3 31 DB  .........[^_].1.


Stack: 1024 bytes starting at (ESP = 0033F960)

* = addr  **                                                  *               
0033F960: B0 24 00 00  E1 0D 00 00  B0 04 00 00  B0 24 00 00  .$...........$..
0033F970: C0 53 27 7E  00 00 00 00  B8 F9 33 00  C5 8A E8 7D  .S'~......3....}
0033F980: C0 53 27 7E  60 D2 10 7C  B0 24 00 00  00 00 00 00  .S'~`..|.$......
0033F990: B0 24 00 00  C0 53 27 7E  60 D2 10 7C  00 00 00 00  .$...S'~`..|....
0033F9A0: 80 80 30 61  01 00 00 00  E1 0D 00 00  40 26 82 7E  ..0a........@&.~
0033F9B0: B0 24 00 00  E1 0D 00 00  E8 F9 33 00  52 F2 7F 7E  .$........3.R..~
0033F9C0: E1 0D 00 00  B0 24 00 00  40 D0 33 7E  40 26 82 7E  .....$..@.3~@&.~
0033F9D0: 00 FA 33 00  B7 2C 80 7E  40 00 00 00  40 00 00 00  ..3..,.~@...@...
0033F9E0: 08 00 1D 01  88 C9 61 13  00 FA 33 00  30 F1 59 00  ......a...3.0.Y.
0033F9F0: E1 0D 00 00  B0 24 00 00  40 00 00 00  88 C9 61 13  .....$..@.....a.
0033FA00: 30 FA 33 00  2C F6 59 00  88 C9 61 13  FF FF FF FF  0.3.,.Y...a.....
0033FA10: 00 00 00 00  00 00 00 00  88 C9 61 13  00 00 00 00  ..........a.....
0033FA20: 01 02 00 00  64 FA 33 00  E1 0D 00 00  08 00 1D 01  ....d.3.........
0033FA30: 40 FA 33 00  C2 F5 59 00  40 00 00 00  FF FF FF FF  @.3...Y.@.......
0033FA40: 6C FA 33 00  2F 4C 59 00  88 C9 61 13  40 00 00 00  l.3./LY...a.@...
0033FA50: 88 CF 5A 13  40 00 00 00  00 00 00 00  00 00 00 00  ..Z.@...........
0033FA60: 40 00 00 00  40 00 00 00  08 00 1D 01  80 FA 33 00  @...@.........3.
0033FA70: F3 AC 58 00  00 00 00 00  8C FA 33 00  01 00 00 00  ..X.......3.....
0033FA80: 9C FA 33 00  A8 AC 58 00  01 00 00 00  00 00 00 00  ..3...X.........
0033FA90: 00 00 00 00  40 00 00 00  40 00 00 00  C0 FA 33 00  ....@...@.....3.
0033FAA0: 23 00 6B 00  00 00 00 00  40 00 00 00  40 00 00 00  #.k.....@...@...
0033FAB0: 01 00 00 00  01 00 00 00  88 81 23 10  FF 51 93 0C  ..........#..Q..
0033FAC0: E0 FA 33 00  D3 F6 6A 00  A8 5A C0 0B  FF 51 93 0C  ..3...j..Z...Q..
0033FAD0: 6B 54 93 0C  88 81 23 10  A8 5A C0 0B  6A 00 00 00  kT....#..Z..j...
0033FAE0: 10 FB 33 00  AB 29 6C 00  A8 5A C0 0B  01 00 00 00  ..3..)l..Z......
0033FAF0: 0A 00 00 00  A8 5A C0 0B  1C 03 00 00  A0 06 00 00  .....Z..........
0033FB00: 0A 00 00 00  04 EB 38 10  01 00 00 00  7B 69 00 00  ......8.....{i..
0033FB10: 40 FB 33 00  EB 86 69 00  06 00 00 00  00 00 00 00  @.3...i.........
0033FB20: 01 00 00 00  00 00 00 00  7B 69 00 00  00 03 00 00  ........{i......
0033FB30: CA 01 00 00  06 00 00 00  60 00 00 00  C6 00 00 00  ........`.......
0033FB40: 5C FB 33 00  C7 83 69 00  C9 01 00 00  00 FC 33 00  \.3...i.......3.
0033FB50: 00 00 00 00  FE 00 00 00  00 C0 3F 44  78 FB 33 00  ..........?Dx.3.
0033FB60: 92 FE 66 00  08 80 B4 09  08 80 1F 07  08 80 B4 09  ..f.............
0033FB70: 00 FC 33 00  90 FB 33 00  1C FC 33 00  9C 32 48 00  ..3...3...3..2H.
0033FB80: C3 F5 C8 BF  24 1E 22 07  08 80 1F 07  08 F4 58 09  ....$.".......X.
0033FB90: E0 37 19 46  EC 66 6E 44  C1 F7 A3 44  28 00 25 07  .7.F.fnD...D(.%.
0033FBA0: B4 FB 33 00  56 A8 6F 00  C8 FD 58 05  28 00 25 07  ..3.V.o...X.(.%.
0033FBB0: 88 FD 58 05  D4 FB 33 00  69 7F 6F 00  96 F1 16 40  ..X...3.i.o....@
0033FBC0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FBD0: 89 82 71 40  00 00 00 00  00 00 00 00  BB 48 19 46  ..q@.........H.F
0033FBE0: 8D C8 6E 44  49 99 A3 44  BB 48 19 46  8D C8 6E 44  ..nDI..D.H.F..nD
0033FBF0: 49 99 A3 44  BB 48 19 46  8D C8 6E 44  52 0D A4 44  I..D.H.F..nDR..D
0033FC00: 2C 34 19 46  77 51 6E 44  50 FD A3 44  00 00 00 00  ,4.FwQnDP..D....
0033FC10: DA CE F7 3D  01 00 00 00  00 00 00 00  A8 FC 33 00  ...=..........3.
0033FC20: 73 2E 48 00  00 00 00 00  00 00 80 3F  00 00 00 00  s.H........?....
0033FC30: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 80 3F  ...............?
0033FC40: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FC50: 00 00 80 3F  00 00 00 00  6B 16 D9 BE  03 AE 87 BE  ...?....k.......
0033FC60: 00 00 00 00  00 00 80 3F  96 F1 16 40  00 00 00 00  .......?...@....
0033FC70: 00 00 00 00  00 00 00 00  00 00 00 00  89 82 71 40  ..............q@
0033FC80: 00 00 00 00  00 00 00 00  00 00 00 80  00 00 00 80  ................
0033FC90: 6F 12 03 BB  00 00 00 00  00 00 00 80  00 00 00 80  o...............
0033FCA0: 00 00 00 80  00 00 80 3F  C4 FC 33 00  31 FC 76 00  .......?..3.1.v.
0033FCB0: 00 00 00 00  08 1E 22 07  24 1E 22 07  24 1E 22 07  ......".$.".$.".
0033FCC0: E8 FC 33 00  E8 FC 33 00  E7 58 76 00  88 CA DB 02  ..3...3..Xv.....
0033FCD0: 08 60 20 07  08 99 45 07  00 00 00 00  C8 9E 45 07  .` ...E.......E.
0033FCE0: 09 00 00 00  DC 6C 20 07  F4 FC 33 00  4C 43 76 00  .....l ...3.LCv.
0033FCF0: 20 99 45 07  BC FD 33 00  4E 26 44 00  20 99 45 07   .E...3.N&D. .E.
0033FD00: DA CE F7 3D  D0 FD 33 00  88 6D 1D 01  88 6D 1D 01  ...=..3..m...m..
0033FD10: 48 29 58 05  70 FD 33 00  B7 47 35 00  06 00 00 00  H)X.p.3..G5.....
0033FD20: DC 00 00 00  00 00 00 00  AC 45 58 05  06 00 00 00  .........EX.....
0033FD30: AC 45 58 05  22 56 00 00  74 14 00 00  0B 00 00 00  .EX."V..t.......
0033FD40: 58 FD 33 00  80 E5 A3 44  FE B0 19 46  C0 A6 4C 41  X.3....D...F..LA
0033FD50: 00 48 9F BF  00 86 D0 41  7B 7D E8 41  7B 7D E8 41  .H.....A{}.A{}.A


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   2
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3592

Percent memory used:    32
Total physical memory:  2122256384
Free Memory:            1423826944
Page file:              2122256384
Total virtual memory:   2147352575

```

**Updated:** I tried running with SET gxApi "D3D". Instead of giving me a debug error, this crashed my X server upon loading the world.

---

### Post by montag451 on 2006-11-25
::Shameless bump.:: ++smart people.

---

### Post by Sammi on 2006-11-26
keep bumping

---

### Post by tparker on 2006-11-27
[justin whitaker:First: Blizzard is tinkering with the servers, logins, etc. the past day or so-they are beginning to preload the expansion. That's going to break some stuff.]

I don't expect that to be breaking too much, but I could be wrong. I am running the expansion beta under wine now having installed it the same as I did my live install. I only needed a work around for the updater (per the postings on the winhq Burning Crusade page) for it to play fine. One note, the expansion does seem to require the -opengl (ran from terminal as  wow.exe -opengl) to not have seriously messed up graphics under wine, so be prepared for that. I haven't checked sound in BC because I use teamspeak which breaks game sound anyway. :)

As to the original poster:

I installed WoW using the how to in this post:
[http://www.ubuntuforums.org/showthread.php?t=243336](http://www.ubuntuforums.org/showthread.php?t=243336)
which looks to be a different thread than the one mentioned in your first post, maybe it would have an idea or two to add to what you have already tried?

I am using wine 0.9.21 in Dapper with all suggested updates, nvidia graphics though so I'm no help with an ATI card, sorry.

---

