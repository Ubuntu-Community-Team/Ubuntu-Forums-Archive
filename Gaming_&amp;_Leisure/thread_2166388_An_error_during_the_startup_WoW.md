---
title: "An error during the startup WoW"
date: 2013-08-09
forum: Gaming &amp; Leisure
---

### Post by Valanth on 2013-08-09
Hello, like in the title I have a problem with starting WoW on Ubuntu. I'm beginner in Ubuntu, so I'm not so good in this stuff. I tried some solutions, that I found on the internet, but non of them worked. Personally I think it is problem with graphic, but I can't be sure. I'm struggling with this issue for few days and I thought that maybe You could help me.

I have a notebook HP Pavilion dv6 6040ew,
graphic card: AMD Radeon HD 6490M (1GB DDR5),
ram: 4GB DDR3,
processor: Intel Core i5-2410M 2,3 GHz, 3 MB Cache,
there might be a problem with notebook itself, because it has 2 graphic cards, one that I mentioned before and the second one integrated (don't know if it's correct word). I changed settings in BIOS to prevent auto switching between them according to specific work that notebook is doing like running game or movie. Cars should switch between them only when laptop is on battery (in that case the worse card is up).

I installed Ubuntu 12.04 (Polish version), 64-bits and drivers for graphic card as system suggested, there were 4 different options and I tested them all, but without succes. Tried also install drivers from official AMD website, but it doesn't work either.

The WoW itself was copied from Windows, the game was installed there and I just moved the folder with it to Ubuntu. To startup the game I used Wine, tried to run WoW through terminal and using PlayOnLinux but the results are below:


```
wine /home/user/games/wow/wow.exe
```

[COLOR=#333333]or
[/COLOR]
```
wine /home/user/games/wow/wow.exe -opengl
```

In both cases the output was the same:
```
[INDENT][COLOR=#333333]archive Data/Cache/SoundCache-3.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-2.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-1.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-0.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-enUS.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13164.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13164.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13164.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13164.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13164.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13205.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13205.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13205.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13205.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13205.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13287.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13287.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13287.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13287.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13287.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13329.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13329.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13329.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13329.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13329.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13596.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13596.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13596.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13596.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13596.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/enUS/wow-update-enUS-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/wow-update-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/patch-enUS-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/patch-base-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/enUS/SoundCache-patch-enUS-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data/Cache/SoundCache-patch-13623.MPQ opened[/COLOR]
[COLOR=#333333]archive Data\art.MPQ opened[/COLOR]
[COLOR=#333333]archive Data\world.MPQ opened[/COLOR]
[COLOR=#333333]archive Data\sound.MPQ opened[/COLOR]
[COLOR=#333333]archive Data\enUS\locale-enUS.MPQ opened[/COLOR]
[COLOR=#333333]archive Data\enUS\speech-enUS.MPQ opened[/COLOR]
[COLOR=#333333]fixme:win:EnumDisplayDevicesW ((null),0,0x32ed40,0x00000000), stub![/COLOR]
[COLOR=#333333]X Error of failed request: BadRequest (invalid request code or no such operation)[/COLOR]
[COLOR=#333333]Major opcode of failed request: 154 (GLX)[/COLOR]
[COLOR=#333333]Minor opcode of failed request: 19 (X_GLXQueryServerString)[/COLOR]
Serial [COLOR=#333333]number of failed request: 244[/COLOR]
[COLOR=#333333]Current serial number in output stream: 244[/COLOR]
[/INDENT]

```
[COLOR=#333333]
I tried to search this[/COLOR]```
fixme:win:EnumDisplayDevicesW

```in web and it lead me to some sites, where people advise to install some libraries to 32-bits system and i did what I could but at some piont I just got lost.

Tried also 

```
[COLOR=#000000][FONT=Ubuntu Mono]glxinfo | grep rendering[/FONT][/COLOR]
```

and I saw something like this:

```
X Error of failed request:  BadRequest (invalid request code or no such operation)  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

Hope that You can help me.

---

### Post by Valanth on 2013-08-10
[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513)

This thread helped me, WoW is running without problems, but now I think that drivers aren't perfect, because graphic of unity is bad, as if there isn't any driver for graphic card, tried to run drivers suggested by system, but they seems to not work. Catalyst seems to detect different graphic card that I have, it detects HD 6700M and mine is HD 6490M.
[COLOR=#000000]
[/COLOR]Could someone help me with that?[COLOR=#000000]
[/COLOR]

---

### Post by CitadelUniversal on 2013-08-10
Have you looked at the WoW winehq page [http://appdb.winehq.org/objectManager.php?sClass=version&iId=23843&iTestingId=66127](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23843&iTestingId=66127) - it has some instructions on how to set the game going.

---

