---
title: "Game won't launch: Ubuntu 14.04 Trusty Thar (Steam)"
date: 2015-12-14
forum: Gaming &amp; Leisure
---

### Post by michigogo on 2015-12-14
Hello all and first, thank you for taking your time to read and help me.

I recently upgraded my old ubuntu 12.04 to ubuntu 14.04. I re-installed steam and installed a game that worked on ubuntu 12.04 (Mount and Blade warband). However the game never loads when I click on "Play". I decided to go through the terminal to see if I had an error message. This is what I got:

```
Installing breakpad exception handler for appid(steam)/version(1449778863)assert_20151214181024_19.dmp[4676]: Uploading dump (out-of-process)
/tmp/dumps/assert_20151214181024_19.dmp
Game update: AppID 48700 "Mount & Blade: Warband", ProcID 4677, IP 0.0.0.0:0
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
Generating new string page texture 128: 256x256, total string texture memory is 1,47 MB
Setting breakpad minidump AppID = 48700
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198054674323 [API loaded no]
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Segmentation fault (core dumped)
Game removed: AppID 48700 "Mount & Blade: Warband", ProcID 4679 
assert_20151214181024_19.dmp[4676]: Finished uploading minidump (out-of-process): success = yes
assert_20151214181024_19.dmp[4676]: response: CrashID=bp-21a2c07e-1f5f-4875-b092-179bc2151214
assert_20151214181024_19.dmp[4676]: file ''/tmp/dumps/assert_20151214181024_19.dmp'', upload yes: ''CrashID=bp-21a2c07e-1f5f-4875-b092-179bc2151214''



```

I haven't found anything on Google, so here I am. 
Please help :(
Cheers!

---

### Post by michigogo on 2015-12-14
Update: I installed another Linux game and this one worked fine. So now I'm wondering why this one isn't working. **It does say it supports linux.**

---

### Post by efflandt on 2015-12-15
Did you upgrade 12.04 to 14.04 or fresh install 14.04? I don't have that game, but if it worked for you in 12.04 it should work in 14.04. It appears to have relatively low computer requirements for Linux. What graphics card/chip do you have and are you using default or added drivers (version?).

Just in case that game is missing any files, the first thing you should try is right clicking on the game in Steam Library, go to Properties > LOCAL FILES and click on VERIFY INTEGRITY OF GAME CACHE... That should check all of the game files and download any that are corrupt or missing.

---

### Post by michigogo on 2015-12-15
Hey, (and thank you),

-I'm not sure about what you mean by "fresh install", but I deleted everything on my pc and installed ubuntu 14.04. (I used to dual boot windows 7, but I decided I didn't need it anymore).

- Here are my computer's specs:

Memory: 3.8 GiB
Processor: Intel® Core&#8482; i5-2410M CPU @ 2.30GHz × 4
Graphic: NVS 4200M/PCIe/SSE2
64 bits

I'm not sure about which driver I'm using, but it seems to be: 
[B]NVIDIA Binary Driver, version 352.63

[/B]Also, I have verified the game cache and it says every is good.

Hope it can help,
Cheers!

---

### Post by oldrocker99 on 2015-12-17
A "fresh install" is when you wipe the drive and install a new version, which you did. You have the latest nVidia driver, too. 

Are you running a 32-bit version? Many Steam games are 64-bit. 64-bit systems can, with proper 32-bit libraries, run 32-bit programs, but 32-bit systems **cannot** run 64-bit programs.

---

### Post by oldrocker99 on 2015-12-17
A "fresh install" is when you wipe the drive and install a new version, which you did. You have the latest nVidia driver, too. 

Are you running a 32-bit version? Many Steam games are 64-bit. 64-bit systems can, with proper 32-bit libraries, run 32-bit programs, but 32-bit systems **cannot** run 64-bit programs.

---

### Post by ltidwell0689 on 2015-12-17
> **michigogo said:**
> Hello all and first, thank you for taking your time to read and help me.

I recently upgraded my old ubuntu 12.04 to ubuntu 14.04. I re-installed steam and installed a game that worked on ubuntu 12.04 (Mount and Blade warband). However the game never loads when I click on "Play". I decided to go through the terminal to see if I had an error message. This is what I got:

```
Installing breakpad exception handler for appid(steam)/version(1449778863)assert_20151214181024_19.dmp[4676]: Uploading dump (out-of-process)
/tmp/dumps/assert_20151214181024_19.dmp
Game update: AppID 48700 "Mount & Blade: Warband", ProcID 4677, IP 0.0.0.0:0
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
Generating new string page texture 128: 256x256, total string texture memory is 1,47 MB
Setting breakpad minidump AppID = 48700
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198054674323 [API loaded no]
ERROR: ld.so: object '/home/arthur/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Segmentation fault (core dumped)
Game removed: AppID 48700 "Mount & Blade: Warband", ProcID 4679 
assert_20151214181024_19.dmp[4676]: Finished uploading minidump (out-of-process): success = yes
assert_20151214181024_19.dmp[4676]: response: CrashID=bp-21a2c07e-1f5f-4875-b092-179bc2151214
assert_20151214181024_19.dmp[4676]: file ''/tmp/dumps/assert_20151214181024_19.dmp'', upload yes: ''CrashID=bp-21a2c07e-1f5f-4875-b092-179bc2151214''



```

I haven't found anything on Google, so here I am. 
Please help :(
Cheers!

Have you tried using play on Linux? I know it's not a fix, but it will work until the problem is resolved.

---

