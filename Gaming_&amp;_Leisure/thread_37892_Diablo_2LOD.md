---
title: "Diablo 2:LOD"
date: 2005-05-29
forum: Gaming &amp; Leisure
---

### Post by DarkKnight on 2005-05-29
Heyo peeps. 

I'm trying to install Diablo 2 LOd (And Never winter nights, but thats another issue >_>) but I keep getting a DirectDraw error and this: 

```
stevie@Steel:/usr/games/d2$ wine Game_crack.exe
Please use the registry key HKEY_CURRENT_CONFIG\Software\Fonts\LogPixels
to set the screen resolution and remove the "Resolution" entry in the config file
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c92f78)->(00010022,00000011)
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c92f78)->(00010022,00000011)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
Wine exited with a successful status

```

I've googled it and tried some of the answers there but no luck... 

Any idea's?  :)

Edit: oopsie... I just found my problem and have it running in a window... :oops: 

Can anyone tell me how to run it full screen though? 
(And for future reference, put a semicolon before "Resolution" under [Fonts] in the config file and un-comment Desktop="640x480")

---

### Post by DarkKnight on 2005-05-30
Does anyone have the same problem of not being able to run games full screen? 

This is what I get when trying to run Diablo2: 
```
stevie@Steel:/usr/games/d2$ wine Game_crack.exe
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c91c48)->(00010022,00000011)
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c91c48)->(00010022,00000011)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
Wine exited with a successful status

```

Any help would be very welcome, I want to get these games working so I can dump windows asap.
(I'll be testing a starcraft laters to see if this is just a diablo2 problem or if it's a directdraw problem.)

---

### Post by DarkKnight on 2005-06-02
Picture this if you will;

I'm playing D2 after getting the CD drive working then the res switching, I've never used the sound so I'm not bothered that it's not working. So here I am listening to my music when all of a sudden, Diablo2 chrashes JUST as I try to go to the next act...

In vain, I tell my self it's a one off, I'll fire it back up and she'll be right... or not. When I start it back up I make sure to save before I try going to the next act, and it's a good thing too, I can't get to act 2!

So here I am more then likely talking to my self hoping any of you have a working wine (apt-get install wine, not winex or compiled) installed version of Diablo 2 LOD. 

I think the problem is the NO-CD crack I have... when I tried to use a different one, I got a DirectDraw error but the rest did the same... the problem is I can't use my CD since D2 can't find it. At first I thought it was the movies, but when I go and play the movies in cinematics, they play just fine (with no sound, but meh).

This is whats being spat out by wine: 

```
stevie@Steel:~$ wine /usr/games/Diablo\ II/Game_crack.exe
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: x11drv: X11DRV_DDHAL_CreatePalette stub
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:wave: DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave: DSDB_MapBuffer Use: "HardwareAcceleration" = "Emulation" in the [dsound] section of your config file.
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c933b8)->(003d0038,00000011)
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:winmm:MMDRV_Exit Closing while ll-driver open
Wine failed with return code 5
```

Google returned very little results and I've seen some other peeps with working 1.10 installs else where... Help anyone? :)

(Incase anyone is thinking it: I already have "HardwareAcceleration" = "Emulation" set.)

---

