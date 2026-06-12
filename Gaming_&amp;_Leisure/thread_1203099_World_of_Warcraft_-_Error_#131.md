---
title: "World of Warcraft - Error #131"
date: 2009-07-02
forum: Gaming &amp; Leisure
---

### Post by Marblemouth on 2009-07-02
Please help me!!! I've been having some serious trouble installing and playing World of Warcraft.  I've spent numerous hours reading forum threads all over the internet on how to install and configure the various applications needed to play WOW.  I am running Hardy Heron (8.04) on an older Compaq Presario (SR1115C).  I no longer have Windows XP installed on this computer.  Please tell me whatever information you need to help.  This is how I installed the game - I downloaded the original game from the blizzard web site then took files from my wife's copy off of her laptop and replaced the patch files on my computer.  This had worked in the past when my wife had to reinstall the game on her computer, thought it might work this time also.  The most current problem I am having is when I attempt to play the game.  The Blizzard launcher comes up and I hit play.... then I get this:

World of WarCraft (build 7561)

Exe:      C:\Program Files\World of Warcraft\WoW.exe
Time:     Jul  2, 2009  8:08:29.609 PM
User:     marblemouth
Computer: marblemouth-des
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #131 (0x85100083) File Corrupt
Program:    C:\Program Files\World of Warcraft\WoW.exe
File:    .\Client.cpp
Line:    2627

Signature string (2) in signaturefile file does not match game's signature version (2).


WoWBuild: 7561
------------------------------------------------------------------------------

----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 1/1 threads...

--- Thread ID: 67 [Current Thread] ---
00645D30 0033F8AC 0001:00244D30 C:\Program Files\World of Warcraft\WoW.exe
00645D54 0033F8C0 0001:00244D54 C:\Program Files\World of Warcraft\WoW.exe
0040230C 0033F984 0001:0000130C C:\Program Files\World of Warcraft\WoW.exe
00405251 0033FBF4 0001:00004251 C:\Program Files\World of Warcraft\WoW.exe
00405BB9 0033FE5C 0001:00004BB9 C:\Program Files\World of Warcraft\WoW.exe
00405FB6 0033FE6C 0001:00004FB6 C:\Program Files\World of Warcraft\WoW.exe
00406008 0033FF08 0001:00005008 C:\Program Files\World of Warcraft\WoW.exe
7B877199 0033FFE8 0001:00056199 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 1/1 threads...

--- Thread ID: 67 [Current Thread] ---
00645D30 WoW.exe      <unknown symbol>+0 (0x85100083,0x0033F900,0x0033F8D0,0x0033F984)
00645D54 WoW.exe      <unknown symbol>+0 (0x85100083,0x0033F900,0x012B4E88,0x00000000)
0040230C WoW.exe      <unknown symbol>+0 (0x012B45E8,0x012B4E88,0x00000A28,0x012E4808)
00405251 WoW.exe      <unknown symbol>+0 (0x00000A28,0x00000002,0x00000001,0x0033FD40)
00405BB9 WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x00406008)
00405FB6 WoW.exe      <unknown symbol>+0 (0x00409B99,0x00400000,0x00000000,0x0011499C)
00406008 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B877199 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x00E65000  C:\Program Files\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  C:\Program Files\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B950000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCAD000  C:\windows\system32\ntdll.dll
0x7D600000 - 0x7D60C000  C:\windows\system32\psapi.dll
0x7D610000 - 0x7D659000  C:\windows\system32\dbghelp.dll
0x7D680000 - 0x7D6B0000  C:\windows\system32\uxtheme.dll
0x7E010000 - 0x7E01F000  C:\windows\system32\midimap.dll
0x7E020000 - 0x7E036000  C:\windows\system32\msacm32.drv
0x7E110000 - 0x7E13C000  C:\windows\system32\winealsa.drv
0x7E170000 - 0x7E1F4000  C:\windows\system32\winex11.drv
0x7E2F0000 - 0x7E2FB000  C:\windows\system32\lz32.dll
0x7E300000 - 0x7E314000  C:\windows\system32\version.dll
0x7E320000 - 0x7E37F000  C:\windows\system32\rpcrt4.dll
0x7E3A0000 - 0x7E475000  C:\windows\system32\ole32.dll
0x7E480000 - 0x7E4A2000  C:\windows\system32\ws2_32.dll
0x7E4B0000 - 0x7E4C7000  C:\windows\system32\msacm32.dll
0x7E4D0000 - 0x7E58A000  C:\windows\system32\comctl32.dll
0x7E5A0000 - 0x7E714000  C:\windows\system32\shell32.dll
0x7E720000 - 0x7E76F000  C:\windows\system32\shlwapi.dll
0x7E780000 - 0x7E791000  C:\windows\system32\mpr.dll
0x7E7B0000 - 0x7E7F8000  C:\windows\system32\wininet.dll
0x7E800000 - 0x7E817000  C:\windows\system32\imm32.dll
0x7E830000 - 0x7E934000  C:\windows\system32\wined3d.dll
0x7E940000 - 0x7E965000  C:\windows\system32\d3d9.dll
0x7EB20000 - 0x7EBA4000  C:\windows\system32\opengl32.dll
0x7EBB0000 - 0x7EBF9000  C:\windows\system32\advapi32.dll
0x7EC10000 - 0x7EC98000  C:\windows\system32\gdi32.dll
0x7ECB0000 - 0x7EDDE000  C:\windows\system32\user32.dll
0x7EDF0000 - 0x7EE73000  C:\windows\system32\winmm.dll


----------------------------------------
    Memory Dump
----------------------------------------

Stack: 1024 bytes starting at (ESP = 0033E2B4)

* = addr               **                                         *           
0033E2B0: B4 E2 33 00  BC 20 00 00  00 00 00 00  6C 44 65 00  ..3.. ......lDe.
0033E2C0: B4 E2 33 00  C8 E2 33 00  64 F0 33 00  72 48 64 00  ..3...3.d.3.rHd.
0033E2D0: 01 00 6E 00  10 45 64 00  BC 20 00 00  03 00 00 00  ..n..Ed.. ......
0033E2E0: 00 00 00 00  F4 55 64 00  1C 8F 86 00  02 00 00 00  .....Ud.........
0033E2F0: 43 0A 00 00  D9 07 07 00  04 00 02 00  14 00 08 00  C...............
0033E300: 1D 00 61 02  00 38 2D 01  84 F0 33 00  1C 8F 86 00  ..a..8-...3.....
0033E310: 00 00 00 00  B0 AB 8A 00  20 00 00 00  00 A1 5F 46  ........ ....._F
0033E320: 1F FB C9 01  00 CB 01 8D  20 FB C9 01  00 A1 5F 46  ........ ....._F
0033E330: 1F FB C9 01  00 00 00 00  00 7A 7B 00  00 00 00 00  .........z{.....
0033E340: 00 00 00 00  57 6F 57 2E  65 78 65 00  00 00 00 00  ....WoW.exe.....
0033E350: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E360: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E370: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E380: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E390: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3A0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3B0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3C0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3D0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3E0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E3F0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E400: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E410: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E420: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E430: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E440: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033E450: 00 00 00 00  00 00 00 00  13 00 00 00  00 00 00 00  ................
0033E460: 00 00 00 00  08 30 2D 01  8D FE 63 00  00 10 00 00  .....0-...c.....
0033E470: 00 A0 00 00  00 10 00 00  A0 A0 C9 7B  8C E4 33 00  ...........{..3.
0033E480: 00 10 A0 01  00 A0 00 00  51 07 00 00  00 00 00 00  ........Q.......
0033E490: 00 00 00 00  6C 31 D2 00  00 10 00 00  88 02 A2 01  ....l1..........
0033E4A0: 91 4D C3 7B  91 7D C6 B7  5B 9C 63 00  0C 4D D2 00  .M.{.}..[.c..M..
0033E4B0: 91 4D C3 7B  F8 47 8B 7B  00 30 2D 01  9C E5 33 00  .M.{.G.{.0-...3.
0033E4C0: AF BE 89 7B  EC E4 33 00  00 00 00 00  1C E6 33 00  ...{..3.......3.
0033E4D0: 0F 1A 64 00  91 7D C6 B7  00 00 00 00  08 5C 2B 01  ..d..}.......\+.
0033E4E0: F8 FE 33 00  E0 BD 89 7B  00 00 A0 01  F8 47 8B 7B  ..3....{.....G.{
0033E4F0: 00 30 2D 01  40 2D D2 00  9C E5 33 00  FE 89 C9 73  .0-.@-....3....s
0033E500: 09 5F 7D 07  00 00 00 00  28 E5 33 00  5C 02 A2 01  ._}.....(.3.\...
0033E510: F8 FE 33 00  48 77 0E 00  14 00 11 00  C8 88 13 00  ..3.Hw..........
0033E520: E0 88 13 00  00 00 11 00  48 14 C9 7B  B8 88 13 00  ........H..{....
0033E530: 28 00 00 00  84 E5 33 00  C6 3C C4 7B  37 C1 89 7B  (.....3..<.{7..{
0033E540: FF FF FF FF  64 E5 33 00  E5 1F C4 7B  00 40 00 00  ....d.3....{.@..
0033E550: 3F 47 C3 7B  00 30 2C 01  54 68 69 73  20 61 70 70  ?G.{.0,.This app
0033E560: 6C 69 63 61  74 69 6F 6E  20 68 61 73  20 65 6E 63  lication has enc
0033E570: 6F 75 6E 74  65 72 65 64  20 61 20 63  72 69 74 69  ountered a criti
0033E580: 63 61 6C 20  65 72 72 6F  72 3A 0A 0A  45 52 52 4F  cal error:..ERRO
0033E590: 52 20 23 31  33 31 20 28  30 78 38 35  31 30 30 30  R #131 (0x851000
0033E5A0: 38 33 29 20  46 69 6C 65  20 43 6F 72  72 75 70 74  83) File Corrupt
0033E5B0: 0A 50 72 6F  67 72 61 6D  3A 09 43 3A  5C 50 72 6F  .Program:.C:\Pro
0033E5C0: 67 72 61 6D  20 46 69 6C  65 73 5C 57  6F 72 6C 64  gram Files\World
0033E5D0: 20 6F 66 20  57 61 72 63  72 61 66 74  5C 57 6F 57   of Warcraft\WoW
0033E5E0: 2E 65 78 65  0A 46 69 6C  65 3A 09 2E  5C 43 6C 69  .exe.File:..\Cli
0033E5F0: 65 6E 74 2E  63 70 70 0A  4C 69 6E 65  3A 09 32 36  ent.cpp.Line:.26
0033E600: 32 37 0A 0A  53 69 67 6E  61 74 75 72  65 20 73 74  27..Signature st
0033E610: 72 69 6E 67  20 28 32 29  20 69 6E 20  73 69 67 6E  ring (2) in sign
0033E620: 61 74 75 72  65 66 69 6C  65 20 66 69  6C 65 20 64  aturefile file d
0033E630: 6F 65 73 20  6E 6F 74 20  6D 61 74 63  68 20 67 61  oes not match ga
0033E640: 6D 65 27 73  20 73 69 67  6E 61 74 75  72 65 20 76  me's signature v
0033E650: 65 72 73 69  6F 6E 20 28  32 29 2E 0A  0A 00 00 00  ersion (2)......
0033E660: 4D 50 51 1A  2C 00 00 00  51 E0 5D 0E  01 00 03 00  MPQ.,...Q.].....
0033E670: 51 02 5D 0E  51 82 5D 0E  00 08 00 00  E0 05 00 00  Q.].Q.].........
0033E680: 00 00 00 00  00 00 00 00  00 00 00 00  8C 01 00 00  ................
0033E690: F7 09 00 00  20 16 00 00  72 23 00 00  06 32 00 00  .... ...r#...2..
0033E6A0: FB 40 00 00  59 50 00 00  E7 5F 00 00  09 6F 00 00  .@..YP..._...o..
0033E6B0: 91 7E 00 00  16 8E 00 00  8F 9D 00 00  F4 AC 00 00  .~..............


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     2560
Os Version:             5.1
Os Service Pack:        2.0

Percent memory used:    35
Total physical memory:  1592881152
Free Memory:            1024892928
Page file:              1961607168
Total virtual memory:   2147352575


####################
UPDATE 
####################
Found this in a Wine thread a few minutes ago... 
This worked...kind of... now I have different problems...lol
I can now launch and log into the game but without sound and my video flashes between the game and my desktop.  

                                  **Re: Howto: WOW with Wine (help.ubuntu.com/community/WorldofWarcraft)**             
                                                                [SIZE=3]**Version Mismatch Error Fix**[/SIZE]

For this error
     Code:
     WoW
This application has encountered a critical error:
ERROR #121  (0x85100079) Version Mismatch
Program: C:\Program Files\World of Warcraft\WoW.exe
DBFilesClient\Startup_Strings.dbc has wrong number of colums (found 19, expected 11)

Press OK to terminate the application.
OK 
Look in your World of Warcraft directory, and if you have both
WoW.exe
and
Wow.exe (notice the lower case "w")

backup 
WoW.exe (perhaps just renaming it WoWbackup.exe)
and rename 
Wow.exe to WoW.exe

At this point I *think* one of the following renames WoW.exe to Wow.exe 
A) the Blizzard Full Client Downloader program 
B) the file repair tool 
C) the Wrath of the Lich King expansion itself

And if you've copied files from another directory (such as a Windows directory after failing miserably to get the Full Client Downloader to run properly in Wine, or copied files from an already updated machine to save time, etc) you will end up with BOTH similarily named executable files. Launcher.exe points to the dud, until you rename your files as outlined above.

-zami
                                                                                                                                    *                                              Last edited by zami; April 16th, 2009 at 09:09 PM..                                                                   Reason: correcting info (detailed over next few posts)                                      *             

####################
UPDATE 
####################
Fixed the sound issue... looks like it was a pretty common issue for the 8.04 Hardy release.  I also fixed the flickering screen .  I found out it was caused by a conflict (?) with the in game mini-map.  I downloaded and added the add on; "ApplyToForehead - 4".  

Thank you in advance for any help you can offer and please let me know what other information you might need to help me solve this problem.

---

