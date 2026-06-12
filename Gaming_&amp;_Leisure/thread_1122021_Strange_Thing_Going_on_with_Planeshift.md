---
title: "Strange Thing Going on with Planeshift"
date: 2009-04-10
forum: Gaming &amp; Leisure
---

### Post by WalmartSniperLX on 2009-04-10
When I first installed the game and ran it, everything ran smooth minus some graphic glitches in-game.

I decided to clean up my Xorg.conf file because I made it a mess when trying to configer Xinerama. Since I don't need dual-displays I did 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And returned everything to default. Then when I tried launching Planeshift, it would loud up to the first screen, then close. I edited the Xorg.conf file since then and now it looks like this: 

> Section "ServerFlags"
	Option		"GlxVisials"    "all"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option		"AccelMethod" "EXA"
	Option		"RenderAccel" "1"
	Option		"EnablePageFlip" "1"
	Option		"AccelDFS" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Launching Planeshift gives me this output:

```
Your configuration files are in... /home/patrick/.PlaneShift
DEBUG: Initializing OpenAL sound system
DEBUG: Retrieving available devices.
DEBUG: Default OpenAL device: '((sampling-rate 44100) (device '(native))
DEBUG: No device specified
DEBUG: Falling back on default device
DEBUG: Can't retrieve attributes size: OpenAL error ALC_INVALID_DEVICE
ATTENTION: default value of option force_s3tc_enable overridden by environment.

planeshift.application.client:
  PlaneShift Steel Blue (0.4.03)
  This game uses Crystal Space Engine created by Jorrit and others
  1.4.0 [Unix-x86-GCC]
Fri Apr 10 12:55:10 2009, LOG_ANY flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_WEATHER flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SPAWN flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CELPERSIST flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_PAWS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_GROUP flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CHEAT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_LINMOVE flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SPELLS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_NEWCHAR flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SUPERCLIENT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_EXCHANGES flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_ADMIN flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_STARTUP flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CHARACTER flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CONNECTIONS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CHAT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_NET flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_LOAD flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_NPC flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_TRADE flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SOUND flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_COMBAT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SKILLXP flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_QUESTS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_SCRIPT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_MARRIAGE flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_MESSAGES flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_CACHE flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_PETS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_USER flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_LOOT flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_DUELS flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, LOG_TRIBES flag deactivated with no filter.
Fri Apr 10 12:55:10 2009, All LOGS are off.
Mounting skin: /this/art/skins/elves.zip
Mounting skin: /planeshift/art/skins/base/client_base.zip
  psEngine initialized.
Using fontsize 16 for resolution 1024x768
Segmentation fault

```

Any ideas? I can't figure it out unless Im missing a section in xorg.conf that was needed before. I have not removed any dependencies from the system either (since at least).

EDIT: Here's some of my glxinfo/Mesa info:
```
$ glxinfo | grep Mesa
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.2 
```

---

### Post by WalmartSniperLX on 2009-04-10
Well I decided to mess around and change the device driver from radeon to vesa. I lose direct rendering but then planeshift launches without problem (minus the fact that the graphics are really, really slow).

---

