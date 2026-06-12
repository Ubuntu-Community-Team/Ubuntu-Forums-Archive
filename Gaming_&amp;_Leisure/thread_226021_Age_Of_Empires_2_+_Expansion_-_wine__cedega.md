---
title: "Age Of Empires 2 + Expansion - wine / cedega"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by drews_blunted on 2006-07-30
I have created this thread to hopefully find a way to run Age of Empires 2 on Ubuntu dapper 6.10. 

I have the latest versions of both Cedega + Wine

I installed the Age of Empires 2 AOK and The Conquerors expansion using wine.
When i first tryed to run the game i got the error for no-cd / copy protection. I used the crack below found in the WineHQ wiki.

[http://appdb.winehq.org/appview.php?iVersionId=147](http://appdb.winehq.org/appview.php?iVersionId=147) - Wine HQ App Database
[http://www.megagames.com/cracks/html/c30080_0.htm](http://www.megagames.com/cracks/html/c30080_0.htm)  - AOE2 NO-CD Crack

Now that that was out of the way when i tryed to run the game i got the error.

Could not initialize graphics system. Make sure your video card and drivers are compatable with direct draw. 

I am not sure where to go from this point. Possibly i will try installing direct draw through wine. Anyhelp with getting this game to run smooth on ubuntu would be thanked.

/me update! I reinstalled and made sure to install directdraw this time.

---

### Post by Kratos on 2006-07-30
Make sure you have the latest video drivers installed for your card.

[https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

---

### Post by drews_blunted on 2006-07-30
my nvidia drivers are the latest version and are working fine.

Ive had this game working before on an earlyer version of ubuntu with and older version of wine. anyone got this game playable in dapper?

---

### Post by berserker on 2006-07-31
I had a similar error when installing America's Army 2.6.  It said to run "wineprefixcreate", which solved the problem.

---

### Post by Qwerty_ on 2006-07-31
Yeah i tried to get AGE3 working as well and i had no success you got futher than me you managed to install it. What version of wine did you try .9.17? or .9.18

---

### Post by drews_blunted on 2006-07-31
I have wine 0.9.9-0Ubuntu2

Also i tryed "wineprefixcreate", and it didn't fix my problem. 

Im not sure what directdraw is? but is their a way to set AOE2 to use opengl?
The installer works great! i had no problems at all with the AOE2 installer in wine.

---

### Post by drews_blunted on 2006-07-31
eureka!

I have found a fix now the game is working!

Simply run **wine empires2.exe -- -opengl**

The game runs

Hope this thread will help others get this game working for themselves!

PS. I have found wine NOT cedega to run this game best! :KS

---

### Post by Qwerty_ on 2006-08-01
Awesome i am going to have another crack at getting it to run now thats a good idea adding -- -opengl i never thought of that it might help me fix some other games as well.

---

### Post by Kalinda on 2006-08-01
Okay.. I tried it.. and it ran.. well, only AoE 2, not the Expansion (which says AoE 2 wasn't detected). I ran it with OpenGL, as per instructions here.

However, I've got some problems - The game is REALLY laggy and the sound skips a lot. I didn't go beyond the menu, but still... Matt (my brother) told me that WINE needs lots of RAM to run stuff well. Anyone know how I can tell WINE to use more RAM? I looked in winecfg and didn't find anything about that.

The game works just fine Windows on my machine, though, so it's not that my computer is slow.. despite being old and sort of craptastic ^_^

Thanks for any help!

EDIT: Here is the terminal output from when I run the command.

```
kalinda@----:~/.wine[/email]/c/Age Of Empires II$ wine empires2.exe -- -opengl
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd71180)->(0x10022,00000013)
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:DIB_DirectDrawSurface_Blt Can't handle DDBLT_WAIT flag right now.
fixme:system:SystemParametersInfoW Unimplemented action: 111 (SPI_SETSHOWIMEUI)
err:dplay:DP_IF_InitializeConnection Unable to load service provider
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:dplay:DP_IF_InitializeConnection Unable to load service provider
err:dplay:DirectPlayCreate Failed to Initialize SP: DPERR_UNAVAILABLE
err:x11drv:GrabPointer Window procedure has been changed!
```

There's something about ALSA in there, which might explain why the sound is incredibly choppy. I donm't know what the rest of that stuff means, though. Anyone got any ideas?

---

### Post by drews_blunted on 2006-08-01
I have a Geforce 5900 wit 1 gb of ram and a amd64 3500+ the game even runs a little slow and lags up a bit for me when i play. overall though i can play the game and it is playable! I am still working on the AOE2 expansion. You can go ahead and use the crack available for the Conquerors expansion available at the wine HQ.

---

### Post by spiffytech on 2006-08-05
I have not yet gotten AOE2 to work properly on my laptop. I downloaded the No-CD crack, and did "wine Empires2.exe --opengl" to it, and got into the game. However, I have no sound, and there's no "exit" button in the game. Plus, the fonts are made in black, and not white like the should be. Can this be fixed?

---

### Post by drews_blunted on 2006-08-16
I ran into the same problem with the sound. You need to run winecfg and in the audio tab change it from OSS to ALSA that worked for me!

Also for sum reason without the package kdebase installed when i clicked on the audio tab it crashes.

---

