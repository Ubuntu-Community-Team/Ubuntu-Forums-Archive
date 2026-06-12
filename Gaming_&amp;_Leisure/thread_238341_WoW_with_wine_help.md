---
title: "WoW with wine help"
date: 2006-08-17
forum: Gaming &amp; Leisure
---

### Post by Mooie on 2006-08-17
I have been playing world of warcraft using cedega since I started playing it, but recently I decided I would like to see how cedega preformance compared to wine preformance (and if I actually need to pay $5 a month, not that its really that much).  So In a terminal i did  "wine /path/to/wow.exe -opengl" and it let me log in just fine, but when I try to enter the world it loads, then just exits the game and gives me the error
```
fixme:powrprof:DllMain (0x628b0000, 8, (nil)) not fully implemented
fixme:powrprof:DllMain (0x628b0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x628b0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wgl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e550,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  500
  Current serial number in output stream:  500
```
(I have the opengl line in my config.wtf file)  when i take out the line in the wtf file, and run the command (without the -opengl part) I can log into the game, but the buildings have these huge spikes pointed out of them, and are really distorted.  I would like to have it running in opengl...    I am using wine 9.19 on 64-bit ubuntu dapper, and I havent used any wine patches. the game works flawlessly with cedega

also, when I try to play games with wine, when i exit them it messes up my  twinview, but in cedega it just goes back to normal, any fixes for that?  or is there any way to change the metamodes line in my xorg.conf to let me have both monitors on when I am playing a game (one browsing the web, one playing WoW)?

i would really like to get this working ](*,)     thanks for your help :D

---

### Post by DJRockoBobo on 2006-08-18
[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Normal_CD_Installation](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Normal_CD_Installation)
Enter on this site and skip the mozilla and active x settings for windows - for me it worked just fine......if u can't make it without those settings install them afterwards. Then if u have any trouble with the graphics then try instead of 

wine WoW.exe -opengl - the following command

wine WoW.exe -d3d 

With d3d try to change the video settings and the see of ot works with opengl

---

### Post by Mooie on 2006-08-18
I got it fixed (kinda, more of a workaround though).  I still have the problem with d3d, but I read that the problem with opengl with wine is the way the minimap is rendered inside buildings.  I downloaded a mod that hides it when you log in or change zones.  It works pretty well now (same fps that I get in cedega, which is kinda scary, I might cancle my subscription).  There isnt a minimap problem w/ d3d though, so it would be nice to be able to use that ](*,)     oh well

---

