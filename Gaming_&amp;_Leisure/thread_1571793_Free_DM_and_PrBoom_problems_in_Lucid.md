---
title: "Free DM and PrBoom problems in Lucid"
date: 2010-09-10
forum: Gaming &amp; Leisure
---

### Post by chris1379 on 2010-09-10
I have a 700MHz PIII laptop that dual boots Ubuntu 10.04 and Windows XP. I can run Quake2, Half-life and most of the Doom ports in XP so I thought I'd give it a try in Ubuntu. I installed PrBoom with Freedoom from the repository but can't get it to run. When I launch it, the screen changes to what I think is 16 color mode and then PrBoom closes after a few seconds. Here is what's in the terminal:
```
:~$ freedm

prboom v2.5.0 (http://prboom.sourceforge.net/)
I_SetAffinityMask: manual affinity mask is 1
M_LoadDefaults: Load system defaults.
 default file: /home/chris/.prboom/prboom.cfg
 found /usr/share/games/freedoom/freedm.wad
IWAD found: /usr/share/games/freedoom/freedm.wad
PrBoom (built Nov  7 2009), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/freedoom/freedm.wad
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
I_ShutdownMusic: removing /tmp/prboom-music-QzkP37
I_ShutdownSound: 

```I tried to include a screenshot of the PrBoom window.
If it helps the video is a Neomagic NM2380 w/ 6MB RAM.

Thanks,
Chris

---

### Post by Flymo on 2010-10-23
Hello Chris,

Have almost the same problem running under Lucid UNE on an Acer 4315 (Celeron 540, intel X3100 graphics) except that 

1) I am using Freedoom from the repository with prboom v2.5.0
2) The graphics are fine, until it all stops.

....but the:

```
 I_SignalHandler: Exiting on signal: signal 8
```

.....is indeed identical

To expand a bit, when launching from GUI, the opening screen appears and hitting enter brings up the menu on that screen. Cursor keys will navigate the screen (with sound fx), you can open menu items and edit them, then the window closes, just like that.  Or you can watch and wait for it to close without any commands at all, which it does.

Launching from a terminal does the same, with a diagnostic list similar to yours (see below), and launching as Root makes no difference that I can see.<sigh>

Have tried varii differing launch options, with similar results.  

 -fullscreen  does what it says on the tin
 -nosound     ditto

Everything starts well, then folds up the window and goes home.

So it looks as though you may have two problems:

 1) The same as mine -  it will not run, and dies with Signal 8
 2) Something video related - looks like a mismatch in resolution to me?


Have had a look at these pages so far:

[http://forums.fedoraforum.org/showthread.php?t=236248](http://forums.fedoraforum.org/showthread.php?t=236248)
[http://translate.google.com.au/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=ru&tl=en&u=http%3A%2F%2Fwww.linux.org.ru%2Fforum%2Fgames%2F4860348&act=url](http://translate.google.com.au/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=ru&tl=en&u=http%3A%2F%2Fwww.linux.org.ru%2Fforum%2Fgames%2F4860348&act=url)

Yes, the last one is in Russian, via Goggle translation to English

They both imply that we need to rebuild from source..... <sigh>

Anyone with ideas on this?

Best regards, Ben

```
root@4315# freedoom

prboom v2.5.0 (http://prboom.sourceforge.net/)
I_SetAffinityMask: manual affinity mask is 1
M_LoadDefaults: Load system defaults.
 default file: /root/.prboom/prboom.cfg
 found /usr/share/games/doom/freedoom.wad
IWAD found: /usr/share/games/doom/freedoom.wad
PrBoom (built Nov  7 2009), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/freedoom.wad
 adding /usr/share/games/doom/prboom.wad
W_InitCache

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - 
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites Tranmap build [........]
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
I_ShutdownMusic: removing /tmp/prboom-music-CQasBw
I_ShutdownSound: 

...and back to the prompt
```

---

### Post by chris1379 on 2010-10-23
See this thread. [http://ubuntuforums.org/showthread.php?t=1411552](http://ubuntuforums.org/showthread.php?t=1411552) . I installed PrBoom from the Debian repos and it worked. Once I got it to work I solved the graphics issues. It was just a matter of using the correct resolution and color depth. I still like ZDoom better in Windows but I haven't quite figured it out in Ubuntu.

---

