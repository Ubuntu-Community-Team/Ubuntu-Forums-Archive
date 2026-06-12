---
title: "Having WoW problems, looking for help"
date: 2007-08-29
forum: Gaming &amp; Leisure
---

### Post by adt41287 on 2007-08-29
I am having world of warcraft problems running with wine.  I have been playing smoothly for 4 months or so but just last night doesnt seem to work :(.  I am able to run wow through wine and everything and i get to the login screen, but when i type my password and hit enter it goes and looks for patches (im assuming thats what its doing) but it hits the "downloading" window and just freezes ive tried leaving it running for half or so at most and just crashes out.  When i open up the system monitor it shows wow.exe process as being "stopped". From here i am not sure what to do and was looking for some help or some log files that may lead me in the right direction..... 

cheers

---

### Post by adt41287 on 2007-08-29
this is what is ran in terminal when i load it up: 

```
cmd: wine /path_to_wow/wow.exe -opengl

fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7cdb0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cdb0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f008,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7c5eb4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:powrprof:DllMain (0x7d030000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d030000, 0, (nil)) not fully implemented
fixme:reg:GetNativeSystemInfo (0x33b020) using GetSystemInfo()
fixme:reg:GetNativeSystemInfo (0x33ab34) using GetSystemInfo()
err:d3d:InitAdapters Failed to initialize gl caps for default adapter
err:wine_d3d:WineDirect3DCreate Failed to initialize direct3d adapters
```

---

### Post by hikaricore on 2007-08-29
This has been happening to folks alot lately, one solution has been to launch the game in D3D mode once:

> wine WoW.exe -d3d

Login to the character selection, then logout, exit, and restart the game normally.

---

### Post by adt41287 on 2007-08-30
thanks!
before i got to try your method i got it working. it was either updating the launcher or clearing the cach folder where WoW is installed

---

### Post by downgrade on 2007-08-30
also if there is a patch just comment out the opengl line in your wtf file, that sometimes works too (only for patching issues though, as far as I know any way) but the d3d option is a bit easier i do suppose

---

### Post by ZarathustraDK on 2007-08-31
I got the same error with wine 0.9.44, I also tried the method above, but for unknown reasons it didn't work.

Then I stumbled across this solution in a subthread on winehq.org :

```
cd /path/to/wowfolder/Cache

chmod ugo-w Survey.mpq 
```

Above fixed my problem, :guitar:

---

