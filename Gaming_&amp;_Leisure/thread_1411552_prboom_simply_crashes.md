---
title: "prboom simply crashes"
date: 2010-02-20
forum: Gaming &amp; Leisure
---

### Post by argos3016 on 2010-02-20
thats the terminal output:
blablabla@blablabla:~$ prboom

prboom v2.5.0 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
I_SetAffinityMask: manual affinity mask is 1
M_LoadDefaults: Load system defaults.
 default file: /home/blablabla/.prboom/prboom.cfg
 found /usr/share/games/doom/doom2.wad
IWAD found: /usr/share/games/doom/doom2.wad
PrBoom (built Jun 23 2009), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/doom2.wad
 adding /usr/share/games/doom/prboom.wad
W_InitCache

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - 
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites 
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables R_InitPatches 
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSound:  configured audio device with 1024 samples/slice
I_InitSound: sound module ready
S_Init: Setting up sound.
S_Init: default sfx volume 8
HU_Init: Setting up heads up display.
I_InitGraphics: 640x480
I_UpdateVideoMode: 640x480 (nofullscreen)
V_InitMode: using 8 bit video mode
I_SetRes: Using resolution 640x480
I_UpdateVideoMode: 0x60000000, SDL buffer, direct access
ST_Init: Init status bar.
G_DoPlayDemo: playing demo with boom v2.02 compatibility
P_GetNodesVersion: using normal BSP nodes
I_SignalHandler: Exiting on signal: signal 8
I_ShutdownMusic: removing /tmp/prboom-music-p3YzlX
I_ShutdownSound:

---

### Post by nzuri on 2010-03-10
exactly the same problem

---

### Post by The Spy on 2010-07-19
What architecture are you guys using. I'm running Prboom 2.5.0 on my 64-bit Arch machine, and it runs fine, but I have a couple of i386 machines with the same distro that wont run it. It's the same version of Prboom.

I can get it to run if I start the game with:
```
prboom -nosound -iwad /wad/location/
```
But of course I have no sound.

---

### Post by CoercibleGerm on 2010-08-10
This appears to be documented as a bug (see [here]("https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498")).

Evidently, the build is bad. I tried installing the debian build (found at [http://packages.debian.org/sid/i386/prboom/download]("http://packages.debian.org/sid/i386/prboom/download")) and it now works for me, complete with sound.

---

