---
title: "Windows Source engine games in ubuntu"
date: 2021-02-01
forum: Gaming &amp; Leisure
---

### Post by mineland on 2021-02-01
Hello, ive moved over to ubuntu in the past month and overall its going really well. Now, i wanted to play my old steam games i had backed up in windows, but trying them in wine will just make them either run really poorly or not running at all. The one im trying to use is an game i can no longer download for some reason, and it looked like it had linux support in its life, but i only have the .exe file and cant open it properly with wine. My question is: is there a way or a program that makes source engine games compiled for windows able to run on linux/ubuntu that isnt wine? or a program that decompiles the exe of the game and recompiles it for linux?



Thanks if anyone can help me
-mineland

---

### Post by QIII on 2021-02-01
If applications do not run under Wine, then they don't.  Wine is not a panacea.  Someone, somewhere, would have to do some work to make them run.  That's not anybody here.

There is no way to "de-compile" proprietary, closed-source code from an .exe and "recompile" it for Linux.  Applications have to be ported by those who develop them.

You could try installing Steam and see if your games will run natively.

---

### Post by mastablasta on 2021-02-02
or you can try and run them via SteamPlay (proton). Check protonDB to see if your game is supported, add you library to steam and run the game with proton.

source games usually have linux version (unless they are some multiplayer games that use some anticheat (e.g. Apex Legends).

sometimes all you need to do is move current binaries from another linux based game to your source game. for example Aperture tag is kind of standalone mod for Portal 2, but won't work, because their binaries are not compatible with Portal and other current libraries. but all you need to do is move the ones from Portal 2 to Aperture Tag folder and overwrite them. suddenly the game starts native in linux and all that.

similar with a few other games. sometime some extra command is needed to launch it from steam. 

i battled Crysis which is supposed to work ok, but didn't. moving binaries arround a bit and overwriting some folders (i believe it was 32 bit) made it work just fine.

---

