---
title: "Dooms Day Problem"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by rathel on 2005-07-06
The installation of DoomsDay when okay, but I cannot play Doom. I get this error message:
```

rathel@ubuntu:~$ sh jdoom.sh
LoadPlugin: /usr/local/lib/libdpdehread
LoadPlugin: /usr/local/lib/libdpmapload
Con_Init: Initializing the console.
SW_Init: Startup message window opened.
Executable: Version 1.8.6 Jul  6 2005 (DGL).
Memory zone: 32.0 Mb.
Parsing configuration files.
W_Init: Init WADfiles.
W_AddFile: /home/rathel/doom/doom.wad
  IWAD identification: 00cdce4c
W_AddFile: Data/Doomsday.wad
W_AddFile: Data/jDoom/jDoom.wad
  IWAD identification: 00056533
Reading definition file: Defs/Doomsday.ded
Reading definition file: Defs/jDoom/jDoom.ded
  138 sprite names
  974 states
  140 things
    8 lights
  112 sound effects
   68 songs
  335 text strings
   27 particle generators
   22 animation groups
   49 surface decorations
   69 map infos
    6 finales
Sys_Init: Setting up machine state.
Sys_Init: Initializing keyboard, mouse and joystick.
Sys_InitTimer.
Sfx_Init: Initializing SDL_mixer...
DS_Load: Loading of libdssdlmixer failed.
Sfx_Init: Driver init failed. Sfx is disabled.
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```
I have the mixer and Sfx installed...
Here's what's in the sh script if that helps any:
```

#!/bin/sh
/usr/local/bin/doomsday -game jdoom -file ~/doom/doom.wad \ -userdir ~/doomsday/jdoom

```

---

### Post by Yagisan on 2005-07-07
G'day,

Would you like to try my Debian Doomsday packages instead ? You can find them here [http://eyagi.bpa.nu/~jamie/doomsday.html](http://eyagi.bpa.nu/~jamie/doomsday.html) (This is linked too from the doomsday wiki, and in the forums). Sometime within the next few weeks I'll redo the repository with seperate Ubuntu Hoary and Debian Sarge builds, when I finally get my development machine fixed.

If you have any problems after installing the packages just run ```
reportbug deng
``` and type a description, and I will try to help, or post a request in the doomsday forums for me.

Your current error looks like libdssdlmixer is missing. This is in libsdl-mixer1.2 package. 

Regards
Yagisan

(Current unofficial maintainer of the Doomsday Engine)

---

### Post by rathel on 2005-07-07
Okay I tried to install Deng Via APT-GET but I get this:
```

The following packages have unmet dependencies:
  deng: Depends: libsdl-mixer1.2 (>= 1.2.6) but 1.2.5-9 is to be installed
E: Broken packages

```
and then I apt-get'd libsdl-mixer1.2 and this:
```

libsdl-mixer1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Yagisan on 2005-07-09
OK. I see, Ubuntu forked before I made the packages. I'll update them in  a few days, check the website I gave to find an updated Ubuntu repository. It should be there by friday.

Thanks

---

### Post by rathel on 2005-07-09
Alright, Cool, Will check that out.

---

### Post by Yagisan on 2005-07-19
[QUOTE=Yagisan]OK. I see, Ubuntu forked before I made the packages. I'll update them in  a few days, check the website I gave to find an updated Ubuntu repository. It should be there by friday.

Thanks[/QUOTE]Took a bit longer then I planned (New upstream version yay! 1.9.0beta2) but I've begun building Ubuntu packages.

i386 built fine, amd64 segfaults, and I can't build powerpc until someone shows me how to get ubuntu installed under pearpc or qemu.

The packages are currently missing desktop files so they are not yet ready for distributon, but I thought I'd post an update anyway.

---

