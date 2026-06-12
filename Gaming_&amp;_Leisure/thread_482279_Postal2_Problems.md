---
title: "Postal2 Problems"
date: 2007-06-23
forum: Gaming &amp; Leisure
---

### Post by Salazar420 on 2007-06-23
> xenouser@XeNoCoMp:~/Desktop/Postal2-Linux/Postal2-Linux/postal2$ ./postal2
Postal 2
Copyright 2003 Running With Scissors, Inc.
Unreal Engine
Copyright 2001 Epic Games, Inc.
open /dev/[sound/]dsp: Device or resource busy
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error
xenouser@XeNoCoMp:~/Desktop/Postal2-Linux/Postal2-Linux/postal2$

Therein is the results of, obviously, myself trying to run Postal2. It's very frustrating because, although I'm running a feeble Radeon 9250 (or 9200 SE), I know it's capable of playing this game. Other games that I've managed to run fail because apparently the drivers are out of date. Watch what happens when I try to install the Graphic Card specific ati drivers.

> xenouser@XeNoCoMp:~/Desktop$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8............................................ .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .........................
-e ==================================================
-e ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
xenouser@XeNoCoMp:~/Desktop$

Please help! I'm a complete newbie to linux and I'm desperate for some answers.

---

### Post by Salazar420 on 2007-06-23
Eh...

---

### Post by bengringo on 2007-06-30
In order to get this to run you cant have XGL running nor Compiz or anything like that. It must be a regular install of gnome or kde running the game. XGL just isn't compatible. try running it with a fail safe terminal and see if you get further

---

### Post by Salazar420 on 2007-07-11
Thanks. Will try.

---

