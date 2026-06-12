---
title: "Panzer General 2 (old W95 game) - video problems"
date: 2007-03-05
forum: Gaming &amp; Leisure
---

### Post by aarondesk on 2007-03-05
Hello all,
 Ubuntu newbie here. I installed Ubuntu two days ago. Also installed Wine. Wine appears somewhat ok. I installed and can run Filezilla. I also have a windows game (Steel Panthers World at War) that installed ok, and appears to play ok, though the movement is a little slow.

Anyways, I'm trying to run a W95 game, Panzer General 2. The Wine site says it works fine. [http://appdb.winehq.org/appview.php?iVersionId=1242](http://appdb.winehq.org/appview.php?iVersionId=1242)

I was able to get the game running by changing to a Virtual Desktop and it loads to the main menu screen fine. However, after I start a scenario, the game loads up with the game control menu, but the central part of the screen where the map of the scenario should be doesn't change. It just stays the same graphic as the previous main menu screen. Clicking on the button to look at the strategic map crashes the game. Basically it appears anything with some bit of graphics doesn't work. 

I've changed Emulation to W95 for the program, and also played with the Video modes, but none of this helps. Any ideas?  It looks like a video problem. From the below error message, I'm wondering if I can change to an 8-bit window for the game to work. 

Here's the output in the terminal. 

[INDENT]aarondesk@aarondesk-desktop:~/.wine/drive_c/Program Files/panzer2$ wine panzer2.exe
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16ead0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16e130)->(0x50024,00000011)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.[/INDENT]
The above part is what loads when I run the game. The below message appears when I try to access the strategic map.
[INDENT]
wine: Unhandled division by zero at address 0x44b469 (thread 002f), starting debugger...
Unhandled exception: divide by zero in 32-bit code (0x0044b469).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
etc. etc. I get 1/2 page of what look like memory registers.[/INDENT]

---

