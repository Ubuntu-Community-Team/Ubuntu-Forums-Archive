---
title: "WoW/Burning Crusade on 7.04"
date: 2007-06-24
forum: Gaming &amp; Leisure
---

### Post by leupi on 2007-06-24
I have Kubuntu 7.04 and just installed Wine 0.9.39 and now I would like to install WoW for my daughter. First off, I am NOT a gamer and am not at all familiar with WoW. I have before  me 9 CDs, five WoW CDs and four WoW Burning Crusade CDs. I was looking at [this]("https://help.ubuntu.com/community/WorldofWarcraft") site and am not sure of how to proceed. I read this:
> Click on Places -> Home Folder in the top panel. Use this application to create a directory and copy all of the files from all of the CD's to this directory on your hard drive (overwrite when prompted).
Which CDs? Do I use all nine CDs or have the four TBC CDs replaced the five WoW CDs?

WoW is the last remaining reason that I still have XP in the house. I do not dare go Linux only till I get this WoW thing worked out  :)

Any advice is appreciated.

Thanks,
Todd

---

### Post by EmperorSquirrels on 2007-06-24
You'd need to install WoW (the core of the game) first, and then the Burning Crusade (the expansion) second. Does anything happen when you put the first WoW disc in?

Also, Cedega, I hear, has better compatibility for WoW. Have you considered it?

---

### Post by leupi on 2007-06-24
Thanks for the response. I have not even tried to install it yet, with all of these disks I was not even sure where to start. As far as Cedega goes, no, I never considered it, never even heard of it  lol. I did a quick Google search and see that it has a monthly fee. Not sure if I really want to pay another monthly fee just for WoW...

I'll try Wine first and see if she whines (no pun intended...) too much; if so, I might consider Cedega.

So I need to copy all of the WoW DCs, install them and then do the same with the TBC CDs? This might be a long night...

Thanks again,
Todd

---

### Post by DonPeppe on 2007-06-24
From experience, the best thing you can do is try the install from the cd's first.  if it fails it will do so at the end of the 1st cd, but if it doesn't you will save the time of copying all to your HD.  Mine installed flawless from a DVD (got the collector's edition) both Classic and Expansion.

If you have an nVidia video card, wine works very well.  Only a few minor details which I'm sure you will learn to live with (I still can't find a solution for my "alt-Click" problem, or how can I change the resolution in-game without it crashing on me).

---

### Post by Paradux on 2007-06-24
I know you can emulate WOW in Crossover if that helps. It'll probably be better in Wine if you can run it though.

---

### Post by leupi on 2007-06-24
Well, I tried to install from the CDs and got all the way to the end of the first CD and it asked me to install CD two. I could not eject CD one. When I tried I got the message that it was still mounted, I tried to umount it and got the message that it was busy and I could not umount it. I could not find a paper clip to eject it that way either...

So now I am copying all of the CDs to /wow and I will then run
```
wine Installer.exe
```
from that directory.

Wish me luck...

Thanks,
Todd

---

### Post by Gazimoff on 2007-06-24
It *should* work

Copy the Burning Crusade ones to a different folder, call it something like wowtbc, as that has a seperate installer that you need to use once the first one is done.

Once it's all done there are some final tweaks to do (there are some other threads here that'll help), then you're all set.

On a side note, I've been showing off WoW on linux with some friends. People are getting jealous, especially with multiple desktops and the Beryl cube :)

---

### Post by leupi on 2007-06-24
I copied all of the CDs to /wow and tried again. It seems that the previous failed install is causing an issue. It is telling me that WoW is already installed there and to try a different location. I have never used Wine before, is there a way that I can remove the remnants of the botched install so that I can continue with this one?

Thanks,
Todd

---

### Post by Gazimoff on 2007-06-25
Go to the Home folder and select Show Hidden Files/Folders (ctrl+h). It should be in .wine/drive_c/Program Files/World of Warcraft/

Hope this helps.

---

### Post by DJMatty on 2007-06-25
There are also some reg keys that get created although I think that's when the game gets run.

I have just this evening successfully copied my World Of Warcraft folder from my vista partition, installed wine, set the sound to alsa, edited the config.wtf and the registry as detailed in the page you linked to, and running WoW works great.

The only thing I have an issue with is occasional black flickers on the screen, annoying but I am gonna see if I can live with it and play the game for a while.

Cheers

Matt

---

### Post by hikaricore on 2007-06-25
> **DJMatty said:**
> There are also some reg keys that get created although I think that's when the game gets run.

This may or may not be correct.

While there _may_ be some registry keys created, they are of no importance to anything.

---

### Post by duncan_nz on 2007-06-25
Check out this page, it is very useful :)

[http://wowwiki.com/Linux/Wine](http://wowwiki.com/Linux/Wine)

---

### Post by leupi on 2007-06-27
Not sure what I am doing wrong. I have tried it both ways, installing it with the CDs and copying it over from Windows XP. When I install from the CDs I get an option to either create a new account or play with an existing account. As my daughter already has an account I choose to play with an existing one. I then get this five minute animated intro and after that, nothing, I just end up at my desktop with no options. If I try to run it again, I get just the intro with no option to login with an account.

With the version that I copied over from XP I just get the intro and again, no option to actually login and play the game. BTW, is there any way to skip the intro?

Thanks,
Todd

---

### Post by Ardrias on 2007-06-28
You could try adding movie = 0 to your config.wtf file. It's found in your WoW-dir under WTF. This page [http://www.wowwiki.com/Config.wtf_defaults](http://www.wowwiki.com/Config.wtf_defaults) is a great resource for troubleshooting and improving performance.

---

### Post by Sammi on 2007-06-28
@leupi
WoW is probably crashing at the login screen. Try running the game in at terminal and posting the text output it creates here.

What are you're system specs by the way? CPU, RAM, graphics card, and Wine and graphics card driver version?

---

### Post by leupi on 2007-07-03
When I tried to run the version that I brought over from Windows (with TBC) I got this:
```
tparks@dell4500:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f008,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x37402324) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7ce1b4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Error: Rage 128 timed out... exiting
tparks@dell4500:~/.wine/drive_c/Program Files/World of Warcraft$
```
I noticed that there was a notice to set hardware acceleration to emulation so I did that, no change.

I then tried to run the version that I installed off of the CDs (no TBC yet) and this time I got the 5 min animation but it never gave me a login (has sound this time though...  The output was:
```
tparks@dell4500:~/.wine/drive_c/Program Files/wow/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d570000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d570000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34eeec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x197138) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexEnvf(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_COMBINE_EXT); @ context.c / 346
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x196db0) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x197138) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=28672, mixpos=0, primary_mixpos=16384, writepos=20480, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=16384
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=12288, mixpos=0, primary_mixpos=16384, writepos=4096, playpos=18432
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=10240, mixpos=0, primary_mixpos=16384, writepos=6144, playpos=20480
fixme:ntdll:NtCreateIoCompletion (0x34fc44, 1f0003, (nil), 0)
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=8192, mixpos=0, primary_mixpos=16384, writepos=8192, playpos=22528
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=6144, mixpos=0, primary_mixpos=16384, writepos=10240, playpos=22528
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=6144, mixpos=0, primary_mixpos=16384, writepos=10240, playpos=24576
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=4096, mixpos=0, primary_mixpos=16384, writepos=12288, playpos=26624
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_psizemax WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ utils.c / 1795
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ utils.c / 1797
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ utils.c / 1799
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ utils.c / 1801
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ utils.c / 1803
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1805
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ utils.c / 1795
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ utils.c / 1797
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ utils.c / 1799
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ utils.c / 1801
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ utils.c / 1803
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1805
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1765
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, GL_PREVIOUS_EXT @ utils.c / 1767
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, GL_SRC_ALPHA @ utils.c / 1769
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1771
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ utils.c / 1795
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ utils.c / 1797
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ utils.c / 1799
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ utils.c / 1801
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ utils.c / 1803
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1805
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_REPLACE @ utils.c / 1785
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src2 @ utils.c / 1787
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr2 @ utils.c / 1789
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1791
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, comb_target, GL_MODULATE @ utils.c / 1795
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src0_target, src1 @ utils.c / 1797
fixme:d3d:settex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr0_target, opr1 @ utils.c / 1799
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, src1_target, src2 @ utils.c / 1801
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, opr1_target, opr2 @ utils.c / 1803
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, scal_target, 1 @ utils.c / 1805
fixme:d3d:set_tex_op >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, useext(GL_COMBINE) @ utils.c / 2270
Error: Rage 128 timed out... exiting
tparks@dell4500:~/.wine/drive_c/Program Files/wow/World of Warcraft$

```
My specs are:
Pentium 2 GHz
640MB RAM
ATI Rage 128 Pro Ultra TF
Wine version 0.9.40

Thanks,
Todd

---

### Post by DJMatty on 2007-07-04
> **hikaricore said:**
> This may or may not be correct.

While there _may_ be some registry keys created, they are of no importance to anything.
The registry keys include the install path etc. which I assume are made by the windows installer, rather than the game itself, as I have run the game on a different vista pc from a copy and no registry keys are created from what I can see.

So yeah, they aren't anything to worry about, sorry for the red-herring.

Matt

---

### Post by FozzyB on 2007-07-04
just for the record im running WOW and TBC through Cedega and generally have had much sucess with it, well worth the small donation to rid my life of windows (hehe well nearly i still can't run supreme commander but ill let that slide for now ;) )

examples of other games working through cegega:
BF1941 (and also desert combat)
BF2
Command and conqure generals (and zero hour)
Star wars knights of the old republic 2
UT2004
Need for speed carbon
Doom 3 (however couldn't get expansion working)

---

### Post by leupi on 2007-07-05
I added movie=0 to the file, everything else in that file was in the form of 'SET gxApi "opengl"'. I got the 5 min intro, but again, after the intro I was just taken back to my desktop with no way to login...

---

### Post by Swarms on 2007-07-05
If you are out of options, make a fresh install of Kubuntu and install wow using a guide, then you will gain success.

About Cedega, wow is very well supported by wine, no use of throwing money away for a graphical interface when it works this well!

---

### Post by btdown on 2007-07-06
Has anyone tried running WOW in a windows xp virtual session (VMware or Virtualbox)?

Is the performance acceptable? I have not had good luck with getting it to work with Wine (actually have not had luck with getting Wine to do anything), so I thought it might be easier to load a windows XP virtual server and load WOW on that. I was curious if anyone has done this and could comment on the performance/etc.

BT

---

### Post by hikaricore on 2007-07-06
> **btdown said:**
> Has anyone tried running WOW in a windows xp virtual session (VMware or Virtualbox)?

Is the performance acceptable? I have not had good luck with getting it to work with Wine (actually have not had luck with getting Wine to do anything), so I thought it might be easier to load a windows XP virtual server and load WOW on that. I was curious if anyone has done this and could comment on the performance/etc.

BT

Virtual Machines do not support gaming level direct rendering.  It will not work, end of story.

*(Minimal rendering support is starting to appear in VM clients, but it's nowhere near what is needed for gaming)*

---

### Post by DonPeppe on 2007-07-06
> **leupi said:**
> I added movie=0 to the file, everything else in that file was in the form of 'SET gxApi "opengl"'. I got the 5 min intro, but again, after the intro I was just taken back to my desktop with no way to login...

Did you try adding
```
SET movie "0"
SET expansionMovie "0"
SET gxApi "OpenGL"
``` 

to your Config.wtf file? The 1st two lines will  skip both movies and bring you directly to the login screen.  the 3rd line it seems you have it.  I dunno if it's case sensitive, but since linux is kinda anal in that sense, it's worth trying.

---

### Post by leupi on 2007-07-07
OK, just tried that and I went to a 600 x 800 resolution(or something like that) and nothing, no 5 min animation, no login. I did get this though:
```
Error: Rage 128 timed out... exiting
```
A friend is pretty sure that my ATI video card is not supported properly (he said that without seeing the above error).

I installed WoW on my Dell Lattitude (with an ATI video) and I went right to a login screen. I also find that I can run Beryl on the laptop but not on the desktop, on the desktop it crashes and resorts back to the KDE default. Seems as if the video card on the desktop is the culprit here. KDE identifies the video card as:
> Rage 128 Pro Ultra TF
Any thoughts on how to get that card working better with Kubuntu?

Thanks,
Todd

---

### Post by leupi on 2007-07-08
I am going to assume that my video card on the desktop is causing the issue as I have it running on the laptop. My only issue with the laptop is that it is not running fullscreen, it is only taking up about 75% of the screen in the upper left corner. I assume that I need to change a setting in wine to change that, can anyone direct me as to where that setting is?

Thanks,
Todd

---

### Post by Nkari on 2007-07-14
The not full screen is not something to do with you running in a different resolution to your laptop&#347; native resolution perhaps?

Wow&#347; monitor settings can be set via that WTF file it uses.

Just something else for you to look at.

Now can anyone suggest the best thread for me to discuss the crashing issues I am facing at the moment, I have it so painfully close to playable and WOW is all that has been keeping me on windows for the last 6 months.

---

### Post by leupi on 2007-07-18
Made a quick modification to the configuration file and all works great, my kid is thrilled. The only issue that I have is that I installed WoW while logged in as myself; as such, it is installed in /home/me/.wine/ so when she logs on as herself she will not be able to play as she does not have access to my home directory. How would this usually be handled? I have about four user accounts on this computer that will be wanting to play WoW, I can't imagine that I would have to install it in each of the /home/user directories...

Thanks,
Todd

---

### Post by CrownP10:8 on 2007-07-18
You might assign group ownership of your ~/.wine directory to the "users" group, then set up shortcuts for the other users to launch from that location.

---

### Post by leupi on 2007-07-18
So I can allow access to /home/me/.wine to users A, B, and C yet they will not have access to anything else in my home directory?

---

### Post by leupi on 2007-08-11
I was running Kubuntu 7.04 on my Dell D600 laptop with WoW running great. I decided to reformat the hard drive and install Ubuntu 7.04 (which I like much better). I then installed Wine and copied the WoW folder from a Windows computer  to the Ubuntu box. Now when I start up WoW, there are no characters and a lot of the icons are scrambled. I see other character's names, but not the character itself. Any thoughts about that? I had it working great in Kubuntu and now my kid is pissed  lol

Thanks,
Todd

---

### Post by Sammi on 2007-08-12
From our community WoW/Wine howto:
[https://help.ubuntu.com/community/WorldofWarcraft#head-2ac1ae13cb6a81b0519108cc62933d3cbdcdb85a](https://help.ubuntu.com/community/WorldofWarcraft#head-2ac1ae13cb6a81b0519108cc62933d3cbdcdb85a)
>  If you experience corrupt icons on your panel then you then you may need to set the SET UIFaster parameter in wtf/Config.wtf

Use it like this:   
Set UIFaster "x" 

Where x equals:  
0 – This turns off all UI acceleration
1 – For Internal Use Only - DO NOT USE!
2 – Enables partial UI acceleration only.
3 – Enables all UI acceleration.

Example:  
Set UIFaster "2" 

The value 2 usually corrects this problem. Try reading the whole troubleshooting section in that guide, if the tip above doesn't solved your problem.

---

### Post by leupi on 2007-09-17
I tried that setting but it did not work. Actually, all of the icons look good, but there is no character in the beginning screen. At the login screen there is some background movement, swirling dust, twinkling stars, all that looks good; however, the entrance doorway thing (look, I don't play this game...) is not there and once you login there is no character there. All else looks good though. I had it working fine on Kubuntu 7.04 but I am stuck here on Ubuntu.

Thanks,
Todd

---

