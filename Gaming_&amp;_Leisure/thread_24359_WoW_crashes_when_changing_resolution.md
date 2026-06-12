---
title: "WoW crashes when changing resolution"
date: 2005-04-06
forum: Gaming &amp; Leisure
---

### Post by nizi on 2005-04-06
I got wow installed and running using cedega (non cvs), but when i try to change the resolution from the default 800x600 to 1280x800 (widescreen laptop), it crashes and i get this error message:

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  147 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x3200005
  Serial number of failed request:  3763
  Current serial number in output stream:  3763


I am running Hoary with ATI Mobility 9700, fglrxinfo shows:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

I also get the same error message when trying to run cs:source

---

### Post by MrParker on 2005-04-07
Does the same thing for me! 

The way I got around it was to go into the WoW directory in your transgaming c_drive and go into program files/world of warcraft/WTF directory


Open config.wtf in gedit and add the line 
SET gxResolution "1280x1024"  Or whatever resolution you want to put in there.


Worked for me, seems the crash only happens when you change a setting that causes a window refresh. Anyway thats how I got around it. Hope it works for you :)

---

### Post by Gioutsaman on 2006-10-03
hey guys i have recently installed wow under dapper kubuntu 6.06 successfully but it seems that something goes wrong with my X server. when i run the game with Wine 0.9.6 i can see the intro but when the intro finishes it crashes me out. I should clarify that my screen resolution is 1280x1024 and that when the game starts my screen resolution goes to 1024x768.....when the game "xrashes" :D i get the following message:

fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c220000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c220000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eee8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f65c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f648,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  386
  Current serial number in output stream:  387


i haven't yet opened the ports manualy from the router (i don't know if this is done automatically by the wow software) but i don't think that this is the reason the game crashes. If somebody has an answer to this i would appreciate it :D

---

