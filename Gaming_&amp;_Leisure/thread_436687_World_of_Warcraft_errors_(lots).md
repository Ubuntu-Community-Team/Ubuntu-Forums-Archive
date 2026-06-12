---
title: "World of Warcraft errors (lots)"
date: 2007-05-08
forum: Gaming &amp; Leisure
---

### Post by deknakker on 2007-05-08
Hi im new too to ubuntu. Trying to get world of warcraft to work in this new environment.

So far i followed all the standard procedures.

I installed wine
Installed WOW in windows and copied it (completely installed) to my desktop folder.
and then i got some more updates of wine and edited Config.wtf

but when i run the game in the terminal i get loads of errors and then i get only the first startupscreen. When i press play i get even more errors.

Terminal errors:
[COLOR="DarkRed"]
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f318,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170f20) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x16edf8) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x170f20) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
[/COLOR]
and the next error is in windows language...

[COLOR="DarkRed"]This application has encountered a critical error:

ERROR #134 (0x85100086) Fatal Condition
Program:	Z:\home\jan\Desktop\World of Warcraft\WoW.exe

Unable to associate local address with socket: The socket is already bound to an address, or the parameter is a listening socket.[/COLOR]

i would love to solve the problem, but just dont know where to start.

And i think my roommate has all the ports of our router forwarded to him. I dont think he will mind me forwarding everything to me but im not even sure if thats the problem.

If someone could help me he/she would get the thanks from a ubuntu noob

greetings 
John



btw how do i turn the smilies off, cant do it in the edit of this post... soz for that

---

### Post by Perfect Storm on 2007-05-08
Try check/search for the howto WoW here in gaming forum.

A good place to start: [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

---

